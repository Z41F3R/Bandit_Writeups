**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en el archivo:

```bash
data.txt
```

El archivo contiene **datos binarios,** pero la contraseña esta dentro de **una de las pocas cadenas legibles por humanos,** precedida por varios caracteres:

```bash
====
```

El objetivo es **extraer las cadenas legibles del archivo** y encontrar la que contiene la contraseña.

---
### Understanding the Challenge

El archivo **data.txt** contiene principalmente **datos binarios,** por lo que usar `cat` directamente no mostrará información útil.

Para resolver este reto se utiliza el comando `strings`, que permite **extraer cadenas de texto legibles (ASCII) desde archivos binarios.**

Posteriormente se utiliza `grep` para filtrar únicamente las lineas que contienen varios caracteres `=`.

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

Intentar visualizar el archivo con `cat` mostrará **muchos caracteres ilegibles,** lo que confirma que contiene datos binarios.

---
### Extracting Human-Readable Strings

Para extraer únicamente las cadenas legibles ejecutamos:

```bash
strings data.txt
```

Esto mostrará múltiples cadenas de texto dentro del archivo.

Para filtrar únicamente las lineas relevantes utilizamos:

```bash
strings data.txt | grep "===="
```

Explicación del comando:

- **strings data.txt**  
    Extrae texto legible del archivo binario.
- **| (pipe)**  
    Envía la salida al siguiente comando.
- **grep " ==== "**  
    Filtra las líneas que contienen varios caracteres `=`.

---
### Retrieving the Password

La salida del comando será similar a:

```bash
========== the password is XXXXXXXXXXXXXXXXXX
```

La cadena la final corresponde a **la contraseña para Bandit Level 10.**

---
### Skills Practiced

- Extracción de texto desde archivos binarios
- Uso del comando `strings`
- Filtrado de texto con `grep`
- Uso de **pipes (`|`)** para combinar comandos
- Análisis de archivos binarios en Linux

---
### Screenshots

