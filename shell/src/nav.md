# Navegación

En la sección pasada mencionamos que bash siempre muestra el
directorio actual en la línea de comandos, y lo llamamos current
working directory. Es importante tener en mente que la terminal
siempre tiene este concepto de directorio actual presente. Es como
abrir una ventana del explorador, siempre está abierta en una carpeta,
y los cambios que se hagan van a suceder _en esa carpeta_. Con la
terminal es similar, los comandos que se den tendrán efecto sobre los
archivos y carpetas en el directorio actual. Además de verlo en la
línea de comandos que da bash puedes usar un comando para obtener el
_path_[^1] completo.

```bash
$ pwd
/Users/alonsoc1s/Documents/itam4code/Cursos/shell/src
```

Los _paths_ que comienzan con `/` se llaman absolutos porque dan una
dirección desde la raíz del sistema de archivos. El directorio (o
carpeta) `/` es especial, pues es el directorio que contiene a todos
los otros. Otro directorio especial es `~` (tilde), que es el
directorio "home" del usuario actual. Por ejemplo, para mi es
`/Users/alonsoc1s`. Los _paths_ que no empiezan con `/` se llaman
relativos, y se interpretan como la dirección a algo a partir de el
directorio actual.

Otras abreviaturas importantes son el directorio `.` que se refiere al
directorio actual, y `..` que se refiere a el directorio padre. Por
ejemplo, puedes navegar una carpeta arriba con `cd ..`. Más tarde lo
veremos con más detalle.

[^1]: La palabra path se refiere a la dirección completa de un archivo
  o carpeta en tu sistema de archivos. Ayuda pensar que es como el
  camino que se debería seguir al navegar por el sistema de archivos
  para llegar hasta un lugar

Dadas las limitaciones de una interfaz de texto hay algunas cosas que
nos gustaría saber hacer. Por ejemplo listar los contenidos de la
carpeta actual, eliminar archivos, renombrarlos, moverlos, y movernos
entre carpetas, entre otras cosas.

## Trabajando con carpetas y archivos

Para listar los contenidos del directorio actual se usa el comando
`ls`. Mnemónico útil: **l**i**s**t

```bash
$ ls
book
book.toml
figs
src
```

En este ejemplo en mi directorio actual tengo algunas carpetas y
algunos archivos. Puedes notar cual es cual porque los archivos suelen
tener extensiones (como `.toml` en el caso de `book`).

Los comandos como `ls` también pueden tomar "argumentos" u opciones.
Por ejemplo, `ls` tiene opciones para ver a quién le pertenecen los
contenidos de un directorio y cuando se modificaron por última vez.

```bash
$ ls -l -a
total 32
drwxr-xr-x   8 alonsoc1s  staff   256 Mar  9 14:08 .
drwxr-xr-x   9 alonsoc1s  staff   288 Mar  8 23:09 ..
-rw-r--r--@  1 alonsoc1s  staff  6148 Mar  9 08:36 .DS_Store
-rw-r--r--   1 alonsoc1s  staff     5 Mar  8 21:13 .gitignore
drwxr-xr-x  33 alonsoc1s  staff  1056 Mar  9 14:37 book
-rw-r--r--   1 alonsoc1s  staff   124 Mar  8 21:13 book.toml
drwxr-xr-x   4 alonsoc1s  staff   128 Mar  8 23:03 figs
drwxr-xr-x  15 alonsoc1s  staff   480 Mar  8 21:33 src
```

Por ahora no importan los detalles del output del comando anterior,
solo la sintaxis para dar argumentos a un comando. La sintaxis
estándar es `-` y una letra, o bien `--` y el nombre largo de la
opción. Bash valora mucho la eficiencia, entonces los nombres de los
comandos son lo más cortos posibles, como una letra. El ejemplo
anterior se puede hacer aún más corto! Cuando se tienen varios
argumentos de una sola letra se pueden combinar bajo el mismo `-` para
formar algo como:

```bash
$ ls -la
```

En ocasiones se puede poner tan ~~ridículo~~ complejo como

```bash
$ curl -fsSL
```

### Entonces ¿se supone que me sepa **todos** los posibles comandos?

Usualmente solo se usan un par de argumentos para algún comando, 
dependiendo de qué uso común le demos. Pero no es necesario saberlos 
todos. Casi todos los comandos de bash e incluso los que se puedan 
instalar aparte por el usuario tienen un argumento especial: `-h`, 
corto para help. Por ejemplo, podemos ver los posibles argumentos de 
`ls` así

```bash
$ ls -h

