<div align="center">

![bandit](image.png)

# OverTheWire — Bandit

**Wargame de Linux y fundamentos de seguridad**

![OverTheWire](https://img.shields.io/badge/OverTheWire-Bandit-2ea44f?style=for-the-badge\&logo=linux\&logoColor=white)
![Niveles](https://img.shields.io/badge/Niveles-33_completados-2ea44f?style=for-the-badge)
![Estado](https://img.shields.io/badge/Estado-Finalizado-gold?style=for-the-badge)

*33 niveles. Una progresión práctica a través de Linux, networking, shell y seguridad.*

</div>

---

## Sobre el proyecto

[OverTheWire Bandit](https://overthewire.org/wargames/bandit/) es un wargame diseñado para desarrollar fundamentos prácticos de Linux y seguridad mediante una serie de desafíos progresivos.

Este repositorio documenta la resolución completa de los **33 niveles**, registrando los comandos utilizados, el proceso de análisis y las técnicas aplicadas para llegar a cada solución.

El objetivo no es únicamente obtener la contraseña del siguiente nivel, sino entender **qué está ocurriendo, cómo identificar el problema y qué herramienta permite resolverlo**.

---

## Progreso

```text
NIVELES       33 / 33
ESTADO        FINALIZADO
PLATAFORMA    OVER THE WIRE
ENTORNO       LINUX
WRITEUPS      33
```

```text
[████████████████████████████████████████] 100%
```

---

## Áreas trabajadas

| Área           | Técnicas                                        |
| -------------- | ----------------------------------------------- |
| Linux          | Sistema de archivos, permisos, procesos y shell |
| Networking     | SSH, Netcat, Nmap y SSL/TLS                     |
| Enumeración    | Búsqueda de archivos, puertos y servicios       |
| Análisis       | `grep`, `strings`, `file`, `diff`, `xxd`        |
| Encoding       | Base64, ROT13 y transformaciones de texto       |
| Automatización | Scripts y fuerza bruta controlada               |
| Privilegios    | SUID y entornos restringidos                    |
| Git            | Commits, historial, tags y repositorios         |

---

## Niveles

Cada nivel cuenta con un writeup independiente.

|  Nivel  | Tema                        | Herramienta / Técnica |          Writeup          |
| :-----: | --------------------------- | --------------------- | :-----------------------: |
| 00 → 01 | Conexión inicial            | `ssh`                 | [Ver](levels/level-00.md) |
| 01 → 02 | Archivo especial            | `cat`                 | [Ver](levels/level-01.md) |
| 02 → 03 | Nombres con espacios        | `cat`                 | [Ver](levels/level-02.md) |
| 03 → 04 | Archivos ocultos            | `ls`                  | [Ver](levels/level-03.md) |
| 04 → 05 | Identificación de archivos  | `file`                | [Ver](levels/level-04.md) |
| 05 → 06 | Enumeración                 | `find`                | [Ver](levels/level-05.md) |
| 06 → 07 | Búsqueda avanzada           | `find`                | [Ver](levels/level-06.md) |
| 07 → 08 | Filtrado de texto           | `grep`                | [Ver](levels/level-07.md) |
| 08 → 09 | Líneas únicas               | `sort`, `uniq`        | [Ver](levels/level-08.md) |
| 09 → 10 | Análisis de binarios        | `strings`             | [Ver](levels/level-09.md) |
| 10 → 11 | Codificación                | Base64                | [Ver](levels/level-10.md) |
| 11 → 12 | Transformación de texto     | `tr` / ROT13          | [Ver](levels/level-11.md) |
| 12 → 13 | Compresión y archivos       | `xxd`, `gzip`, `tar`  | [Ver](levels/level-12.md) |
| 13 → 14 | Autenticación               | SSH Private Key       | [Ver](levels/level-13.md) |
| 14 → 15 | Networking                  | `nc`                  | [Ver](levels/level-14.md) |
| 15 → 16 | SSL/TLS                     | `openssl`             | [Ver](levels/level-15.md) |
| 16 → 17 | Enumeración de puertos      | `nmap`                | [Ver](levels/level-16.md) |
| 17 → 18 | Comparación de archivos     | `diff`                | [Ver](levels/level-17.md) |
| 18 → 19 | Entorno restringido         | Shell                 | [Ver](levels/level-18.md) |
| 19 → 20 | Privilegios                 | SUID                  | [Ver](levels/level-19.md) |
| 20 → 21 | Comunicación entre procesos | `nc`                  | [Ver](levels/level-20.md) |
| 21 → 22 | Tareas programadas          | `cron`                | [Ver](levels/level-21.md) |
| 22 → 23 | Scripts automatizados       | `cron`                | [Ver](levels/level-22.md) |
| 23 → 24 | Manipulación de scripts     | `cron`                | [Ver](levels/level-23.md) |
| 24 → 25 | Fuerza bruta                | Automatización        | [Ver](levels/level-24.md) |
| 25 → 26 | Shell restringida           | Shell                 | [Ver](levels/level-25.md) |
| 26 → 27 | Evasión de restricciones    | Shell                 | [Ver](levels/level-26.md) |
| 27 → 28 | Repositorios                | Git                   | [Ver](levels/level-27.md) |
| 28 → 29 | Historial                   | Git                   | [Ver](levels/level-28.md) |
| 29 → 30 | Recuperación de información | Git                   | [Ver](levels/level-29.md) |
| 30 → 31 | Tags y referencias          | Git                   | [Ver](levels/level-30.md) |
| 31 → 32 | Repositorio remoto          | Git                   | [Ver](levels/level-31.md) |
| 32 → 33 | Shell restringida           | Shell                 | [Ver](levels/level-32.md) |

---

## Técnicas

### Linux

```text
Sistema de archivos
├── Navegación
├── Archivos ocultos
├── Nombres especiales
├── Permisos
└── Procesos

Shell
├── Bash
├── Variables
├── Redirecciones
├── Entornos restringidos
└── Evasión de restricciones

Automatización
└── Cron
```

### Networking

```text
SSH
└── Autenticación

Netcat
└── Comunicación con servicios

Nmap
└── Enumeración de puertos y servicios

OpenSSL
└── Comunicación SSL/TLS
```

### Análisis

```text
grep
sort
uniq
strings
file
diff
xxd
gzip
tar
```

### Git

```text
Repositorios
├── Commits
├── Historial
├── Tags
├── Referencias
└── Repositorios remotos
```

---

## Metodología

Los writeups buscan conservar el proceso seguido para resolver cada desafío.

```text
┌─────────────────────┐
│      OBJETIVO       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│    ENUMERACIÓN      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│       ANÁLISIS      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│      TÉCNICA        │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│      SOLUCIÓN       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│    CONCLUSIONES     │
└─────────────────────┘
```

La intención es documentar el **razonamiento detrás de la solución**, no únicamente mostrar el comando final.

---

## Herramientas utilizadas

```text
Linux
Bash
SSH
Netcat
Nmap
OpenSSL
Git
grep
find
strings
file
diff
xxd
gzip
tar
cron
```

---

## Estructura del repositorio

```text
Bandit/
│
├── levels/
│   ├── level-00.md
│   ├── level-01.md
│   ├── level-02.md
│   ├── ...
│   └── level-32.md
│
├── image.png
└── README.md
```

---

## Ruta de aprendizaje

Bandit representa una de las bases prácticas dentro de una ruta de aprendizaje orientada a seguridad ofensiva.

```text
                    BANDIT
                       │
          ┌────────────┼────────────┐
          │            │            │
        Linux      Networking      Shell
          │            │            │
          └────────────┼────────────┘
                       │
                       ▼
                     Python
                       │
                       ▼
                  Automatización
                       │
                       ▼
              Seguridad Ofensiva
                       │
              ┌────────┴────────┐
              │                 │
          Pentesting         Red Team
```

---

## Uso del repositorio

Si estás realizando Bandit por tu cuenta, la recomendación es intentar resolver cada nivel antes de consultar el writeup.

Los writeups pueden utilizarse posteriormente para:

* Comparar diferentes métodos de resolución.
* Repasar comandos de Linux.
* Comprender técnicas de enumeración.
* Revisar herramientas utilizadas en CTF.
* Reforzar conceptos de networking y shell.

---

## Seguridad y ética

Este repositorio tiene fines exclusivamente educativos.

Todos los ejercicios documentados fueron realizados dentro del entorno autorizado de **OverTheWire Bandit**.

Las técnicas aquí descritas no deben utilizarse contra sistemas sin autorización explícita.

---

<div align="center">

**33 / 33 — FINALIZADO**

```text
$ whoami
learner

$ echo $STATUS
completed
```

</div>

