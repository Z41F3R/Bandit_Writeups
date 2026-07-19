**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective 

La contraseña para el siguiente nivel se encuentra almacenada en el archivo:

```Plain text
data.txt
```

La contraseña es **la única línea de texto que aparece solo una vez** dentro del archivo.

El objetivo del reto es **identificar esa línea única** entre muchas líneas duplicadas.

---
### Understanding the Challenge

El archivo **data.txt** contiene **muchas líneas repetidas.**
Solo **una línea aparece una sola vez,** y esa corresponde a la contraseña del siguiente nivel.

Para resolver este reto se utilizan los comando `sort` y `uniq`.

- `sort` ordena las líneas del archivo.
- `uniq` filtra líneas duplicadas.

Esto es necesario porque `uniq` **solo detecta duplicados cuando están uno junto al otro,** por lo que primero debemos ordenar el archivo.

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

Podemos observar el contenido del archivo:

```bash
cat data.txt
```

Veremos **muchas líneas aparentemente similares,** lo que indica que existen múltiples duplicados.

---
### Searching the Unique Line

Para encontrar la línea que aparece solo una vez ejecutamos:

```bash
sort data.txt | uniq -u
```

Explicación del comando:

- **sort data.txt**  
    Ordena todas las líneas del archivo.
- **| (pipe)**  
    Envía la salida del primer comando al siguiente.
- **uniq -u**  
    Muestra únicamente las líneas que aparecen **una sola vez**.

---
### Retrieving the Password

La salida del comando mostrará  **directamente la línea única,** por ejemplo:

```bash
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

Esa línea corresponde a **la contraseña para Bandit Level 9.**

---
### Skills Practiced

- Procesamiento de texto en Linux
- Uso de `sort` para ordenar datos
- Uso de `uniq` para identificar duplicados
- Uso de **pipes (`|`)** para combinar comandos
- Análisis de archivos con muchas líneas

---
### Screenshots

