**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel puede obtenerse  **enviando la contraseña actual al puerto** `30001` **en** `localhost` **utilizando una conexión SSL/TLS.**

Si la contraseña es correcta, el servicio devolverá **la contraseña del siguiente nivel.**

---
### Understanding the Challenge

En este nivel anterior interactuamos con un servicio TCP simple usando `nc`.

En este nivel el servicio funciona de forma similar, pero la conexión  está **protegida con SSL/TLS.**

Esto significa que no podemos conectarnos usando `nc` normal, ya que la comunicación está cifrada.

Para resolverlo necesitamos una herramienta que soporte **conexiones SSL,** como:

- `openssl s_client`
- `ncat --ssl`

En este caso utilizaremos `ncat`, que permite establecer conexiones TCP con soporte TLS de forma sencilla.

---
### Enumeration 

Primero obtenemos la contraseña del nivel actual (`bandit15`):

```bash
cat /etc/bandit_pass/bandit15
```

Output:

```Plain text
[REDACTED]
```

Guardaremos esta contraseña, ya que será enviada al servicio.

---
### Connecting to the SSL Service

Ahora nos conectamos al servicio TLS que escucha en el puerto **30001:** 

```bash
ncat --ssl localhost 30001
```

Explicación del comando:

- `ncat` → versión avanzada de netcat incluida en **Nmap**
- `--ssl` → establece la conexión usando **TLS**
- `localhost` → servicio local
- `30001` → puerto donde escucha el servicio

Una vez conectados, pegamos la contraseña obtenida anteriormente.

Ejemplo:

```Plain text
<password_de_bandit15>
```

---
### Retrieving the Password

Si la contraseña es correcta, el servidor responderá con algo similar a:

```Plain text
Correct!
XXXXXXXXXXXXXXXXXX
```

La segunda línea corresponde a **la contraseña para Bandit Level 16**.

---
### Skills Practiced

- Comunicación con servicios **SSL/TLS**
- Uso de **ncat con soporte SSL**
- Interacción manual con servicios de red
- Comprensión de la diferencia entre **TCP y TLS**

---
### Screenshots