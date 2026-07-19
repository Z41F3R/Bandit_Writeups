**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective 

Para obtener la contraseña del siguiente nivel debemos usar un **programa especial llamado:**

```Plain text
bandit20-do
```

Este programa permite **ejecutar comandos como el usuario** `bandit20`.

La contraseña del siguiente nivel se encuentra almacenada en:

```Plain text
/etc/bandit_pass/bandit20 
```

---
### Understanding the Challenge

En este nivel encontramos un **archivo ejecutable especial** dentro del directorio home del usuario.

Listando los archivos:

```bash
ls -l
```

Output:

```Plain text
-rwsr-x--- 1 bandit20 bandit19 ... bandit20-do
```

Aquí aparece algo importante en los permisos:

```Plain text
rws
```

La `s` **en lugar de** `x` indica que el archivo tiene activado el **bit SUID.**

---
### What is SUID?

**SUID (Set User ID)** es un permiso especial en Linux que permite que **un programa se ejecute con los privilegios del propietario del archivo,** en lugar de ejecutarse con los privilegios del usuario que lo ejecuta.

Normalmente en Linux ocurre lo siguiente: 

- Un usuario ejecuta un programa 
- El programa se ejecuta **con los permisos de ese usuario**

Pero cuando un archivo tiene activado **SUID,** ocurre algo diferente:

- El programa se ejecuta **con los permisos del propietario del archivo**

En este caso:

- El propietario del programa es **bandit20**
- Nosotros estamos conectados como **bandit19**

Por lo tanto, al ejecutar:

```Plain text
./bandit20-do
```

el programa **se ejecuta con privilegios de** `bandit20`, permitiendo acceder a recursos que normalmente `bandit19` no podría leer.

Los permisos del archivo se ven así:

```Plain text
-rwsr-x---
```

Desglose:

| Permiso | Significado                                                     |
| ------- | --------------------------------------------------------------- |
| `rws`   | propietario puede leer, escribir y ejecutar con **SUID activo** |
| `r-x`   | el grupo puede leer y ejecutar                                  |
| `---`   | otros usuarios no tienen permisos                               |

Cuando aparece **`s` en lugar de `x`**, significa que el **SUID está activo**.

---
### Enumeration

Primero verificamos con qué usuario se ejecuta el programa:

```bash
./bandit20-do whoami
```

Output:

```Plain text
bandit20
```

Esto confirma que el programa **se esta ejecutando con privilegios de** `bandit20`.

---
### Retrieving the Password

Ahora utilizamos el programa para leer el archivo protegido que contiene la contraseña del siguiente nivel:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 20.**

---
### Skills Practiced

- Permisos especiales en Linux

- Comprensión del bit SUID

- Ejecución de programas con privilegios de otro usuario

- Acceso a archivos protegidos mediante programas privilegiados

---
### Security Insight

Los **SUID binaries mal configurados** son una de las formas más comunes de **escalación de privilegios en sistemas Linux**.

Cuando un programa con SUID permite ejecutar comandos arbitrarios o interactuar con archivos sensibles, puede convertirse en una vulnerabilidad.

Durante auditorios de seguridad o CTFs es común enumerar estos binarios con el comando: 

```bash
find / -perm -4000 2>/dev/null
```

Este comando lista **todos los archivos que tienen el bit SUID activado,** permitiendo identificar posibles vectores de escalación de privilegios.

---
### Screenshots

