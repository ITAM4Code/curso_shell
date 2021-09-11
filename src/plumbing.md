# Un poco de plomería

Ya vimos algunos ejemplos de cómo la terminal de mucho poder al
usuario que sabe usarla, su auténtico poder se libera haciendo uso de
las características que precisamente la hacen diferente a trabajar con
un navegador de archivos, por ejemplo. Es bueno recordar que un
_shell_ es un intérprete de comandos en toda la extensión de la
palabra.

## Inputs, outputs, errores

Hasta ahora hemos usado los términos _input_ y _output_ sin mucho
cuidado. Ahora habrá que clarificar su uso, porque son conceptos muy
importantes. El que el _shell_ tenga concepto de esto le permite hacer
mucho más que crear y mover archivos ociosamente. No hay que olvidar
que en tiempos de UNIX ésta era la única manera de interactuar con una
computadora, y muchas personas hacían tareas complejas como procesar
texto, todo sin siquiera acercase a algo como word.

Como mencionamos antes, los comandos tienen un output determinado.
Este se suele mostrar en la terminal justo después de que se corrió el
comando, como lo hemos estado mostrando en estas notas. Los comandos
de bash están diseñados para usar dos canales de comunicación con el
usuario: standard out (stdout) y standard error (stderr). Cuando
creamos un archivo con el comando,

```bash
$ ls > contenidos.txt
```

redirigimos des stdout hacia otro lugar, en donde bash lo tomó y lo
mandó como contenido al archivo `contenidos.txt`. Ese lugar se llama
standard in (stdin). Entonces, ahora tenemos un canal para enviar
información a comandos, y dos en los cuales la recibimos. Esta
redirección es mucho más versátil que solo escribir archivos nuevos.

## El pipe

El operador `>` nos permitió redirigir stdout a un archivo. Lo
interesante es que se puede redirigir de stdout directo a stdin para
que otros comandos los puedan leer. Por ejemplo, `less` tomaba como
argumento un nombre de archivo, pero en realidad no es necesario
dárselo! Si se corre `less` sin argumentos, tratará de leer de stdin.
En un ejemplo concreto, podemos usar el ejemplo de `grep` otra vez y
ahora buscar una palabra muy común. Por ejemplo:

```bash
$ grep el *
```

Ese comando buscará las líneas donde aparezca la palabra "el" en los
archivos que componen éstas notas. Es de esperarse que haya muchos
resultados, por lo que `grep` llenará la pantalla sin problemas. Si se
quiere hacer una análisis minucioso de las apariciones, _scrollear_
arriba y abajo en la ventana de la terminal no es lo más cómodo.
Intentemos escribirlo a un archivos!

```bash
$ grep el * > resultados.txt
```

Ahora podemos usar `less` para abrir el archivo con más comodidad.

```bash
$ less resultados.txt
```

Pero, ¿no se siente arcaico crear un archivo intermedio para después
tener que borrarlo? Lo es. Podemos evitar este paso dándolo a `less`
lo que queremos que nos muestre directamente.

```bash
$ grep el * | less
```

El caracter `|` se llama _pipe_ en inglés. En términos simples, toma
el stdout del lado izquierdo y lo manda a stdin para el comando del
lado derecho. Esto se llama "piping" en inglés y me referiré a ello
como "pipear" a falta de una mejor traducción.

En el ejemplo anterior estamos tomando stdout de `grep`, el listado de
coincidencias como en el ejemplo de la sección anterior, y en vez de
mostrarlo todo al mismo tiempo en la terminal, lo envía como input a
`less`, que como recordamos, toma ese texto y lo divide en páginas
para facilitar su lectura.

No hay límite para cuantos comandos se pueden encadenar uno tras otro,
y el uso creativo de estos bloques básicos de construcción da para
resultados realmente increíbles. Al principio de las notas se comentó
que la filosofía de diseño UNIX era crear muchos programas pequeños
diseñados para hacer una y solo una cosa muy bien. Ahora debería hacer
más sentido esa decisión de diseño. No se necesitan programas
complicados cuando se tiene los ladrillos y el cemento, y mucha
creatividad.

Los ejemplos más bellos de éste concepto en acción los da el mismísimo
Brian Kernighan en esta [joya
histórica](https://www.youtube.com/watch?v=tc4ROCJYbm0), un documental
de UNIX con la aparición de los iconos Kernighan y Ritchie.
