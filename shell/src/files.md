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
