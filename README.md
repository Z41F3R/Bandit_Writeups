![bandit](image.png)

![OverTheWire](https://img.shields.io/badge/OverTheWire-Bandit-2ea44f?style=for-the-badge&logo=linux&logoColor=white)
![Niveles](https://img.shields.io/badge/Niveles-33_completados-2ea44f?style=for-the-badge)
![Estado](https://img.shields.io/badge/Estado-Finalizado-gold?style=for-the-badge)

Repositorio que documenta la resolución progresiva del wargame Bandit, un viaje enfocado en el desarrollo de habilidades prácticas en sistemas Linux, manipulación de archivos y la aplicación de fundamentos esenciales para entornos CTF (Capture The Flag).

---

### Sobre el proyecto

Este repositorio es más que una simple colección de contraseñas; es la evidencia tangible de un proceso de aprendizaje estructurado. Cada nivel resuelto representa un paso adelante en la consolidación de habilidades clave para la ciberseguridad.

**¿Qué encontrarás aquí?**

🖥️ **Uso práctico de comandos Linux:** Desde ls y cat hasta nmap, openssl y grep.

🧩 **Análisis y resolución de problemas:** Un enfoque paso a paso para superar cada reto.

🔒 **Comprensión de conceptos clave:** Permisos, procesos, redes, criptografía básica y más.

📝 **Documentación estructurada:** Cada solución incluye el comando utilizado, una explicación clara del razonamiento y el proceso aplicado.

---

### Niveles completados

La siguiente tabla resume el camino recorrido. Cada enlace te llevará a un writeup detallado con la solución y las reflexiones detrás de ella.

| Nivel | Descripción | Link |
|------|------------|------|
| 0 → 1 | Conexión inicial vía SSH | [Ver](levels/level-00.md) |
| 1 → 2 | Lectura de archivo con nombre especial (`-`) | [Ver](levels/level-01.md) |
| 2 → 3 | Manejo de archivos con espacios en el nombre | [Ver](levels/level-02.md) |
| 3 → 4 | Búsqueda de archivos ocultos | [Ver](levels/level-03.md) |
| 4 → 5 | Identificación de archivos por tipo (`file`) | [Ver](levels/level-04.md) |
| 5 → 6 | Búsqueda con criterios específicos (`find`) | [Ver](levels/level-05.md) |
| 6 → 7 | Búsqueda avanzada en el sistema | [Ver](levels/level-06.md) |
| 7 → 8 | Filtrado en archivos grandes (`grep`) | [Ver](levels/level-07.md) |
| 8 → 9 | Identificación de líneas únicas (`uniq`) | [Ver](levels/level-08.md) |
| 9 → 10 | Extracción de texto legible desde binarios (`strings`) | [Ver](levels/level-09.md) |
| 10 → 11 | Decodificación Base64 | [Ver](levels/level-10.md) |
| 11 → 12 | Transformación de texto ROT13 (`tr`) | [Ver](levels/level-11.md) |
| 12 → 13 | Descompresión en múltiples capas (`xxd`, `gzip`, `tar`) | [Ver](levels/level-12.md) |
| 13 → 14 | Autenticación mediante clave privada SSH | [Ver](levels/level-13.md) |
| 14 → 15 | Interacción con servicios remotos (`nc`) | [Ver](levels/level-14.md) |
| 15 → 16 | Conexión segura con SSL/TLS (`openssl s_client`) | [Ver](levels/level-15.md) |
| 16 → 17 | Enumeración de puertos (`nmap`) | [Ver](levels/level-16.md) |
| 17 → 18 | Comparación de archivos (`diff`) | [Ver](levels/level-17.md) |
| 18 → 19 | Ejecución en entorno restringido | [Ver](levels/level-18.md) |
| 19 → 20 | Escalación de privilegios | [Ver](levels/level-19.md) |
| 20 → 21 | Comunicación entre procesos | [Ver](levels/level-20.md) |
| 21 → 22 | Análisis de tareas programadas (`cron`) | [Ver](levels/level-21.md) |
| 22 → 23 | Revisión de scripts automatizados | [Ver](levels/level-22.md) |
| 23 → 24 | Manipulación de scripts programados | [Ver](levels/level-23.md) |
| 24 → 25 | Ataque de fuerza bruta controlado | [Ver](levels/level-24.md) |
| 25 → 26 | Interacción con shell restringida | [Ver](levels/level-25.md) |
| 26 → 27 | Evasión de restricciones en terminal | [Ver](levels/level-26.md) |
| 27 → 28 | Uso básico de repositorios Git | [Ver](levels/level-27.md) |
| 28 → 29 | Análisis de historial en repositorios Git | [Ver](levels/level-28.md) |
| 29 → 30 | Recuperación de información desde commits | [Ver](levels/level-29.md) |
| 30 → 31 | Uso de etiquetas y referencias en Git | [Ver](levels/level-30.md) |
| 31 → 32 | Interacción con repositorio remoto (`push`) | [Ver](levels/level-31.md) |
| 32 → 33 | Evasión de restricciones en shell avanzada | [Ver](levels/level-32.md) |

---

### Habilidades desarrolladas

Este viaje a través de Bandit ha permitido fortalecer y aplicar un conjunto de habilidades fundamentales:

- **Administración básica de sistemas Linux:** Navegación, manipulación de archivos, gestión de permisos y procesos.

- **Manejo de archivos y directorios:** Desde archivos con nombres complejos hasta la búsqueda recursiva con criterios específicos.

- **Procesamiento de texto en consola:** Dominio de herramientas como grep, awk, sed, sort, uniq y redirecciones.

- **Análisis de datos en entornos restringidos:** Extracción de información de binarios, logs y servicios de red.

- **Fundamentos de redes y criptografía:** Uso de netcat, openssl, codificaciones y cifrados básicos.

- **Pensamiento analítico y resolución de problemas:** Aplicación de la metodología CTF para superar desafíos progresivos.

---

### Uso del repositorio

1. **Explora secuencialmente:** Sigue la tabla de niveles para una progresión lógica.

2. **Busca por concepto:** Si quieres repasar un comando o técnica específica, revisa los títulos de los writeups.

3. **Aprende haciendo:** Lo ideal es intentar resolver el nivel por ti mismo antes de consultar la solución.

---

### Notas

Este proyecto es parte de mi formación continua en ciberseguridad. No solo es un registro de retos superados, sino una bitácora de aprendizaje que busca ayudar a otros en el mismo camino. Cada nivel es un recordatorio de que la mejor manera de aprender es poniendo manos a la tecla.

“La práctica no es lo que haces una vez que eres bueno. Es lo que te hace bueno.”
