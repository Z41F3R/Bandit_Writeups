**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se puede obtener **conectándose al puerto correcto entre** `31000` **y** `32000` **en** `localhost` **utilizando SSL/TLS.**

Uno de estos puertos ejecutan un servicio que **devuelve una clave privada SSH** cuando se le envía la contraseña correcta del nivel actual.

---
### Understanding the Challenge

En este nivel no sabemos **qué puerto exacto está ejecutando el servicio correcto**.

Por lo tanto, primero debemos realizar **enumeración de puertos** para identificar:

- qué puertos están abiertos
- qué servicio está corriendo en cada uno

Una vez encontrado el puerto correcto, debemos **enviar la contraseña actual mediante una conexión TLS.**

El servicio responderá con **una clave privada SSH,** la cual será utilizada **en el siguiente nivel**.

---
### Enumeration

Primero obtenemos la contraseña del nivel actual (`bandit16`):

```bash
cat /etc/bandit_pass/bandit16
```

Output:

```Plain text
[REDACTED]
```

---
### Scanning for the Correct Port

Para encontrar el puerto correcto realizamos un escaneo en el rango **31000-32000** usando `nmap`:

```bash
nmap localhost -sV -n -T5 --open -p31000-32000
```

Explicación del comando:

- `localhost` → escanea el host local 
- `-sV` → detecta versión del servicio
- `-n` → evita resolución DNS
- `-T5` → escaneo rápido
- `--open` → muestra solo puertos abiertos
- `-vvv` → salida muy detallada
- `-p31000-32000` → rango de puertos a escanear

Output de ejemplo:

```Plain text
PORT      STATE SERVICE
31790/tcp open  ssl/unknown
```

El puerto **31790** es el que ejecuta el servicio TLS que necesitamos.

---
### Sending the Password

Ahora enviamos la contraseña al servicio usando `ncat` con SSL:

```bash
echo "<password_de_bandit16>" | ncat --ssl localhost 31790
```

Explicación:

- `echo` → envía la contraseña
- `|` → pipe que pasa la salida al siguiente comando
- `ncat --ssl` → conexión TCP usando TLS
- `localhost 31790` → servicio identificado con `nmap`

---
### Retrieving the SSH Key

Si la contraseña es correcta, el servidor responderá con algo similar a:

```Plain text
Correct!
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

Esta salida contiene **una clave privada SSH,** la cual será utilizada **en el siguente nivel para autenticarse como** `bandit17`.

---
### Skills Practiced

- Enumeración de puertos con `nmap`
- Identificación de servicios TLS
- Uso de `ncat` para conexiones SSL
- Uso de **pipes (`|`)** para enviar datos a servicios

---
### Screenshots
