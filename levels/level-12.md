**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en el archivo:

```Plain text
data.txt
```

Este archivo contiene un **volcado hexadecimal (hexdump)** de un archivo que ha sido **comprimido múltiples veces utilizando diferentes formatos.** 

El objetivo del reto es:

1. Convertir el **hexdump a su formato binario original**.
2. Identificar cada capa de compresión.
3. Descomprimir sucesivamente hasta obtener el archivo final que contiene la contraseña.

---
### Understanding the Challenge

El archivo **data.txt** no es texto plano.

Es un **hexdump,** es decir, una representación hexadecimal de un archivo binario.

Para resolver este reto se deben usar varias herramientas de Linux:

- `xxd` → convertir el hexdump a binario    
- `file` → identificar el tipo de archivo
- `gzip`, `bzip2`, `tar` → descomprimir archivos

El proceso consiste en **repetir los siguientes pasos:**

1. Identificar el tipo de archivo.
2. Descomprimir según el formato.
3. Volver a identificar el archivo resultante.

---
### Enumeration

Primero verificamos el contenido del directorio:

```bash
ls
```

Output:

```Plain text
data.txt
```

Para trabajar de forma segura se recomienda usar un **directorio temporal**

---
### Preparing a Working Directory

Creamos un directorio en `/tmp`:

```bash
mkdir /tmp/bandit12
cd /tmp/bandit12
```

Luego copiamos el archivo original:

```bash
cp ~/data.txt .
```

---
### Converting the Hexdump

El archivo es un **hexdump,** por lo que debemos convertirlo nuevamente a binario:

```bash
xxd -r data.txt data.bin
```

Explicación:

- `xxd` → herramienta para visualizar o revertir hexdumps
- `-r` → reverse (hexadecimal → binario)
- `data.txt` → archivo de entrada
- `data.bin` → archivo binario resultante

---
### Identifying the File Type

Para saber qué tipo de archivo es utilizamos:

```bash
file data.bin
```

Output de ejemplo:

```Plain text
data.bin: gzip compressed data
```

---
### Extracting the Layers

A partir de este punto el proceso se repite varias veces.

Cada vez se debe:

1. Identificar el tipo de archivo
2. Renombrarlo correctamente
3. Descomprimirlo

Ejemplo de flujo típico:

**gzip**

```bash
mv data.bin data.gz
gunzip data.gz
```

**bzip2**

```bash
mv data data.bz2
bzip2 -d data.bz2
```

**tar**

```bash
tar -xf data.tar
```

Este proceso se repite varias veces hasta llegar al archivo final.

El orden exacto depende de lo que indique el comando `file`.

---
### Retrieving the Password

Después de eliminar todas las capas de compresión obtendremos un archivo de texto.  

Para ver su contenido:

```bash
cat data
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 13.**

---
### Skills Practiced

- Análisis de archivos binarios en Linux
- Uso de `xxd` para revertir hexdumps
- Identificación de formatos de archivo con `file`
- Extracción de múltiples capas de compresión
- Uso de herramientas como `gzip`, `bzip2` y `tar` 

---
### Screenshots







