**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en **el único archivo legible por humanos** dentro del directorio:

```Plain text
inhere
```

En este directorio existen varios archivos con nombres similares como:

```
-file00
-file01
-file02
...
```

La mayoría contienen **datos binarios,**  pero uno de ellos contiene **texto legible,** que corresponde a la contraseña del siguiente nivel.

---
### Understanding the Challenge

El reto consiste en **identificar qué archivo contiene texto legible.**

Para ello se utiliza el comando `file`, que permite determinar **el tipo de contenido de un archivo,** indicando si es texto, binario, imagen, ejecutable, etc.

---
### Enumeration

Primero se accede al directorio correspondiente: 

```bash
cd inhere
```

Luego se listan los archivos:

```bash
ls
```

Output:

```
-file00
-file01
-file02
...
```

---
### Identifying the Human-Readable File

Para identificar qué archivo contiene texto, se utiliza el comando:

```bash
file ./*
```

Este comando analizará todos los archivos del directorio. 

Output de ejemplo: 

```
./-file00: data
./-file01: data
./-file02: data
./-file07: ASCII text
```

El archivo que contiene `ASCII text` es el que posee la contraseña.

---
### Retrieving the Password

Una vez identificado el archivo correcto, se lee su contenido: 

```bash
cat ./-file07
```

Output:

```
[REDACTED]
```

---
#### Skills Practiced

- Identificación del **tipo de archivo en Linux**
- Uso del comando `file`
- Análisis de múltiples archivos en un directorio
- Lectura de archivos con `cat`

---
### Screenshots
