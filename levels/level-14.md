**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel puede obtenerse **enviando la contraseña del nivel actual al puerto** `30000` **en** `localhost`.

El servicio que escucha en ese puerto **verificará la contraseña y devolverá la del siguiente nivel.**

---
### Understanding the Challenge

En este nivel debemos **interactuar con un servicio de red local.**

El servicio escucha en:

```Plain text
localhost:30000
```

Si enviamos la **contraseña correcta del usuario** `bandit14`, el servicio responderá con la **contraseña de** `bandit15`.

Para interactuar con este tipo de servicios se puede utilizar `nc` **(netcat)**, una herramienta que permite **establecer conexiones TCP manuales.**

---
### Enumeration

Primero obtenemos la contraseña del nivel actual (`bandit14`):

```bash
cat /etc/bandit_pass/bandit14
```

Output:

```Plain text
[REDACTED]
```

Guardamos o copiamos esta contraseña, ya que será necesaria para comunicarnos con el servicio.

---
### Connecting to the Service

Ahora nos conectamos al servicio que está escuchando en el puerto **30000** usando nc:

```bash
nc localhost 30000
```

Esto abrirá una conexión TCP con el servicio.

Una vez conectado, **pegamos la contraseña obtenida anteriormente.**

Ejemplo:

```Plain text
<password_de_bandit14>
```

---
### Alternative Method (Using Pipes)

También podemos enviar la contraseña directamente al servicio **sin abrir una sesión interactiva,** utilizando un **pipe (`|`)**.

```bash
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```

Explicación:

- `cat /etc/bandit_pass/bandit14` → muestra la contraseña del usuario `bandit14`
- `|` → redirige la salida al siguiente comando
- `nc localhost 30000` → envía la contraseña al servicio que escucha en el puerto **30000**

---
### Retrieving the Password

Si la contraseña enviada es correcta, el servidor responderá con algo similar a: 

```Plain text
Retrieving the Password
```

La segunda linea corresponde a **la contraseña para Bandit Level 15.**

---
### Skills Practiced

- Comunicación con servicios TCP
- Uso de **netcat (`nc`)**
- Comprensión de **localhost y puertos**
- Uso de **pipes (`|`)** para automatizar comandos

---
### Screenshots
