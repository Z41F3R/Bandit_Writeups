**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en el archivo:

```bash
data.txt
```

El contenido de este archivo está **codificado utilizando Base64.**

El objetivo del reto es **decodificar el contenido del archivo** para obtener la contraseña del siguiente nivel.

---
### Understanding the Challenge

**Base64** es un esquema de codificación que convierte datos binarios en texto ASCII utilizando un conjunto de 64 caracteres.

Este tipo de codificación se utiliza comúnmente para **transmitir datos binarios a través de sistemas que manejan texto.**

Para resolver esto reto se utiliza el comando `base64` con la opción de **decodificación.**

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

Si observamos el contenido del archivo:

```bash
cat data.txt
```

Veremos una cadena de caracteres similares a:

```bash
VGhpcyBpcyBhbiBleGFtcGxlIG9mIGJhc2U2NCBlbmNvZGluZw==
```

Este formato es característico de **datos codificados en Base64**

---
### Decoding the File

Para decodificar el archivo utilizamos:

```bash
base64 -d data.txt
```

En algunos sistemas también se puede usar:

```bash
base64 --decode data.txt
```

Explicación del comando:

- **base64**  
    Herramienta para codificar o decodificar datos en Base64.
- **-d / --decode**  
    Indica que queremos **decodificar** el contenido.

---
### Retrieving the Password

Al ejecutar el comando anterior, la salida mostrará directamente la contraseña:

```bash
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 11.**

---
### Skills Practiced

- Identificación de datos codificados
- Decodificación de Base64 en Linux
- Uso del comando `base64`
- Análisis de formatos de codificación comunes en CTF

---
### Screenshots




