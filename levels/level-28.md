**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

En este nivel debemos acceder a un **repositorio Git** alojado en el servidor, pero esta vez el repositorio tiene **ramas (branches)** adicionales. Nuestro objetivo es clonar el repositorio, explorar sus ramas y encontrar la contraseña del siguiente nivel.

---
### Understanding the Challenge

El nivel nos indica que hay un repositorio Git corriendo en el puerto `2220` bajo el usuario `bandit28-git`. Necesitamos clonar este repositorio usando SSH, pero la contraseña no está en la rama principal (`master/main`), sino en alguna otra rama.

---
### Cloning the Repository

Usamos el comando `git clone` con la URL SSH proporcionada:

```bash
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
```

Ingresamos la contraseña de `bandit28` cuando se nos solicite.

Output:

```Plain text
Cloning into 'repo'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
```

---
### Exploring the Repository

Entramos al directorio clonado:

```bash
cd repo
ls -la
```

Output:

```Plain text
total 16
drwxrwxr-x 3 bandit28 bandit28 4096 Apr 23 18:17 .
drwxr-xr-x 3 bandit28 bandit28 4096 Apr 23 18:17 ..
drwxrwxr-x 8 bandit28 bandit28 4096 Apr 23 18:17 .git
-rw-rw-r-- 1 bandit28 bandit28   49 Apr 23 18:17 README.md
```

---
### Reading the README

Revisamos el archivo `README.md`:

```bash
cat README.md
```

Output:

```Plain text
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
```

La contraseña ha sido reemplazada por asteriscos. Esto sugiere que la contraseña **fue eliminada o modificada en commits posteriores**.

---
### Inspecting Git Log

Revisamos el historial de commits para encontrar la versión original:

```bash
git log
```

Output:

```Plain text
commit adc7f885a129baee883058b8a870739489f80194 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Apr 3 15:17:54 2026 +0000

    fix info leak

commit a3437bddd447f2d496731658e86b98cbea9d3c98
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Apr 3 15:17:54 2026 +0000

    add missing data

commit cb630ec182b75bc289595511f8bcf4d47cfec50d
Author: Ben Dover <noone@overthewire.org>
Date:   Fri Apr 3 15:17:54 2026 +0000

    initial commit of README.md
```

Vemos que hay **dos commits**. El más reciente "fix info leak" eliminó la contraseña. El commit anterior "add missing data" contenía la contraseña original.

---
### Inspecting the Previous Commit

Examinamos el commit anterior (el que contiene la contraseña):

```bash
git show a3437bddd447f2d496731658e86b98cbea9d3c98
```

Output:

```bash
commit a3437bddd447f2d496731658e86b98cbea9d3c98
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Apr 3 15:17:54 2026 +0000

    add missing data

diff --git a/README.md b/README.md
index 7ba2d2f..d4e3b74 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: <TBD>
+- password: [REDACTED]
```

Ahí está la contraseña original.

---
### Retrieving the Password

```Plain text
+- password: [REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 29.**

---
### Skills Practiced

- Uso de **Git** para clonar repositorios remotos
- Navegación por el **historial de commits** con `git log`
- Inspección de **commits antiguos** con `git show`
- Identificación de **información sensible expuesta** en el historial de Git
- Comprensión de que **eliminar un archivo no lo borra del historial**

---
### Screenshots
