**Wargame:** Bandit  
**Platform:** OverTheWire

---
### Objective

En este nivel debemos **interactuar con el repositorio Git de manera activa**. Nuestro objetivo es **subir (push) un archivo específico** al repositorio remoto para que el servidor valide el contenido y nos revele la contraseña del siguiente nivel.

---
### Understanding the Challenge

El README del repositorio nos da instrucciones claras:

```Plain text
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

Debemos crear un archivo llamado `key.txt` con el contenido exacto `'May I come in?'` y subirlo a la rama `master` del repositorio remoto. El servidor tiene un **hook** que valida el archivo y, si es correcto, muestra la contraseña.

---
### Creating the Required File

Creamos el archivo `key.txt` con el contenido exacto solicitado:

```bash
echo 'May I come in?' > key.txt
```

---
### Adding and Committing the File

Añadimos el archivo al área de staging. Usamos `-f` para forzar si es necesario:

```bash
git add -f key.txt
```

Realizamos el commit:

```bash
git commit -m "nimodo"
```

Output:

```Plain text
En la rama master
Tu rama está adelantada a 'origin/master' por 1 commit.
  (usa "git push" para publicar tus commits locales)

nada para hacer commit, el árbol de trabajo está limpio
```

---
### Pushing to the Remote Repository

Ahora subimos los cambios al repositorio remoto:

```bash
git push
```

Output:

```Plain text
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit31-git@bandit.labs.overthewire.org's password: 
Enumerando objetos: 4, listo.
Contando objetos: 100% (4/4), listo.
Compresión delta usando hasta 12 hilos
Comprimiendo objetos: 100% (2/2), listo.
Escribiendo objetos: 100% (3/3), 335 bytes | 335.00 KiB/s, listo.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: [REDACTED] <- **contraseña**
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
To ssh://bandit.labs.overthewire.org:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: falló el empuje de algunas referencias a 'ssh://bandit.labs.overthewire.org:2220/home/bandit31-git/repo'
```

---
### Retrieving the Password

A pesar de que el `push` es rechazado (el hook decline el push), el servidor **igualmente ejecuta la validación** y nos muestra la contraseña:

```Plain text
[REDACTED]
```

Este valor corresponde a **la contraseña para Bandit Level 32.**

---
### Skills Practiced

- **Clonación** de repositorios Git remotos
- **Creación** de archivos con contenido específico
- **Añadir** archivos al staging area con `git add -f`
- **Commit** de cambios localmente (`git commit`)
- **Push** de cambios al repositorio remoto (`git push`)
- Comprensión de **Git hooks** (`pre-receive`) en el servidor remoto
- Interpretación de mensajes del servidor aunque el push sea rechazado    

---
### Screenshots

