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

Para crear un directorio podemos usar el directorio `mkdir`. Es fácil
recordar el nombre porque casi de lee "makedir". Por ejemplo para
crear una carpeta llamada prueba en el directorio actual, una carpeta
dentro de una carpeta llamada padre, o una carpeta en un path
arbitrario podemos hacer:

```bash
$ mdir prueba # Crear en el directorio actúal una carpeta llamada prueba
$ mkdir -p prueba/dir_hijo # Crear carpeta dentro de otra
$ mkdir dir1 dir2 dir3 # Crear muchas carpetas con un solo comando
```

## Una manera de crear archivos

Bash da muchas opciones para crear nuevos archivos e incluso nos deja
ponernos muy creativos. Una de las opciones más fáciles es usando el
comando `touch` con el nombre del archivo nuevo.

```bash
$ touch nuevo_archivo.txt
```

El archivo `nuevo.txt` estará vacío y se creará con la extensión
específica. Técnicamente `touch` hace más que crear archivos, pero es
muy útil para crearlos rápidamente.

Una manera más divertida de crear archivos es crearlos
_redireccionando_ el resultado de otros comandos y guardarlo en un
archivo nuevo. Por ejemplo, usando `ls` podemos guardar en un archivo
nuevo llamado `carpetas.txt` todas las carpetas presentes en el
directorio actual.

```bash
$ ls > carpetas.txt
```

El operador `>` redirige el _output_ que resulta de correr `ls`.
Usualmente `ls` y la mayoría de comandos imprimen en la terminal sus
resultados. Ese texto es tomado por `>` y enviado como contenido a un
archivo. Por ejemplo, otra manera de crear un archivo con texto
predeterminado se puede hacer con `echo`.

```bash
$ echo "# Esto es un readme" > README.md
```

Como mencionamos antes `echo` hace lo que el nombre sugiere: toma
texto y lo imprime tal cual en la terminal. En el ejemplo anterior
está tomando el texto "# Esto es un readme" y lo está escribiendo tal
cual en archivo `README.MD`. Si no existía lo crea, pero si ya existía
borra los contenidos anteriores y los reemplaza. Si no es eso lo que
queremos y preferimos añadir al contenido anterior podemos usar el
operador `>>`, que funciona exactamente igual pero evita perder la
información que ya estaba en el archivo.

### Ejemplo de uso común

El comando `cat` sigue bien la tradición de nombres cortos y auto
descriptivos. En este caso es corto para "concatenate", y hace justo
eso. Recibe como argumentos nombres de archivos, y pega los contenidos
de éstos uno detrás de otro. Esto es muy útil en muchas situaciones.

Por ejemplo, si se tienen dos o más archivos, ¿cómo juntar sus
contenidos en un archivo nuevo? Usando un mouse la solución obvia
sería abrir cada archivo uno por uno, copiar sus contenidos y pegarlos
en algún otro lugar. Usando la terminal esto se puede hacer
escribiendo una sola línea de texto:

```bash
$ cat autores.txt contenido.txt >> doc.txt
```
Podría parecer que este es un ejemplo de juguete, y hasta cierto punto
lo es. Pero es una situación que surge comúnmente en la práctica y se
puede hacer aún más poderoso. Por ejemplo, ¿qué tal si hay demasiados
archivos como para listarlos uno por uno? Por ejemplo, digamos que hay
muchos archivos de texto que guardan notas de clase y están numerados
por clase y necesitas todo en un solo archivo. Pensando que los
archivos se llaman `clase_1.txt, clase_2.txt, ...` y así
sucesivamente, podemos usar el siguiente comando.

```bash
$ cat clase_*.txt >> clases.txt
```

El `*` permite seleccionar todos los números al final del nombre de
los archivos. Hay otra variedad de patrones que permiten seleccionar
archivos dependiendo de patrones, pero lo veremos más tarde. El
concepto de redirección también lo revisaremos más tarde. ¿Ya se
empieza a ver el poder de la terminal?

### Entonces ¿se supone que me sepa **todos** los posibles comandos?

Usualmente solo se usan un par de argumentos para algún comando,
dependiendo de qué uso común le demos. Pero no es necesario saberlos
todos. Casi todos los comandos de bash e incluso los que se puedan
instalar aparte por el usuario tienen un argumento especial: `-h`,
corto para `--help`. Por ejemplo, podemos ver los posibles argumentos
de `cat` así.

```bash
$ cat --help
Usage: cat [OPTION]... [FILE]...
Concatenate FILE(s) to standard output.

With no FILE, or when FILE is -, read standard input.

  -A, --show-all           equivalent to -vET
  -b, --number-nonblank    number nonempty output lines, overrides -n
  -e                       equivalent to -vE
  -E, --show-ends          display $ at end of each line
  -n, --number             number all output lines
  -s, --squeeze-blank      suppress repeated empty output lines
  -t                       equivalent to -vT
  -T, --show-tabs          display TAB characters as ^I
  -u                       (ignored)
  -v, --show-nonprinting   use ^ and M- notation, except for LFD and TAB
      --help     display this help and exit
      --version  output version information and exit

Examples:
  cat f - g  Output f's contents, then standard input, then g's contents.
  cat        Copy standard input to standard output.

GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
Full documentation at: <http://www.gnu.org/software/coreutils/cat>
or available locally via: info '(coreutils) cat invocation'
```
