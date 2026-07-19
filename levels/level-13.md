**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra almacenada en:

```Plain text
/etc/bandit_pass/bandit14
```

Sin embargo, este archivo **solo puede ser leído por el usuario** `bandit14`.

En este nivel no se proporciona directamente la contraseña, sino **una clave privada SSH** que permite autenticarse como `bandit14`.

El objetivo es **usar esta clave para iniciar sesión como** `bandit14` **y obtener la contraseña del siguiente nivel.**

---
### Understanding the Challenge

A diferencia de niveles anteriores, **no se utiliza autenticación por contraseña.**

En su lugar, se utiliza **autenticación mediante clave privada SSH.**

Las claves SSH permiten autenticarse de forma segura sin necesidad de escribir una contraseña, siempre que se posea la **clave privada correspondiente.**

En el directorio home de `bandit13` existe un archivo que contiene esta clave.

---
### Enumeration

Primero verificamos el contenido del directorio actual:

```bash
ls
```

Output:

```Plain text
sshkey.private
```

Este archivo corresponde a una **clave privada SSH válida para el usuario** `bandit14`.

---
### Copying the Key to Local Machine

Ahora debemos copiar la clave a nuestra **maquina local.**

Desde la terminal local ejecutamos:

```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```

Explicación:

- `scp` → copia archivos mediante SSH
- `-P 2220` → puerto utilizado por el servidor Bandit
- `bandit13@bandit.labs.overthewire.org` → servidor remoto
- `.` → directorio actual en la máquina local

---
### Fixing Key Permissions

Una vez que la clave está en nuestra **máquina local**, debemos ajustar sus permisos.

SSH **rechaza claves privadas que tengan permisos demasiado abiertos** por motivos de seguridad.

Ajustamos los permisos:

```bash
chmod 600 sshkey.private
```

Verificamos los permisos:

```bash
ls -l sshkey.private
```

Output esperado:

```Plain text
-rw------- 1 user user ... sshkey.private
```

Esto significa:

- **solo el propietario puede leer y escribir**
    
- ningún otro usuario puede acceder a la clave

---
### SSH Authentication Using the Private Key

Una vez descargada la clave. nos conectamos como `bandit14`:

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

Si la autenticación es correcta, veremos el siguiente prompt:

```Plain text
bandit14@bandit:~$
```

Esto confirma que hemos iniciado sesión como `bandit14`.

---
### Retrieving the Password

Finalmente obtenemos la contraseña del siguiente nivel:

```bash
cat /etc/bandit_pass/bandit14
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 14.**

---
### Skills Practiced

- Autenticación SSH mediante clave privada
- Gestión de permisos de archivos con `chmod`
- Transferencia segura de archivos con `scp`
- Uso de SSH con claves (`ssh -i`)
- Comprensión del sistema de autenticación de SSH

---
### Screenshots


