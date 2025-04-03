---
title: Introducción al shell
teaching: 5
exercises: 0
---


::::::::::::::::::::::::::::::::::::::: objectives

- Explicar cómo se relaciona el shell con el teclado, la pantalla, el sistema operativo y los programas de los usuarios.
- Explicar cuándo y por qué deben utilizarse interfaces de línea de comandos en lugar de interfaces gráficas.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- ¿Qué es un intérprete de comandos y por qué debería utilizarlo?

::::::::::::::::::::::::::::::::::::::::::::::::::

### Antecedentes

Los humanos y los ordenadores suelen interactuar de muchas formas diferentes, como a través de un teclado y un ratón, interfaces de pantalla táctil o utilizando sistemas de reconocimiento de voz. La forma más utilizada para interactuar con los ordenadores personales se denomina **interfaz gráfica de usuario** (GUI). Con una GUI, damos instrucciones haciendo clic con el ratón y utilizando interacciones basadas en menús.

Aunque la ayuda visual de una interfaz gráfica de usuario hace que el aprendizaje sea intuitivo, esta forma de dar instrucciones a un ordenador es muy poco escalable. Imagine la siguiente tarea: para una búsqueda bibliográfica, tiene que copiar la tercera línea de mil archivos de texto en mil directorios diferentes y pegarla en un único archivo. Si utilizara una interfaz gráfica de usuario, no sólo pasaría varias horas haciendo clic en su escritorio, sino que además podría cometer un error en el proceso de realización de esta tarea repetitiva. Aquí es donde aprovechamos las ventajas del shell de Unix. El shell de Unix es tanto una interfaz de línea de comandos (CLI) como un lenguaje de secuencias de comandos, que permite realizar estas tareas repetitivas de forma automática y rápida. Con los comandos adecuados, el shell puede repetir tareas con o sin alguna modificación tantas veces como queramos. Usando el shell, la tarea del ejemplo de la literatura puede realizarse en segundos.

### El Shell

El shell es un programa en el que los usuarios pueden escribir comandos. Con el shell, es posible invocar programas complicados como el software de modelado climático o comandos sencillos que crean un directorio vacío con una sola línea de código. El intérprete de comandos Unix más popular es Bash (Bourne Again SHell, así llamado porque deriva de un intérprete de comandos escrito por Stephen Bourne). Bash es el shell por defecto en la mayoría de las implementaciones modernas de Unix y en la mayoría de los paquetes que proporcionan herramientas tipo Unix para Windows. Ten en cuenta que 'Git Bash' es un software que permite a los usuarios de Windows utilizar una interfaz similar a Bash cuando interactúan con Git.

Utilizar el shell requiere cierto esfuerzo y tiempo de aprendizaje. Mientras que una interfaz gráfica de usuario te presenta opciones para seleccionar, las opciones de la CLI no se te presentan automáticamente, por lo que deberás aprender algunos comandos como si se tratara de vocabulario nuevo en un idioma que estás estudiando. Sin embargo, a diferencia de un idioma hablado, un pequeño número de "palabras" (es decir, comandos) te lleva un largo camino, y vamos a cubrir esos pocos esenciales hoy.

La gramática de un shell permite combinar herramientas existentes en potentes pipelines y manejar grandes volúmenes de datos de forma automática. Las secuencias de comandos pueden escribirse en un *script*, lo que mejora la reproducibilidad de los flujos de trabajo.

Además, la línea de comandos suele ser la forma más sencilla de interactuar con máquinas remotas y superordenadores. La familiaridad con el shell es casi esencial para ejecutar una variedad de herramientas y recursos especializados, incluidos los sistemas informáticos de alto rendimiento. A medida que los clústeres y los sistemas de computación en nube se hacen más populares para el procesamiento de datos científicos, ser capaz de interactuar con el intérprete de comandos se está convirtiendo en una habilidad necesaria. Podemos basarnos en las habilidades de la línea de comandos que se tratan aquí para abordar una amplia gama de cuestiones científicas y retos computacionales.

Empecemos.

Cuando se abre el intérprete de comandos por primera vez, aparece un **prompt**, que indica que el intérprete está esperando una entrada.

```bash
$
```

El shell suele utilizar `$ ` como prompt, pero puede utilizar un símbolo diferente. En los ejemplos de esta lección, mostraremos el prompt como `$ `. Lo más importante, *no escribas el prompt* cuando escribas comandos. Sólo escriba el comando que sigue al prompt. Esta regla se aplica tanto en estas lecciones como en lecciones de otras fuentes. También tenga en cuenta que después de escribir un comando, tiene que pulsar la tecla <kbd>Enter</kbd> para ejecutarlo.

El prompt va seguido de un **cursor de texto**, un carácter que indica la posición en la que aparecerá lo que escribas. El cursor suele ser un bloque parpadeante o sólido, pero también puede ser un guión bajo o una tubería. Es posible que lo hayas visto en un programa editor de texto, por ejemplo.

Ten en cuenta que tu prompt puede tener un aspecto algo diferente. En particular, los entornos de shell más populares ponen por defecto su nombre de usuario y el nombre del host antes de `$`. Un prompt de este tipo podría tener, por ejemplo, el aspecto siguiente

```bash
nelle@localhost $
```

El prompt puede incluir incluso más que esto. No se preocupe si su prompt no es sólo un corto `$ `. Esta lección no depende de esta información adicional y tampoco debería ser un obstáculo. El único elemento importante es el carácter `$ ` y veremos más adelante por qué.

Así que vamos a probar nuestro primer comando, `ls`, que es la abreviatura de listado. Este comando listará el contenido del directorio actual:

```bash
$ ls
```

```output
Desktop     Downloads   Movies      Pictures
Documents   Library     Music       Public
```

::::::::::::::::::::::::::::::::::::::::: callout

## Comando no encontrado

Si el shell no puede encontrar un programa cuyo nombre sea el comando que has escrito, imprimirá un mensaje de error como:

```bash
$ ks
```

```output
ks: command not found
```

Esto puede ocurrir si el comando se ha escrito mal o si el programa correspondiente a ese comando no está instalado.


::::::::::::::::::::::::::::::::::::::::::::::::::

## Nelle's Pipeline: Un problema típico

Nelle Nemo, bióloga marina, acaba de regresar de un estudio de seis meses en el [Giro del Pacífico Norte](https://en.wikipedia.org/wiki/North_Pacific_Gyre), donde ha estado tomando muestras de vida marina gelatinosa en el [Gran Parche de Basura del Pacífico](https://en.wikipedia.org/wiki/Great_Pacific_Garbage_Patch). Tiene 1520 muestras que ha pasado por una máquina de ensayo para medir la abundancia relativa de 300 proteínas. Tiene que pasar estos 1520 archivos por un programa imaginario llamado `goostats.sh`. Además de esta ingente tarea, tiene que escribir los resultados antes de fin de mes, para que su artículo pueda aparecer en un número especial de *Aquatic Goo Letters*.

Si Nelle elige ejecutar `goostats.sh` a mano utilizando una GUI, tendrá que seleccionar y abrir un archivo 1520 veces. Si `goostats.sh` tarda 30 segundos en ejecutar cada archivo, todo el proceso requerirá más de 12 horas de la atención de Nelle. Con el intérprete de comandos, Nelle puede asignar a su ordenador esta tarea mundana mientras se concentra en escribir su trabajo.

Las próximas lecciones explorarán las formas en que Nelle puede conseguirlo. Más concretamente, las lecciones explican cómo puede utilizar un intérprete de comandos para ejecutar el programa `goostats.sh`, utilizando bucles para automatizar los pasos repetitivos de introducción de nombres de archivo, de modo que su ordenador pueda trabajar mientras ella escribe su trabajo.

Como ventaja adicional, una vez que haya creado un canal de procesamiento, podrá volver a utilizarlo siempre que recopile más datos.

Para realizar su tarea, Nelle necesita saber cómo:

- navegar a un archivo/directorio
- crear un archivo/directorio
- comprobar la longitud de un archivo
- encadenar comandos
- recuperar un conjunto de archivos
- iterar sobre archivos
- ejecutar un script de shell que contenga su pipeline

:::::::::::::::::::::::::::::::::::::::: keypoints

- Un shell es un programa cuyo propósito principal es leer comandos y ejecutar otros programas.
- Esta lección utiliza Bash, el shell por defecto en muchas implementaciones de Unix.
- Los programas pueden ejecutarse en Bash introduciendo comandos en el prompt de la línea de comandos.
- Las principales ventajas del intérprete de comandos son su elevada relación entre acciones y pulsaciones, su capacidad para automatizar tareas repetitivas y su capacidad para acceder a máquinas en red.
- Un reto importante a la hora de utilizar el shell puede ser saber qué comandos hay que ejecutar y cómo ejecutarlos.

::::::::::::::::::::::::::::::::::::::::::::::::::



