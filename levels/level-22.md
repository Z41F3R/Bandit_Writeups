**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

Un **cronjob** está ejecutándose automáticamente para el usuario `bandit23`.

Nuestro objetivo es **encontrar qué script está ejecutando ese cron job** y descubrir **dónde guarda la contraseña del siguiente nivel.**

---
### Understanding the Challenge

Los **cron jobs** son tareas programadas en sistemas Linux que se ejecutan automáticamente en intervalos definidos.

Estas tareas suelen configurarse dentro del directorio: 

```Plain text
/etc/cron.d/
```

Cada archivo dentro de este directorio define **qué script se ejecuta, con qué usuario y con qué frecuencia.**

En este nivel debemos analizar esos archivos para descubrir **qué script se está ejecutando y qué hace.**

---
### Enumerating Cron Jobs

Primero listamos los archivos dentro del directorio de cron jobs:

```bash
ls /etc/cron.d/
```

Output:

```Plain text
cronjob_bandit22  cronjob_bandit23
```

---
### Inspecting the Cron Job

Ahora revisamos el contenido del archivo correspondiente a `bandit23`:

```bash
cat /etc/cron.d/cronjob_bandit23
```

Output:

```Plain text
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh
```

Ahora sabemos **qué script se ejecuta automáticamente.**

---
### Inspecting the Script

Revisamos el contenido del script:

```bash
cat /usr/bin/cronjob_bandit23.sh
```

Output:

```bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

---
### Understanding the Script Logic

El script realiza las siguientes operaciones: 

| Codigo                                                                               | Operación que realiza                                                                                                     |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| `myname=$(whoami)` - Determina el usuario actual                                     | - Cuando el cron job se ejecuta: `myname = bandit23`                                                                      |
| `mytarget=$(echo I am user $myname \| md5sum \| cut -d ' ' -f 1)` - Crea un hash MD5 | - Toma la cadena `"I am user bandit23"`<br>    <br>- Calcula su hash MD5<br>    <br>- Extrae únicamente el valor del hash |
| `cat /etc/bandit_pass/$myname > /tmp/$mytarget` - Copia la contraseña                | - La contraseña de `bandit23` se escribe en `/tmp/[hash_MD5]`                                                             |

Necesitamos calcular el hash que el script genera **cuando se ejecuta como usuario** `bandit23`.

---
### Calculating the Correct Filename

Calculamos manualmente el hash simulando la ejecución como `bandit23`:

```bash
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
```

Output:

```Plain text
8ca319486bfbbc3663c0e5f62879c7c7
```

Este es el nombre del archivo donde el cron job guarda la contraseña.

---
### Retrieving the Password

Ahora leemos el archivo donde el cron job guarda la contraseña:

```bash
cat /tmp/8ca319486bfbbc3663c0e5f62879c7c7
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 23.**

---
### Skills Practiced

- Análisis de **cron jobs**
- Exploración de **scripts automáticos del sistema**
- Lectura de scripts Bash con variables y sustitución de comandos
- Cálculo de **hashes MD5** desde la línea de comandos
- Simulación de contexto de ejecución para predecir comportamiento

---
### Screenshots

