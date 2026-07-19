**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en el archivo: 

```bash
data.txt
```

El contenido del archivo está **ofuscado utilizando ROT13**, lo que significa que **todas las letras minúsculas (`a-z`) y mayúsculas (`A-Z`) han sido rotadas 13 posiciones en el alfabeto**.

El objetivo del reto es **decodificar el texto utilizando ROT13** para obtener la contraseña del siguiente nivel.

---
### Understanding the Challenge

**ROT13** es un cifrado de sustitución simple donde cada letra del alfabeto se desplaza **13 posiciones.**

Ejemplo:

```Plain text
A → N
B → O
C → P
...
M → Z
N → A
O → B
...
Z → M
```

El mismo principio se aplica a las letras minúsculas:

```Plain text
a → n
b → o
c → p
...
m → z
n → a
...
z → m
```

Los **números y símbolos no se modifican.**

Para decodificar este tipo de cifrado en Linux se utiliza el comando `tr`, que permite **remplazar caracteres por otros.**

---
### Enumeration

Primero verificamos que el archivo existe:

```bash
ls
```

Output:

```Plain text
data.txt
```

Si visualizamos el contenido:

```bash
cat data.txt
```

Veremos una cadena de texto que **no parece una contraseña legible,** ya que esta cifrada con ROT13.

---
### Decoding ROT13

Para decodificar el texto utilizamos el siguiente comando:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Explicación del comando:

- **cat data.txt**  
    Muestra el contenido del archivo.
- **| (pipe)**  
    Envía la salida al siguiente comando.
- **tr 'A-Za-z' 'N-ZA-Mn-za-m'**  
    Reemplaza cada letra del alfabeto con su equivalente ROT13.

---
### Retrieving the Password

Al ejecutar el comando anterior se mostrará directamente la contraseña:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 12.**

---
### Skills Practiced

- Comprensión del cifrado ROT13
- Uso del comando `tr` para sustitución de caracteres
- Manipulación de texto en Linux
- Uso de **pipes (`|`)** para combinar comandos

---
### Screenshots




