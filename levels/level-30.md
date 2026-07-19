**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

En este nivel debemos acceder a un **repositorio Git** alojado en el servidor. La particularidad de este nivel es que la contraseña no está en ninguna rama visible, sino en una **etiqueta (tag)** específica del repositorio.

---
### Understanding the Challenge

El nivel nos indica que hay un repositorio Git corriendo en el puerto `2220` bajo el usuario `bandit30-git`. Necesitamos clonar el repositorio y explorar **todas las referencias** (ramas, tags, etc.) para encontrar la contraseña.

---
### Exploring the Repository

Entramos al directorio clonado:

```bash
cd repo
ls -la
```

Output:

```Plain text
total 12
drwxrwxr-x 3 bandit30 bandit30 4096 Apr 23 18:17 .
drwxr-xr-x 3 bandit30 bandit30 4096 Apr 23 18:17 ..
drwxrwxr-x 8 bandit30 bandit30 4096 Apr 23 18:17 .git
-rw-rw-r-- 1 bandit30 bandit30   31 Apr 23 18:17 README.md
```

---
### Reading the README

Revisamos el archivo `README.md`:

```bash
cat README.md
```

Output:

```Plain text
just an epmty file... muahaha
```

No hay nada útil aquí.

---
### Listing All Tags

Revisamos las etiquetas (tags) del repositorio:

```bash
git tag
```

Output:

```Plain text
secret
```

¡Hay un tag llamado `secret`!

---
### Inspecting the Tag

Necesitamos ver qué contiene ese tag. Podemos mostrar el contenido del tag:

```bash
git show secret
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 31.**

---
### Skills Practiced

- Uso de **Git** para clonar repositorios remotos
- Listado de **etiquetas (tags)** con `git tag`
- Inspección de **tags** con `git show`
- Comprensión de que Git tiene múltiples tipos de **referencias** (commits, branches, tags)
- Búsqueda de información en **objetos ocultos** del repositorio

---
### Screenshots
