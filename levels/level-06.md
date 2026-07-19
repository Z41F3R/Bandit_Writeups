**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se encuentra **en algún lugar del servidor.**

El archivo que contiene la contraseña tiene las siguientes propiedades:

- Pertenece al **usuario `bandit7`**
- Pertenece al **grupo `bandit6`**
- Tiene un tamaño exacto de **33 bytes**

El objetivo del reto es **localizar ese archivo especifico en el sistema** y leer su contenido.

---
### Understanding the Challenge

En este nivel la contraseña **no se encuentra en el directorio personal del usuario.**

Por lo tanto, sera necesario **buscar en todo el sistema de archivos.**

Para resolver este reto se utiliza el comando `find`, que permite buscar archivos aplicando filtros como:

- usuario propietario
- grupo
- tamaño del archivo

Usando estos criterios podemos localizar **exactamente el archivo que contiene la contraseña.**

---
### Enumeration

Primero confirmando que no hay archivos relevantes en el directorio actual:

```bash
ls
```

Output:

```Plain text
(no relevant files)
```

Esto indica que debemos **realizar una búsqueda en todo el sistema**

---
### Searching the Correct File

Para localizar el archivo correcto utilizamos el siguiente comando:

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

Explicación del comando: 

- **/**  
    Realiza la búsqueda desde la raíz del sistema.
- **-user bandit7**  
    Busca archivos cuyo propietario sea el usuario `bandit7`.
- **-group bandit6**  
    Filtra archivos cuyo grupo sea `bandit6`.
- **-size 33c**  
    Busca archivos de **33 bytes exactos**.
- **2>/dev/null**  
    Descarta los errores de permisos para mantener la salida limpia.

Output de ejemplo:

```Plain text
/var/lib/dpkg/info/bandit7.password
```

---
### Retrieving the Password

Una vez localizado el archivo correcto, se procede a leer su contenido:

```bash
cat /var/lib/dpkg/info/bandit7.password
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a la contraseña para **Bandit Level 7.**

---
### Skills Practiced

- Búsqueda de archivos en todo el sistema Linux
- Uso avanzado del comando `find`
- Filtrado de archivos por usuario, grupo y tamaño
- Gestión de errores con redirección (`2>/dev/null`)
- Lectura de archivos con `cat`

---
### Screenshots





