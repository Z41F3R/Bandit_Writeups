**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

Una vez que tenemos acceso a una shell como `bandit26` (después de escapar del programa restringido), nuestro objetivo es **obtener la contraseña del siguiente nivel,** `bandit27`.

---
### Understanding the Challenge

En el directorio home de `bandit26`, encontramos un archivo especial que nos permitirá ejecutar comandos con los privilegios de `bandit27`.

---
### Enumerating the Home Directory

Una vez dentro de la shell como bandit26, listamos el contenido del directorio:

```bash
ls -la
```

Output:

```Plain text
total 36
drwxr-xr-x  2 root     root      4096 Apr 23 18:17 .
drwxr-xr-x 70 root     root      4096 Apr 23 18:18 ..
-rw-r--r--  1 root     root       220 Jan  6  2022 .bash_logout
-rw-r--r--  1 root     root      3771 Jan  6  2022 .bashrc
-rw-r--r--  1 root     root       807 Jan  6  2022 .profile
-rwsr-x---  1 bandit27 bandit27  14876 Apr 23 18:17 bandit27-do
-rw-r-----  1 bandit26 bandit26    215 Apr 23 18:17 text.txt
```

---
### Retrieving the Password

Ahora usamos `bandit27-do` para leer la contraseña de `bandit27`:

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

Output:

```Plain text
[REDACTED]
```

---
### Skills Practiced

- Uso de **setuid binaries** para escalar privilegios
- Ejecución de comandos con privilegios de otro usuario
- Exploración de permisos de archivos con `ls -l`
- Identificación del bit **setuid** (`rws`)
- Lectura de archivos protegidos mediante binarios con privilegios elevados

---
### Screenshots

