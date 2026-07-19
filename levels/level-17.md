**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

Hay **dos archivos** en el directorio home:

```Plain text
passwords.old
passwords.new
```

La contraseña para el siguiente nivel se encuentra en `passwords.new`, pero es **la única linea que es diferente comparada con** `passwords.old`.

---
### Understanding the Challenge

En el nivel anterior obtuvimos **una clave privada SSH** desde un servicio TLS.

Esa clave se utiliza para **autenticarnos como** `bandit17` en el servidor.

Una vez dentro, el objetivo es **comparar dos archivos** para encontrar la línea que cambió.

Para esto se utiliza el comando:

```Plain text
diff
```

Este comando muestra **las diferencias entre dos archivos.**

---
### Connecting to the Level

Primero guardamos la clave privada obtenida en el nivel anterior en un archivo, por ejemplo:

```Plain text
sshkey.private
```

Ajustamos los permisos de la clave:

```bash
chmod 600 sshkey.private
```

Luego iniciamos sesión usando esa clave:

```bash
ssh -i sshkey.private bandit17@bandit.labs.overthewire.org -p 2220
```

---
### Enumeration 

Una vez dentro del sistema listamos los archivos disponibles:

```bash
ls
```

Output:

```Plain text
passwords.new
passwords.old
```

---
### Comparing the Files

Para encontrar la diferencia entre ambos archivos usamos:

```bash
diff passwords.new passwords.old
```

Output:

```Plain text
42c42
< XXXXXXXXXXXXXXXXXX
---
> BMIOFKM7CRSLI97voLp3TD80NAq5exxk
```

---
### Retrieving the Password

El símbolo `<`  indica **la linea que pertenece a** `passwords.new`.

Por lo tanto, la contraseña para el siguiente nivel es:

```Plain text
x2glXXXXXXXXXXXXXX
```

---
### Skills Practiced

- Comparación de archivos en Linux
- Uso del comando `diff`
- Autenticación SSH mediante clave privada
- Identificación de cambios entre archivos

---
### Screenshots
