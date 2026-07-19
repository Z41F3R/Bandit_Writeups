**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

En este nivel, al conectarnos como `bandit32`, entramos en un **shell restringido (Uppercase Shell)** que convierte todos los comandos a mayúsculas. Nuestro objetivo es **escapar de esta restricción** para poder ejecutar comandos y leer la contraseña del siguiente nivel (`bandit33`).

---
### Understanding the Challenge

Cuando iniciamos sesión como `bandit32` con la contraseña obtenida en el nivel anterior:

```bash
ssh bandit32@bandit.labs.overthewire.org -p 2220
```

Después de ingresar la contraseña, vemos:

```Plain text
WELCOME TO THE UPPERCASE SHELL
```

Todo lo que escribimos se convierte automáticamente a **MAYÚSCULAS**. Si intentamos `ls`, el shell recibe `LS` y no funciona.

---
### Escaping the Uppercase Shell

Probamos ejecutar la variable `$0`, que en muchos shells representa el nombre del script o shell actual:

```bash
>> $0
```

Output:

```Plain text
$
```

¡Ya tenemos una shell normal sin restricción de mayúsculas!

---
### Retrieving the Password

Ahora simplemente leemos la contraseña de `bandit33`:

```bash
cat /etc/bandit_pass/bandit33
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 33.**

---
### Bandit Level 33 → Level 34

No hay un siguiente nivel. Bandit termina aquí. Revisamos si hay algún archivo de despedida:

```bash
ls -la
```

Output:

```bash
total 20
drwxr-xr-x  2 root     root     4096 Apr 23 18:17 .
drwxr-xr-x 70 root     root     4096 Apr 23 18:18 ..
-rw-r--r--  1 root     root      220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root     3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root     root      807 Jan  6  2022 .profile
-rw-r--r--  1 root     root      200 Apr 23 18:17 README.txt
```

```bash
cat README.txt
```

Output:

```Plain text
Congratulations on solving the last level of this game!

At this moment, there are no more levels to play in this game. However, we are constantly working
on new levels and will most likely expand this game with more levels soon.
Keep an eye out for an announcement on our usual communication channels!
In the meantime, you could play some of our other wargames.

If you have an idea for an awesome new level, please let us know!
```

---
### ¡Bandit Completado!

```Plain text
             _                     _ _ _   
            | |__   __ _ _ __   __| (_) |_ 
            | '_ \ / _` | '_ \ / _` | | __|
            | |_) | (_| | | | | (_| | | |_ 
            |_.__/ \__,_|_| |_|\__,_|_|\__|

Congratulations! You've completed the Bandit wargame.
```

