**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

En este nivel debemos acceder a un **repositorio Git** alojado en el servidor. Nuestro objetivo es **clonar el repositorio** utilizando SSH y encontrar la contraseña del siguiente nivel dentro de los archivos del repositorio.

---
### Understanding the Challenge

El nivel nos indica que hay un repositorio Git corriendo en el puerto `2220`
bajo el usuario `bandit27-git`. Necesitamos clonar este repositorio usando SSH para obtener los archivos que contiene.

---
### Cloning the Repository

Usamos el comando `git clone` con la URL SSH proporcionada. La contraseña que usaremos es la de `bandit27`:

```bash
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
```

Al ejecutar el comando, se nos pedirá la contraseña. Ingresamos:

```Text plain
[REDACTED]
```

Output:

```Plaiin text
Cloning into 'repo'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```

---
### Exploring the Repository

Ahora tenemos un directorio llamado `repo`. Entramos y listamos su contenido:

```bash
cd repo
ls -la
```

Output:

```Plain text
total 12
drwxrwxr-x 3 bandit27 bandit27 4096 Apr 23 18:17 .
drwxr-xr-x 3 bandit27 bandit27 4096 Apr 23 18:17 ..
drwxrwxr-x 8 bandit27 bandit27 4096 Apr 23 18:17 .git
-rw-rw-r-- 1 bandit27 bandit27   68 Apr 23 18:17 README
```

---
### Reading the README File

Revisamos el contenido del archivo `README`:

```bash
cat README
```

Output:

```Plain text
The password to the next level is: [REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 28.**

---
### Skills Practiced

- Uso de **Git** para clonar repositorios remotos
- Autenticación SSH en **repositorios Git**    
- Navegación por **directorios clonados**
- Lectura de archivos dentro de un repositorio

---
### Screenshots