# Otros comandos útiles

El contenido de los últimos capítulos puede parecer restrictivo y es
porque si lo es. Esos son apenas los fundamentos para hacer cosas que
ya sabías hacer en tu explorador de archivos. Pero la terminal tiene
mucho más qué ofrecer, y algunas de estas herramientas te pueden ser
muy útiles a la hora de resolver los problemas con los que se suele
encontrar una persona que desarrolla software. Esto es apenas un
teaser, no se cubre ningún comando con particular atención.

## Grep

Con el comando `grep` podemos encontrar texto dentro de archivos u
otros medios de input a la terminal. Lo interesante es que `grep` no
solo encuentra texto tal cual, sino que está equipado para encontrar
*patrones* usando un subconjunto de algo llamado "expresiones
regulares" que amerita sus propias notas. Basta saber que `*` sirve
para encontrar "cualquier cadena de caracteres", de la misma manera en
la que usamos `*` antes para seleccionar todos los archivos dentro de
una carpeta. Veremos esto más a detalle.

Por ejemplo, digamos que busco las líneas que contengan la palabra
"terminal" en estas notas.

```bash
$ grep terminal *
files.md:Una vez más, el usar una terminal nos permite ahorrarnos algunos pasos
first_steps.md:## ¿Cómo abro una de esas terminales?
first_steps.md:busca "terminal". En MacOS al escribir terminal en la barra de
historia.md:las estaciones con teclados se llamaban _terminales_
intro.md:Muchas personas argumentan que las _terminales_ son
meta.md:algo que se debe de escribir en la terminal. A veces se usa también
nav.md:working directory. Es importante tener en mente que la terminal
```

Grep muestra el nombre del archivo donde encontró una coincidencia,
seguido de la línea donde está.

## Less

A veces nos interesa dar un vistazo rápido a un archivo, y localizarlo
en la terminal para después abrirlo en el explorador de archivos es
muy ineficiente. Para eso existe el comando `less`. El comando actúa
como un paginador, algo que parte el archivo en la cantidad de líneas
que caben en tu ventana actual. Para avanzar una "página" puedes usar
la barra de espacio, para ir atrás una puedes usar la tecla b. Para
salir presiona q.

El comando `man` mencionado en la sección sobre navegación utiliza un
paginador muy similar, también puedes salir de ahí presionando q. El
nombre `less`puede parecer contraintuitivo. Se debe a que es sucesor
de otro paginador llamado `more` por el texto `--MORE--` que aparece
en la parte de abajo de la pantalla cuando lo usas.

## Head & Tail

A veces usar `less` es más de lo necesario. Si necesitas información
de las primeras líneas en un archivo, puedes usar `head`, y si
necesitas información de las últimas, puedes usar `tail`. Los nombres
de los comandos son auto-descriptivos. Cabe mencionar que se puede
ajustar el número de líneas que muestran `head` y `tail`. ¿Cuál es la
sintaxis para eso? Buen momento para poner en práctica `man`!

## Diff

En muchas ocasiones es útil comparar dos archivos. Por ejemplo,
archivos `.csv` con muchas filas de datos. Diff permite comparar
archivos línea por línea y solo muestra las líneas que no coinciden.
Si los archivos coinciden en todos lados no muestra nada. Se usa así:

```bash
diff archivo_a.csv archivo_b.csv
```

## Find

Otra cosa que podrías extrañar de tu explorador de archivos es la
barra de búsqueda. También se pueden buscar archivos en la misma
terminal. Por ejemplo, si sabes con seguridad que buscas un archivo
específico en alguna parte del árbol de archivos puedes buscarlo sin
importar a qué profundidad esté. Por ejemplo, puedo buscar el archivo
`meme_git.png` de un ejemplo anterior dentro de mis Documentos.

```bash
$ find ~/Documents/ -name meme_git.png
```

Esta forma de buscar también da el poder de buscar archivos *por sus
contenidos*, o dando un patrón de búsqueda para el nombre de archivo
al estilo de `grep`, pero eso es algo avanzado para este curso.

## Uniq

El comando `uniq` por default muestra las líneas únicas "no repetidas"
en un archivo de texto. Suele ser muy común pegar dos veces al copiar
una línea, entonces una manera rápida de verificar es usando `uniq`.
El comando también se puede configurar para solo mostrar las
repetidas, lo cual es útil en archivos de texto como escritos o
scripts, mientras que la configuración estándar es útil por ejemplo
para detectar observaciones repetidas en un archivo de formato `.csv`.

```bash
$ uniq README.md # Encuentra líneas únicas en el archivo.
```
