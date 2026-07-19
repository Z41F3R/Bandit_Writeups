**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

La contraseña para el siguiente nivel se almacena en el archivo:

```Plain text
readme
```

Sin embargo, cuando se inicia sesión normalmente como `bandit18`, el servidor **cierra la conexión inmediatamente,** impidiendo ejecutar comando de forma interactiva.

---
### Understanding the Challenge

Este nivel introduce un comportamiento especial:
el sistema está configurado para **cerrar la sesión inmediatamente después del login.**

Esto ocurre por que en el entorno del usuario existe un **script de logout** que finaliza la sesión automáticamente.

Para evitar este problema debemos **ejecutar un comando directamente al momento de conectarnos por SSH,** sin abrir una sesión interactiva.

SSH permite hacer esto colocando **al final de la conexión.**

---
### Connecting and Executing the Command

En lugar de conectarnos normalmente, ejecutamos el comando `cat readme` directamente durante la conexión: 

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```

Explicación:

- `ssh` → cliente SSH
- `bandit18@bandit.labs.overthewire.org` → usuario y host
- `-p 2220` → puerto SSH usado por Bandit
- `"cat readme"` → comando que se ejecutará inmediatamente al conectarse

Esto evita que el sistema cierre la sesión antes de poder ejecutar comandos.

---
### Retrieving the Password

El comando ejecutado durante la conexión mostrará el contenido del archivo `readme`.

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 19.**

---
### Skills Practiced

- Uso de **SSH para ejecutar comandos remotos**
- Comprensión de **sesiones no interactivas**
- Bypass de scripts de logout automáticos
- Lectura directa de archivos remotos

---
### Screenshots

