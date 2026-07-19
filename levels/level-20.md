**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective 

Existe un programa en el directorio home llamado:

```PLain text
suconnect
```

Este programa **se conecta a un puerto especifico en el localhost** y espera recibir la contraseña del nivel actual.

Si la contraseña enviada es correcta, el programa responderá con **la contraseña del siguiente nivel.** 

---
### Understanding the Challenge

El programa `suconnect` funciona como **cliente de red.**

Esto significa que:

- el programa **intentará conectarse a un puerto**
- espera que **otro proceso esté escuchando en ese puerto**

En otras palabras, necesitamos crear **un servidor temporal** que recibe la conexión de `suconnect`.

Para hacer esto utilizamos `ncat` o `nc` en **modo listener.**

---
### How Network Communication Works Here

En este nivel ocurren dos roles de red:

| Rol      | Programa    | Función                |
| -------- | ----------- | ---------------------- |
| Servidor | `ncat -l`   | Escucha conexiones     |
| Cliente  | `suconnect` | Se conecta al servidor |

El flujo es el siguiente:

```Plain text
suconnect → conecta → puerto local
ncat → escucha → puerto local
```

Cuando la conexión se establece:

1. suconnect se conecta al puerto
2. ncat acepta la conexión
3. enviamos la contraseña del nivel actual
4. suconnect verifica la contraseña
5. si es correcta, devuelve la contraseña del siguiente nivel

---
### Starting a Listener

Primero abrimos un **listener** usando `ncat`:

```bash
ncat -l localhost 8080
```

Explicación:

- -l → modo escucha (listener)
- localhost → solo conexiones locales
- 8080 → puerto donde esperamos la conexión

Ahora el sistema está esperando que alguien se conecte a ese puerto.

---
### Connecting with the Program

En otra terminal ejecutamos el programa:

```bash
./suconnect 8080
```

Este programa ahora **se conecta al puerto 8080 en localhost.**

En ese momento la conexión queda establecida entre:

```Plain text
suconnect <-> ncat
```

---
### Sending the Password

Desde la terminal donde está ejecutándose `ncat`,  enviamos la contraseña del nivel actual:

```Plain text
[REDACTED]
```

El programa `suconnect` recibirá esa contraseña y verificara si es correcta.

---
### Retrieving the Password

Si la contraseña enviada es válida, el programa responderá con algo similar a:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 21.**

---
### Why This Works

Aunque `ncat` está en modo escucha, **también permite enviar datos manualmente a la conexión.**

Cuando `suconnect` se conecta al puerto:

- la conexión TCP queda abierta    
- cualquier texto que escribamos en `ncat` se envía al cliente (`suconnect`)
- `suconnect` procesa esa información y devuelve una respuesta

Esto crea un canal de comunicación bidireccional:

```Plain text
ncat <-> suconnect
```

---
### Skills Practiced

- Comunicación entre procesos mediante sockets
- Uso de netcat / ncat como servidor temporal
- Comprensión del modelo cliente-servidor
- Interacción manual con servicios de red

---
### Screenshots
