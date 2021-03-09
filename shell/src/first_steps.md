# Primeros pasos

## ¿Cómo abro una de esas terminales?

### Para Linux y MacOS:

Abre la carpeta o menú donde usualmente están tus aplicaciones, y
busca "terminal". En MacOS al escribir terminal en la barra de
Spotlight saldrá la terminal pre instalada. Esa es suficiente por
ahora.

En Linux las instrucciones específicas dependen de al distribución,
window manager y desktop environment. Un atajo rápido que funciona en
la mayoría de las distros es la combinación de teclas `ctrl + alt +
t`

### Para Windows:

La forma más fácil de obtener bash es descargando git
[aquí](https://git-scm.com/downloads). Después de eso puedes buscar
"git bash" en el menú windows y abrirlo.

## Una vez instalado

Al abrir la terminal aparecerá una pantalla con texto, y probablemente
una línea de texto con lo siguiente:

```bash
host:~$
```

Esta línea se suele llamar _prompt_ y quiere decir un par de cosas. La
primera palabra, en este caso `host` es el nombre de la computadora en
la que se está trabajando. Eso cambiará en cada caso particular.
Separado por `:` está un _tilde_ (`~`). Después de los dos puntos
encontramos el nombre de la carpeta actual. La tilde es una
abreviación para la carpeta "home" en tu sistema. Finalmente, hay un
signo `$`. El cursor siempre aparece después de él, e indica que se
pueden empezar a escribir comandos.

A partir de ahora adoptamos la convención de omitir el hostname y
directorio actual (current working directory). Las líneas de código
que comiencen con `$` deben ser interpretadas como una nueva línea en
la terminal. Por ejemplo, puedes correr este primer comando:


```bash
$ echo "Hola Mundo"
Hola mundo
```
