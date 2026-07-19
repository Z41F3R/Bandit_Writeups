**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

En este nivel debemos acceder a un **repositorio Git** alojado en el servidor. Esta vez, la contraseña no está en la rama principal ni en el historial de commits, sino en una **rama (branch) diferente** que no es `master`.

---
### Understanding the Challenge

El nivel nos indica que hay un repositorio Git corriendo en el puerto `2220` bajo el usuario `bandit29-git`. Necesitamos clonar el repositorio y explorar **todas las ramas** para encontrar la contraseña.

---
### Cloning the Repository

Usamos el comando `git clone` con la URL SSH proporcionada:

```bash
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
```

Ingresamos la contraseña de `bandit29` cuando se nos solicite.

Output:

```Plain text
Cloning into 'repo'...
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Total 16 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (16/16), done.
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
drwxrwxr-x 3 bandit29 bandit29 4096 Apr 23 18:17 .
drwxr-xr-x 3 bandit29 bandit29 4096 Apr 23 18:17 ..
drwxrwxr-x 8 bandit29 bandit29 4096 Apr 23 18:17 .git
-rw-rw-r-- 1 bandit29 bandit29  131 Apr 23 18:17 README.md
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
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```

La contraseña está marcada como `<no passwords in production!>` No está aquí.

---
### Listing All Branches

Revisamos todas las ramas disponibles en el repositorio:

```bash
git branch -a
```

Output:

```Plain text
  dev
* master
  sploits-dev
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
```

¡Hay muchas ramas! Especialmente notamos una rama llamada `dev`.

---
### Switching to a Different Branch

Probamos a cambiar a la rama `dev`:

```bash
git checkout dev
```

Output:

```Plain text
Cambiado a rama 'dev'
Tu rama está actualizada con 'origin/dev'.
```

---
### Inspecting the Dev Branch

Listamos el contenido en la rama `dev`:

```bash
ls -la
```

Output:

```Plain text
total 24
drwxrwxr-x   4 r4nc0x r4nc0x 4096 abr  4 11:38 .
drwx--x---+ 33 r4nc0x r4nc0x 4096 abr  4 11:04 ..
drwxrwxr-x   2 r4nc0x r4nc0x 4096 abr  4 11:38 code
drwxrwxr-x   7 r4nc0x r4nc0x 4096 abr  4 11:38 .git
-rw-rw-r--   1 r4nc0x r4nc0x  134 abr  4 11:38 README.md
```

---
### Reading the README File

```bash
cat README.md
```

Output:

```Plain text
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: [REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 30.**

---
### Alternative Approach: Inspecting Each Branch

Podríamos haber explorado todas las ramas con:

```bash
git branch -a | grep remotes | cut -d '/' -f3- | while read branch; do
    echo "=== Branch: $branch ==="
    
    git checkout "$branch" 2>/dev/null
    
    echo "--- Buscando en README.md ---"
    grep -i "password" README.md 2>/dev/null
    
    echo "--- Buscando en password.txt ---"
    grep -i "password" password.txt 2>/dev/null
    
    echo
done
```

---
### Skills Practiced

- Uso de **Git** para clonar repositorios remotos
- Listado de **ramas** con `git branch -a`
- Cambio entre **ramas** con `git checkout`
- Exploración de archivos en **diferentes ramas**
- Comprensión de que la información puede estar **fuera de la rama principal**

---
### Screenshots
