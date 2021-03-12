# Archivos

Ahora revisamos algunas de las tareas básicas del día a día con
respecto a archivos. Por ejemplo, mover, renombrar, copiar y borrar.
Continuamos con el ejemplo de la sección anterior con una carpeta que
se ve así:

```bash
$ ls
book
book.toml
src
```

## Moviendo archivos

Por ejemplo, si decidimos que el archivo `book.toml` debería estar en
la carpeta `book`, podemos usar el comando `mv` (**m**o**v**e).

```bash
$ mv book.toml book
```

Una vez más, el usar una terminal nos permite ahorrarnos algunos pasos
extra que tendríamos que dar trabajando con el explorador gráfico de
archivos. Por ejemplo, si hay un archivo `importante.txt` dentro de la
carpeta `book` y queremos moverlo a la carpeta actual, un primer
instinto sería movernos dentro de `book` con `cd`, y mover el archivo
hacia arriba con `mv importante.txt ..` (recordar que `..` hace
referencia al directorio padre). Pero hay un camino más fácil. Como
podemos referirnos a objetos en el sistema de archivos con paths
relativos y absolutos podemos mover y copiar cosas por todo el árbol
de archivos sin tener que cambiar de carpeta una sola vez. Para este
ejemplo específico podemos usar el comando que está abajo. Nótese que
`.` hace referencia a la carpeta actual.

```bash
$ mv book/importante.txt .
```

En este caso `mv` toma dos argumentos: El primero es el nombre del
archivo que se va a mover, y el segundo es a dónde será movido. Es
decir, primero recibe un nombre de archivo, y luego un nombre de
directorio. Es importante notar que no solo el orden es importante,
sino que darle argumentos diferentes a el mismo comando resulta en
comportamientos diferentes. El caso particular de `mv` lo revisaremos
ahora mismo.

## Renombrando archivos

Cuando se utiliza `mv` con dos argumentos, ambos nombres de archivos,
`mv` cambia el nombre del archivo en el primer argumento. En un
ejemplo concreto, tomemos el archivos `book.toml` y cambiemos el
nombre a `libro.toml`.

```bash
$ mv book.toml libro.toml
$ ls # Usamos ls para verificar que funcionó. No es necesario
book
libro.toml
src
```

## Copiando archivos

Copiar archivos es muy simple. El comando para hacerlo se llama `cp`
(por **c**o**p**y). Su sintaxis es muy similar a la de `mv`, toma por
primer argumento el nombre del archivo que se va a copiar, y el
segundo argumento es el nombre del archivo copia. Por ejemplo, si
queremos hacer un backup de `book.toml` lo podemos hacer con el
siguiente comando.

```bash
$ cp book.toml book_backup.toml
```

Como ya es costumbre, podemos usar paths relativos o absolutos para
copiar cualesquiera dos archivos en el sistema de archivos, sin
importar qué tan lejos estén. Por ejemplo, para la creación de estas
notas usé una foto que ya tenía guardada en mis archivos en otro
carpeta lejana.

```bash
$ cp ~/Documents/projects/meme_git.png meme_git.png
```

Nótese que el segundo argumento es un nombre de archivo simple, o eso
parece a primera vista. En realidad se puede pensar como un path
relativo! Es un path que apunta directamente al current working
directory. Entonces el comando anterior copia un archivo
`meme_git.png` localizado en `~/Documents/projects/` a el directorio
actual con el nombre `meme_git.png`.

## Borrando carpetas y archivos

> ADVERTENCIA: A diferencia de usar un explorador de archivos gráfico,
> borrar un archivo o carpeta no envía archivos a una papelera u otro
> espacio intermedio. Lo que se borra con estos comandos NO HAY MANERA
> DE RECUPERAR.

Borrar archivos es tan fácil como moverlos o renombrarlos, hay un
comando de nombre fácil de recordar. Ese comando se llama `rm` por
**r**e**m**ove. A diferencia de por ejemplo `mv`, `rm` solo necesita
un argumento: el nombre del archivo a borrar. Sin embargo puede tomar
muchos argumentos y todos ellos serán borrados. Por ejemplo, si
queremos borrar el archivo `book.toml` el siguiente comando lo hace.

```bash
$ rm book.toml
```

Realmente no hay mucho más qué decir respecto a borrar archivos, pero
borrar carpetas requiere un poco más de discusión. Si intentamos
borrar una capeta no-vacía con la misma estrategia con la que borramos
un archivo obtendremos un error.

```bash
$ rm book
rm: book: is a directory
```

Dado que no hay un undo para `rm`, el comando tiene un poco de
seguridad integrada. Detecta que la carpeta `book` no está vacía, y
avisa para que no borres una cantidad enorme de archivos por error. Si
efectivamente querías borrar toda la carpeta y sus contenidos hay un
modificador que permite hacer eso: `-r` por `--recursive`. Por
ejemplo.

```bash
$ rm -r book
```
Otro comando para eliminar carpetas es `rmdir`.

> En foros para principiantes de Linux hay un comando "de broma" muy
> común: `sudo rm -rf /*`. Nunca nunca es buena idea correr este
> comando. `sudo` es un comando que da permisos de
> administrador para correr un comando. Puntos extra si logras ver
> porqué es mala idea correr este comando.
