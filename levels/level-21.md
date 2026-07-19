**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

Un **cron job** está ejecutándose automáticamente para el usuario `bandit22`.

Nuestro objetivo es **encontrar qué script está ejecutando ese cron job** y descubrir **dónde guarda la contraseña del siguiente nivel.**

---
### Understanding the Challenge

Los **cron job** son tareas programadas en sistemas Linux que se ejecutan automáticamente en intervalos definidos.

Estas tareas suelen configurarse dentro del directorio:

```Plain text
/etc/cron.d/
```

Cada archivo dentro de este directorio define **qué script se ejecuta, con qué usuario y con qué frecuencia.**

En este nivel debemos analizar esos archivos para descubrir **qué script está ejecutándose y qué hace.**

---
### Enumerating Cron Jobs

Primero listamos los archivos dentro del directorio de cron jobs:

```bash
ls /etc/cron.d/
```

Output:

```Plain text
cronjob_bandit22
```

---
### Inspecting the Cron Job

Ahora revisamos el contenido del archivo:

```bash
cat /etc/cron.d/cronjob_bandit22
```

Output de ejemplo:

```Plain text
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh
```

Explicación:

```Plain text
* * * * *   → se ejecuta cada minuto
bandit22    → se ejecuta como usuario bandit22
script      → /usr/bin/cronjob_bandit22.sh
```

Ahora sabemos **qué script se ejecuta automáticamente.**

---
### Inspecting the Script

Revisamos el contenido del script:

```bash
cat /usr/bin/cronjob_bandit22.sh
```

Output de ejemplo:

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit22 > /tmp/t0f6kR1m...
```

El script está copiando la contraseña del nivel `bandit22` a un archivo temporal dentro de `/tmp`.

---
### Retrieving the Password

Ahora simplemente leemos el archivo donde el cron job guarda la contraseña:

```bash
cat /tmp/t0f6kR1m...
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 22.**

---
### Skills Practiced

- Análisis de **cron jobs**
- Exploración de **scripts automáticos del sistema**
- Lectura de scripts Bash
- Identificación de **tareas programadas en Linux**

---
### Screenshots

