**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective 

La contraseña para el siguiente nivel se encuentra almacenada **en un archivo oculto dentro del directorio `inhere`**.

El objetivo es localizar ese archivo y leer su contenido para obtener la contraseña del **Level 4**.

---
### Understanding the Challenge

En Linux, los archivos cuyo nombre comienza con `.` se consideran **archivos ocultos**.

Estos archivos **no aparecen con un `ls` normal**, por lo que es necesario usar opciones adicionales para visualizarlos.

---
### Enumeration 

Primero listamos el contenido del directorio actual:

```bash
ls
```

Output:

```Plain text
inhere
```

Entramos al directorio:

```bash
cd inhere
```

Si ejecutamos nuevamente `ls`:

```bash
ls
```

no aparecerá ningún archivo visible.

Para listar **archivos ocultos,** usamos:

```bash
ls -a
```

Output:

```Plain text
. .. ...Hiding-From-You
```

El archivo relevante es:

```Plain text
...Hiding-From-You
```

---
### Retrieving the Password

Para leer el contenido del archivo:

```bash
cat ...Hiding-From-You
```

Output:

```Plain text
[REDACTED]
```

Este valor corresponde a la contraseña para **Bandit Level 4.**

---
### Skills Practiced

- Identificación de **archivos ocultos en Linux**    
- Uso del comando `ls` con la opción `-a`
- Navegación básica entre directorios con `cd`

---
### Screenshots










