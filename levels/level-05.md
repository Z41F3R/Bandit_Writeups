**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en **un archivo dentro del directorio**

```Plain text
inhere
```

Este archivo tiene **todas las siguientes características:**

- Es **legible por humanos**
- Tiene un tamaño exacto de **1033 bytes**
- **No es ejecutable**

El objetivo del reto es **localizar ese archivo específico** y leer su contenido para obtener la contraseña del siguiente nivel.

---
### Understanding the Challenge

Dentro del directorio **inhere** existen múltiples subdirectorios y archivos.
Buscar manualmente seria muy ineficiente.

Para resolver este reto se utiliza el comando `find`, que permite buscar archivos dentro de un sistema de archivos aplicando diferentes filtros como:

- tamaño
- permisos
- tipo de archivo
- nombre
- entre otros

En este caso utilizaremos filtros que coincidan exactamente con las propiedades del archivo que buscamos.

---
### Enumeration

Primero se listan los archivos del directorio principal del nivel:

```bash
ls
```

Output:

```Plain text
inhere
```

Luego accedemos al directorio:

```bash
cd inhere
```

Dentro existen múltiples subdirectorios con nombres similares:

```Plain text
maybehere00
maybehere01
maybehere02
...
```

Cada uno contiene varios archivos.

---
### Searching the Correct File

Para encontrar el archivo correcto utilizamos el siguiente comando:

```bash
find . -size 1033c ! -executable -readable 2>/dev/null
```

Explicación del comando:

- **`.`**  
    Directorio donde se realizará la búsqueda.
- **-size 1033c**  
    Busca archivos con tamaño exacto de **1033 bytes**.
- **! -executable**  
    Selecciona archivos que **no son ejecutables**.
- **-readable**  
    Archivos que el usuario puede leer.
- **2>/dev/null**  
    Descarta mensajes de error (stder) para mantener limpia la salida.

Output de ejemplo:

```Plain text
inhere/maybehere07/.file2
```

---
### Retrieving the Password

Una vez identificado el archivo correcto, se procede a leer su contenido:

```bash
cat inhere/maybehere07/.file2
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a la contraseña para **Bandit Level 6** 

---
### Skills Practiced

- Búsqueda avanzada de archivos en Linux
- Uso del comando `find`
- Filtrado de archivos por tamaño y permisos
- Enumeración eficiente en sistemas Linux
- Lectura de archivos con `cat`

---
### Screenshots


















```bash
find inhere -size 1033c ! -executable -readable 2>/dev/null
```

Explicación del comando:

- **inhere**  
    Directorio donde se realizará la búsqueda.
- **-size 1033c**  
    Busca archivos con tamaño exacto de **1033 bytes**.
- **! -executable**  
    Selecciona archivos que **no son ejecutables**.
- **-readable**  
    Archivos que el usuario puede leer.
- **2>/dev/null**  
    Descarta mensajes de error (stder) para mantener limpia la salida.

Output de ejemplo:

```Plain text
inhere/maybehere07/.file2
```

---
### Retrieving the Password

Una vez identificado el archivo correcto, se procede a leer su contenido:

```bash
cat inhere/maybehere07/.file2
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a la contraseña para **Bandit Level 6.** 

---
### Skills Practiced

- Búsqueda avanzada de archivos en Linux
- Uso del comando `find`
- Filtrado de archivos por tamaño y permisos
- Enumeración eficiente en sistemas Linux
- Lectura de archivos con `cat`

---
### Screenshots


















