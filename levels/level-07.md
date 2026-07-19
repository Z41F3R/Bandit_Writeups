**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en el archivo:

```bash
data.txt
```

La contraseña está **en la misma línea que contiene la palabra:**

```Plain text
millionth
```

El objetivo del reto es **localizar esa línea dentro del archivo** y obtener la contraseña.

---
### Understanding the Challenge

El archivo **data.txt** contiene muchas lineas de texto.
Buscar manualmente la palabra `millionth` seria poco eficiente.

Para resolver este reto se utiliza el comando `grep`, que permite **buscar texto dentro de archivos.**

`grep` mostrará únicamente las líneas que contienen el patrón especificado.

---
### Enumeration

Primero verificamos que el archivo existe en el directorio actual:

```bash
ls
```

Output:

```Plain text
data.txt
```

Luego podemos inspeccionar el archivo con herramientas de búsqueda.

---
### Searching the Correct Line

Para encontrar la línea que contiene la palabra **millionth** utilizamos:

```bash
grep millionth data.txt
```

Explicación del comando:

- **grep**  
    Herramienta de búsqueda de texto.
- **millionth**  
    Patrón que queremos encontrar.
- **data.txt**  
    Archivo donde se realizará la búsqueda.

Una alternativa equivalente sería:

```bash
cat data.txt | grep "millionth"
```

---
### Retrieving the Password

La salida del comando será similar a:

```bash
millionth   cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

la **segunda columna corresponde a la contraseña** para el siguiente nivel.

---
### Skills Practiced

- Búsqueda de texto dentro de archivos en Linux
- Uso del comando `grep`
- Filtrado de información dentro de archivos grandes
- Procesamiento básico de texto en terminal

---
### Screenshots


