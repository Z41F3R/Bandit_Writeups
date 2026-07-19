**Wargame:** Bandit
**Plataform:** OverTheWire

---
### Objective

El objetivo de este nivel es **conectarse al servidor del laboratorio usando SSH** 

Datos de conexión:

- Host: `bandit.labs.overthewire.org`
- Puerto: `2220
- Usuario: `bandit0`
- Contraseña inicial: `bandit0`

Una vez dentro del servidor, se debe encontrar la **contraseña para el siguiente nivel ,** almacenada en un archivo dentro del directorio home.

---
### SSH Connection

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

**Explicación del comando**

- `ssh` → cliente de conexión remota segura
- `bandit0` → usuario del nivel inicial
- `bandit.labs.overthewire.org` → servidor del laboratorio
- `-p 2220` → puerto SSH utilizado por el entorno de Bandit

En la primara coEn la **primara conexión,** el cliente SSH preguntara si se confía en el host:

```Plain Text
Are you sure you want to continue connecting (yes/no)?
```

Se debe responder:

```bash
yes
```

Luego el sistema solicitara la contraseña:

```Plain Text
bandit0
```

---
### Verifying Access

Si la conexión fue exitosa, el prompt cambiará a:

```Plain Text
bandit0@bandit:~$
```

Esto indica que se ha iniciado sesión correctamente en el servidor.

---
### Enumeration

El siguiente paso es listar los archivos del directorio actual:

```bash
ls
```

Output:

```Plain text
readme
```

---
### Retrieving the Password

El archivo `readme` contiene la contraseña del siguiente nivel.

Para leer su contenido:

```bash
cat readme
```

Output:

```
[REDACTED]
```

Este valor corresponde a la contraseña para **Bandit Level 1.**

---
### Closing the Session

Para salir del servidor SSH:

```bash
exit
```

---
### Skills Practiced

- Conexión remota mediante **SSH**
- Uso básico de comandos Linux (`ls`, `cat`)
- Navegación en sistemas Linux remotos

---
### Screenshots
