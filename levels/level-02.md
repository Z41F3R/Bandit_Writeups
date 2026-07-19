**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en un archivo llamado:

```Plain text
--spaces in this filename--
```

Este archivo se encuentra en el **directorio home del usuario `bandit2`**.

El reto consiste en leer el contenido de este archivo para obtener la contraseña del **Level 3**.

---
### Understanding the Challenge

El nombre del archivo contiene **espacios**, lo que puede causar problemas al utilizar comandos en la terminal.

En Linux, Los espacios separan argumentos dentro de un comando, por que al intentar ejecutar:

```bash
cat --spaces in this filename--
```

el sistema interpreta cada palabra como un argumento diferente.

Para solucionar esto se pueden usar varias técnicas, como **escapar los espacios** o **encerrar el nombre del archivo en comillas.**

---
### Enumeration

Primero se listan los archivos del directorio actual:

```bash
ls
```

Output:

```Plain text
--spaces in this filename--
```

---
### Retrieving the Password

**Escaping spaces**

Se pueden escapar los espacios utilizando el carácter `\`:

```bash
cat ~/--spaces\ in\ this\ filename--
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a la contraseña para **Bandit Level 3.**

---
### Skills Practiced

- Manejo de **nombres de archivos con espacios**
- Uso del carácter **escape `\` en Bash**
- Lectura de archivos en Linux con `cat`

---
### Screenshots

















