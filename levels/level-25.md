**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

Al conectarnos como `bandit25`, tenemos acceso a una **clave SSH privada** para el usuario `bandit26`. Nuestro objetivo es usar esta clave para autenticarnos como `bandit26` y luego **escapar del programa restringido** que se ejecuta al iniciar sesión para obtener una shell y leer la contraseña del siguiente nivel.

---
### Understanding the Challenge

Cuando iniciamos sesión como `bandit25`, encontramos una clave SSH en su directorio home:

```bash
ls -l
```

Output:

```Plain text
total 20
drwxr-xr-x  2 root     root     4096 Apr 23 18:17 .
drwxr-xr-x 70 root     root     4096 Apr 23 18:18 ..
-rw-r-----  1 bandit25 bandit25   33 Apr 23 18:17 text.txt
-rw-r-----  1 bandit25 bandit25 1679 Apr 23 18:17 bandit26.sshkey
```

La clave `bandit26.sshkey` nos permite conectarnos directamente como `bandit26` sin necesidad de contraseña.

---
### Connecting with the SSH Key

Usamos la clave para autenticarnos:

```bash
ssh -i bandit26.sshkey bandit26@localhost -p 2220
```

Al conectarnos, en lugar de obtener una shell, vemos un banner ASCII y la conexión se cierra inmediatamente.

---
### The Exploit Strategy

La clave está en el comportamiento del programa que se ejecuta al iniciar sesión, que utiliza `more` para mostrar el banner. `more` tiene una característica: si el contenido **no cabe en la pantalla**, se queda en pausa esperando input del usuario, mostrando el prompt `--More--`.

Podemos aprovechar esto para obtener una shell.

---
### Step 1: Reducing Terminal Size

Antes de conectarnos, reducimos el tamaño de la ventana del terminal hasta que tenga solo **1 o 2 líneas de altura**. Esto hará que el banner ASCII no quepa en la pantalla y `more` entre en pausa.

---
### Step 2: Connecting with the SSH Key

Con la ventana pequeña, ejecutamos:

```bash
ssh -i bandit26.sshkey bandit26@localhost -p 2220
```

Ahora vemos el prompt de `more`:

```Plain text
--More--(0%)
```

---
### Step 3: Entering Vim from More

Presionamos la tecla **`v`**. Esto abre el editor `vim` con el contenido del banner.

---
### Step 4: Setting the Shell in Vim

Dentro de `vim`, necesitamos obtener una shell. Ejecutamos:

```vim
:set shell=/bin/bash
```

Luego, abrimos una shell:

```vim
:shell
```

---
### Step 5: We Have a Shell

¡Ya tenemos una shell interactiva con los permisos de `bandit26`!

Verificamos quiénes somos:

```bash
whoami
```

Output:

```Plain text
bandit26
```

---
### Retrieving the Password

Ahora leemos la contraseña:

```bash
cat /etc/bandit_pass/bandit26
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 26.**

---
### Skills Practiced

- Uso de **claves SSH** para autenticación    
- **Escapando de programas restringidos** con `more`
- Manipulación del **tamaño de terminal** para forzar comportamiento
- Uso de **`v` en more** para acceder a vim
- Ejecución de comandos desde **vim** con `:shell`
- Cambio de shell en vim (`:set shell=/bin/bash`)
- Obtención de **shell interactiva** desde un entorno limitado

---
### Screenshots

