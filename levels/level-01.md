**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra en un archivo llamado: 

```Plain text
-
```

Este archivo esta ubicado en el **directorio home del usuario** `bandit1`.

El reto consiste en leer el contenido de este archivo para obtener la contraseña del **Level 2.**

---
### Understanding the Challenge

El nombre del archivo es especial porque el carácter `-`  en Linux suele representar **la entrada estandar (stdin - standard input )**.

Por esta razón, ejecutar directamente:

```bash
cat -
```

no funciona como se espera, ya que `cat` interpreta `-` como **entrada estandar** y no como un archivo.

Para resolver el problema es necesario **especificar la ruta del archivo explícitamente.**

---
### Enumeration 

Primero se listan los archivos del directorio actual:

```bash
ls
```

Output:

```Plain text
-
```

---
### Retrieving the Password

Existen varias formas validas de leer el archivo.

**Option 1 - Using the current directory path**

```bash
cat $(pwd)/-
```

**Option 2 — Using the home directory shortcut**

```bash
cat ~/-
```

**Option 3 — Using a relative path**

```bash
cat ./-
```

Cualquiera de estos comandos mostrará el contenido del archivo.

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a la contraseña para **Bandit Level 2.**

---
### Skills Practiced

- Manejo de **nombres de archivos especiales en Linux**
- Uso de **rutas absolutas y relativas**
- Comprensión del concepto de **stdin**

---
### Screenshots

