---
title: Pipes y filtros
teaching: 25
exercises: 10
---


::::::::::::::::::::::::::::::::::::::: objectives

- Explica la ventaja de enlazar comandos con pipes y filtros.
- Combina secuencias de comandos para obtener una nueva salida
- Redirige la salida de un comando a un archivo.
- Explica qué ocurre normalmente si un programa o una pipe no recibe ninguna entrada para procesar.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- ¿Cómo puedo combinar comandos existentes para producir una salida deseada?
- ¿Cómo puedo mostrar sólo una parte de la salida?

::::::::::::::::::::::::::::::::::::::::::::::::::

Ahora que ya conocemos algunos comandos básicos, por fin podemos echar un vistazo a la característica más poderosa del shell: la facilidad con la que nos permite combinar programas existentes de nuevas formas. Empezaremos con el directorio `shell-lesson-data/exercise-data/alkanes` que contiene seis archivos que describen algunas moléculas orgánicas simples. La extensión `.pdb` indica que estos archivos están en formato Protein Data Bank, un formato de texto simple que especifica el tipo y la posición de cada átomo en la molécula.

```bash
$ ls
```

```output
cubane.pdb    methane.pdb    pentane.pdb
ethane.pdb    octane.pdb     propane.pdb
```

Vamos a ejecutar un comando de ejemplo:

```bash
$ wc cubane.pdb
```

```output
20  156 1158 cubane.pdb
```

`wc` es el comando 'word count': cuenta el número de líneas, palabras y caracteres en ficheros (devolviendo los valores en ese orden de izquierda a derecha).

Si ejecutamos el comando `wc *.pdb`, el `*` en `*.pdb` coincide con cero o más caracteres, por lo que el shell convierte `*.pdb` en una lista de todos los ficheros `.pdb` en el directorio actual:

```bash
$ wc *.pdb
```

```output
  20  156  1158  cubane.pdb
  12  84   622   ethane.pdb
   9  57   422   methane.pdb
  30  246  1828  octane.pdb
  21  165  1226  pentane.pdb
  15  111  825   propane.pdb
 107  819  6081  total
```

Observe que `wc *.pdb` también muestra el número total de todas las líneas en la última línea de la salida.

Si ejecutamos `wc -l` en lugar de sólo `wc`, la salida muestra sólo el número de líneas por fichero:

```bash
$ wc -l *.pdb
```

```output
  20  cubane.pdb
  12  ethane.pdb
   9  methane.pdb
  30  octane.pdb
  21  pentane.pdb
  15  propane.pdb
 107  total
```

Las opciones `-m` y `-w` también pueden usarse con el comando `wc` para mostrar sólo el número de caracteres o el número de palabras, respectivamente.

::::::::::::::::::::::::::::::::::::::::: callout

## ¿Por qué no hace nada?

¿Qué pasa si un comando debe procesar un fichero, pero no le damos un nombre de fichero? Por ejemplo, ¿qué pasa si escribimos:

```bash
$ wc -l
```

pero no escribe `*.pdb` (ni nada más) después del comando? Dado que no tiene ningún nombre de archivo, `wc` asume que se supone que debe procesar la entrada dada en el símbolo del sistema, por lo que simplemente se sienta allí y espera a que le demos algunos datos de forma interactiva. Desde el exterior, sin embargo, todo lo que vemos es que se sienta allí, y el comando no parece hacer nada.

Si comete este tipo de error, puede salir de este estado manteniendo pulsada la tecla control (<kbd>Ctrl</kbd>) y pulsando la letra <kbd>C</kbd> una vez: <kbd>Ctrl</kbd>\+<kbd>C</kbd>. A continuación, suelta ambas teclas.


::::::::::::::::::::::::::::::::::::::::::::::::::

## Capturando la salida de los comandos

¿Cuál de estos ficheros contiene menos líneas? Es una pregunta fácil de responder cuando sólo hay seis ficheros, pero ¿y si hubiera 6000? Nuestro primer paso hacia la solución es ejecutar el comando

```bash
$ wc -l *.pdb > lengths.txt
```

El símbolo mayor que, `>`, indica al shell que **redirija** la salida del comando a un fichero en lugar de imprimirla en pantalla. Este comando no imprime ninguna salida en pantalla, porque todo lo que `wc` hubiera impreso ha ido al fichero `lengths.txt` en su lugar. Si el archivo no existe antes de emitir el comando, el shell creará el archivo. Si el archivo ya existe, se sobrescribirá silenciosamente, lo que puede provocar la pérdida de datos. Por lo tanto, los comandos **redirigir** requieren precaución.

`ls lengths.txt` confirma que el archivo existe:

```bash
$ ls lengths.txt
```

```output
lengths.txt
```

Ahora podemos enviar el contenido de `lengths.txt` a la pantalla usando `cat lengths.txt`. El comando `cat` recibe su nombre de 'concatenar', es decir, unir, e imprime el contenido de los ficheros uno tras otro. En este caso sólo hay un fichero, así que `cat` sólo nos muestra lo que contiene:

```bash
$ cat lengths.txt
```

```output
  20  cubane.pdb
  12  ethane.pdb
   9  methane.pdb
  30  octane.pdb
  21  pentane.pdb
  15  propane.pdb
 107  total
```

::::::::::::::::::::::::::::::::::::::::: callout

## Salida Página por Página

Continuaremos usando `cat` en esta lección, por conveniencia y consistencia, pero tiene la desventaja de que siempre vuelca todo el fichero en la pantalla. Más útil en la práctica es el comando `less` (por ejemplo `less lengths.txt`). Esto muestra un pantallazo del archivo, y luego se detiene. Puedes avanzar una pantalla pulsando la barra espaciadora, o retroceder una pulsando `b`. Pulsa `q` para salir.


::::::::::::::::::::::::::::::::::::::::::::::::::

## Filtrar salida

A continuación usaremos el comando `sort` para ordenar el contenido del archivo `lengths.txt`. Pero primero haremos un ejercicio para aprender un poco sobre el comando sort:

::::::::::::::::::::::::::::::::::::::: challenge

## ¿Qué hace `sort -n`?

El fichero `shell-lesson-data/exercise-data/numbers.txt` contiene las siguientes líneas:

```source
10
2
19
22
6
```

Si ejecutamos `sort` en este fichero, la salida es:

```output
10
19
2
22
6
```

Si ejecutamos `sort -n` en el mismo fichero, obtenemos esto en su lugar:

```output
2
6
10
19
22
```

Explica por qué `-n` tiene este efecto.

::::::::::::::: solution

## Solución

La opción `-n` especifica una ordenación numérica en lugar de alfanumérica.



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

También usaremos la opción `-n` para especificar que la ordenación sea numérica en lugar de alfanumérica. Esto *no* cambia el fichero, sino que envía el resultado ordenado a la pantalla:

```bash
$ sort -n lengths.txt
```

```output
  9  methane.pdb
 12  ethane.pdb
 15  propane.pdb
 20  cubane.pdb
 21  pentane.pdb
 30  octane.pdb
107  total
```

Podemos poner la lista ordenada de líneas en otro fichero temporal llamado `sorted-lengths.txt` poniendo `> sorted-lengths.txt` después del comando, igual que usamos `> lengths.txt` para poner la salida de `wc` en `lengths.txt`. Una vez hecho esto, podemos ejecutar otro comando llamado `head` para obtener las primeras líneas en `sorted-lengths.txt`:

```bash
$ sort -n lengths.txt > sorted-lengths.txt
$ head -n 1 sorted-lengths.txt
```

```output
  9  methane.pdb
```

Usar `-n 1` con `head` le dice que sólo queremos la primera línea del fichero; `-n 20` obtendría las 20 primeras, y así sucesivamente. Como `sorted-lengths.txt` contiene las longitudes de nuestros ficheros ordenadas de menor a mayor, la salida de `head` debe ser el fichero con menos líneas.

::::::::::::::::::::::::::::::::::::::::: callout

## Redireccionando al mismo fichero

Es una muy mala idea intentar redirigir la salida de un comando que opera sobre un fichero al mismo fichero. Por ejemplo:

```bash
$ sort -n lengths.txt > lengths.txt
```

Hacer algo como esto puede darte resultados incorrectos y/o borrar el contenido de `lengths.txt`.


::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::: challenge

## ¿Qué significa `>>`?

Hemos visto el uso de `>`, pero existe un operador similar `>>` que funciona de forma ligeramente diferente. Aprenderemos las diferencias entre estos dos operadores imprimiendo algunas cadenas. Podemos utilizar el comando `echo` para imprimir cadenas, por ejemplo

```bash
$ echo The echo command prints text
```

```output
The echo command prints text
```

Ahora prueba los comandos de abajo para revelar la diferencia entre los dos operadores:

```bash
$ echo hello > testfile01.txt
```

y:

```bash
$ echo hello >> testfile02.txt
```

Sugerencia: Intenta ejecutar cada comando dos veces seguidas y luego examina los archivos de salida.

::::::::::::::: solution

## Solución

En el primer ejemplo con `>`, la cadena 'hola' se escribe en `testfile01.txt`, pero el fichero se sobreescribe cada vez que ejecutamos el comando.

Vemos en el segundo ejemplo que el operador `>>` también escribe 'hola' en un fichero (en este caso `testfile02.txt`), pero añade la cadena al fichero si ya existe (es decir, cuando lo ejecutamos por segunda vez).



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::: challenge

## Añadiendo datos

Ya hemos conocido el comando `head`, que imprime líneas desde el principio de un fichero. el comando `tail` es similar, pero imprime líneas desde el final del fichero.

Considera el fichero `shell-lesson-data/exercise-data/animal-counts/animals.csv`. Después de estos comandos, seleccione la respuesta que corresponde al fichero `animals-subset.csv`:

```bash
$ head -n 3 animals.csv > animals-subset.csv
$ tail -n 2 animals.csv >> animals-subset.csv
```

1. Las tres primeras líneas de `animals.csv`
2. Las dos últimas líneas de `animals.csv` son
3. Las tres primeras líneas y las dos últimas líneas de `animals.csv`
4. La segunda y la tercera línea de `animals.csv`

::::::::::::::: solution

## Solución

La opción 3 es correcta. Para que la opción 1 sea correcta sólo ejecutaríamos el comando `head`. Para que la opción 2 sea correcta sólo ejecutaríamos el comando `tail`. Para que la opción 4 sea correcta tendríamos que pasar la salida de `head` a `tail -n 2` haciendo `head -n 3 animals.csv | tail -n 2 > animals-subset.csv`



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Pasando la salida a otro comando

En nuestro ejemplo de encontrar el fichero con menos líneas, estamos usando dos ficheros intermedios `lengths.txt` y `sorted-lengths.txt` para almacenar la salida. Esta es una forma confusa de trabajar porque incluso una vez que entiendes lo que hacen `wc`, `sort`, y `head`, esos ficheros intermedios hacen difícil seguir lo que está pasando. Podemos hacerlo más fácil de entender ejecutando `sort` y `head` juntos:

```bash
$ sort -n lengths.txt | head -n 1
```

```output
  9  methane.pdb
```

La barra vertical, `|`, entre los dos comandos se llama **pipe**. Le dice al shell que queremos usar la salida del comando de la izquierda como entrada para el comando de la derecha.

Esto ha eliminado la necesidad del archivo `sorted-lengths.txt`.

## Combinando múltiples comandos

Nada nos impide encadenar pipes consecutivamente. Podemos, por ejemplo, enviar la salida de `wc` directamente a `sort`, y luego enviar la salida resultante a `head`. Esto elimina la necesidad de ficheros intermedios.

Empezaremos usando una pipe para enviar la salida de `wc` a `sort`:

```bash
$ wc -l *.pdb | sort -n
```

```output
   9 methane.pdb
  12 ethane.pdb
  15 propane.pdb
  20 cubane.pdb
  21 pentane.pdb
  30 octane.pdb
 107 total
```

Podemos entonces enviar esa salida a través de otra pipe, a `head`, de modo que la pipe completa se convierte en:

```bash
$ wc -l *.pdb | sort -n | head -n 1
```

```output
   9  methane.pdb
```

Esto es exactamente como si un matemático anidara funciones como *log(3x)* y dijera 'el logaritmo de tres veces *x*'. En nuestro caso, el algoritmo es 'cabeza de ordenación del recuento de líneas de `*.pdb`'.

La redirección y las pipes utilizadas en los últimos comandos se ilustran a continuación:

![](fig/redirects-and-pipes.svg){alt='Redirecciones y pipes de diferentes comandos: "wc -l \*.pdb" dirigirá la salida al shell. "wc -l \*.pdb > longitudes" dirigirá la salida al archivo "longitudes". "wc -l \*.pdb | sort -n | head -n 1" creará un canal en el que la salida del comando "wc" es la entrada del comando "sort", la salida del comando "sort" es la entrada del comando "head" y la salida del comando "head" se dirige al intérprete de órdenes'}

::::::::::::::::::::::::::::::::::::::: challenge

## Uniendo comandos en pipes

En nuestro directorio actual, queremos encontrar los 3 archivos que tienen el menor número de líneas. ¿Qué comando de los que aparecen a continuación funcionaría?

1. `wc -l * > sort -n > head -n 3`
2. `wc -l * | sort -n | head -n 1-3`
3. `wc -l * | head -n 3 | sort -n`
4. `wc -l * | sort -n | head -n 3`

::::::::::::::: solution

## Solución

La opción 4 es la solución. El carácter `|` se utiliza para conectar la salida de un comando a la entrada de otro. el carácter `>` se utiliza para redirigir la salida estándar a un archivo. ¡Pruébalo en el directorio `shell-lesson-data/exercise-data/alkanes`!



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Herramientas diseñadas para trabajar juntas

Esta idea de enlazar programas es la razón por la que Unix ha tenido tanto éxito. En lugar de crear enormes programas que intentan hacer muchas cosas diferentes, los programadores de Unix se centran en crear un montón de herramientas simples que cada una hace bien un trabajo, y que funcionan bien entre sí. Este modelo de programación se denomina "pipes y filtros". Ya hemos visto las pipes; un **filtro** es un programa como `wc` o `sort` que transforma un flujo de entrada en un flujo de salida. Casi todas las herramientas estándar de Unix pueden trabajar de esta manera. A menos que se les indique lo contrario, leen de la entrada estándar, hacen algo con lo que han leído y escriben en la salida estándar.

La clave es que cualquier programa que lea líneas de texto de la entrada estándar y escriba líneas de texto en la salida estándar puede combinarse con cualquier otro programa que también se comporte de esta manera. Puedes *y debes* escribir tus programas de esta forma para que tú y otras personas podáis poner esos programas en pipes para multiplicar su potencia.

::::::::::::::::::::::::::::::::::::::: challenge

## Comprensión de Lectura de pipes

Un fichero llamado `animals.csv` (en la carpeta `shell-lesson-data/exercise-data/animal-counts`) contiene los siguientes datos:

```source
2012-11-05,deer,5
2012-11-05,rabbit,22
2012-11-05,raccoon,7
2012-11-06,rabbit,19
2012-11-06,deer,2
2012-11-06,fox,4
2012-11-07,rabbit,16
2012-11-07,bear,1
```

¿Qué texto pasa a través de cada una de las pipes y la redirección final en la pipe de abajo? Nota, el comando `sort -r` ordena en orden inverso.

```bash
$ cat animals.csv | head -n 5 | tail -n 3 | sort -r > final.txt
```

Pista: construye la pipe comando a comando para comprobar tu comprensión

::::::::::::::: solution

## Solución

El comando `head` extrae las 5 primeras líneas de `animals.csv`. A continuación, se extraen las 3 últimas líneas de las 5 anteriores mediante el comando `tail`. Con el comando `sort -r` esas 3 líneas se ordenan en orden inverso. Finalmente, la salida se redirige a un fichero: `final.txt`. El contenido de este fichero puede comprobarse ejecutando `cat final.txt`. El fichero debería contener las siguientes líneas

```source
2012-11-06,rabbit,19
2012-11-06,deer,2
2012-11-05,raccoon,7
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::: challenge

## Construcción de pipes

Para el fichero `animals.csv` del ejercicio anterior, considera el siguiente comando:

```bash
$ cut -d , -f 2 animals.csv
```

El comando `cut` se utiliza para eliminar o 'cortar' ciertas secciones de cada línea del fichero, y `cut` espera que las líneas estén separadas en columnas por un carácter <kbd>Tab</kbd>. Un carácter utilizado de esta forma se denomina **delimitador**. En el ejemplo anterior utilizamos la opción `-d` para especificar la coma como carácter delimitador. También hemos utilizado la opción `-f` para especificar que queremos extraer el segundo campo (columna). El resultado es el siguiente

```output
deer
rabbit
raccoon
rabbit
deer
fox
rabbit
bear
```

El comando `uniq` filtra las líneas adyacentes coincidentes en un fichero. ¿Cómo podrías extender este conducto (usando `uniq` y otro comando) para averiguar qué animales contiene el fichero (sin duplicados en sus nombres)?

::::::::::::::: solution

## Solución

```bash
$ cut -d , -f 2 animals.csv | sort | uniq
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::: challenge

## ¿Qué pipe?

El fichero `animals.csv` contiene 8 líneas de datos formateadas de la siguiente manera:

```output
2012-11-05,deer,5
2012-11-05,rabbit,22
2012-11-05,raccoon,7
2012-11-06,rabbit,19
...
```

El comando `uniq` tiene una opción `-c` que proporciona un recuento del número de veces que una línea aparece en su entrada. Suponiendo que tu directorio actual es `shell-lesson-data/exercise-data/animal-counts`, ¿qué comando usarías para producir una tabla que muestre el recuento total de cada tipo de animal en el fichero?

1. `sort animals.csv | uniq -c`
2. `sort -t, -k2,2 animals.csv | uniq -c`
3. `cut -d, -f 2 animals.csv | uniq -c`
4. `cut -d, -f 2 animals.csv | sort | uniq -c`
5. `cut -d, -f 2 animals.csv | sort | uniq -c | wc -l`

::::::::::::::: solution

## Solución

La opción 4. es la respuesta correcta. Si tienes dificultades para entender por qué, intenta ejecutar los comandos, o subsecciones de las pipes (asegúrate de que estás en el directorio `shell-lesson-data/exercise-data/animal-counts`).



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

## Pipe de Nelle: Comprobación de archivos

Nelle ha pasado sus muestras por las máquinas de ensayo y ha creado 17 archivos en el directorio `north-pacific-gyre` descrito anteriormente. Como comprobación rápida, partiendo del directorio `shell-lesson-data`, Nelle teclea:

```bash
$ cd north-pacific-gyre
$ wc -l *.txt
```

La salida son 18 líneas que tienen este aspecto:

```output
300 NENE01729A.txt
300 NENE01729B.txt
300 NENE01736A.txt
300 NENE01751A.txt
300 NENE01751B.txt
300 NENE01812A.txt
... ...
```

Ahora escribe esto:

```bash
$ wc -l *.txt | sort -n | head -n 5
```

```output
 240 NENE02018B.txt
 300 NENE01729A.txt
 300 NENE01729B.txt
 300 NENE01736A.txt
 300 NENE01751A.txt
```

Ups: uno de los ficheros es 60 líneas más corto que los otros. Cuando vuelve y lo comprueba, ve que hizo ese ensayo a las 8:00 de un lunes por la mañana --- probablemente alguien estuvo usando la máquina el fin de semana, y se olvidó de reiniciarla. Antes de volver a ejecutar esa muestra, comprueba si algún archivo tiene demasiados datos:

```bash
$ wc -l *.txt | sort -n | tail -n 5
```

```output
 300 NENE02040B.txt
 300 NENE02040Z.txt
 300 NENE02043A.txt
 300 NENE02043B.txt
5040 total
```

Esos números tienen buena pinta --- pero ¿qué hace esa 'Z' ahí en la antepenúltima línea? Todas sus muestras deberían estar marcadas con 'A' o 'B'; por convención, su laboratorio utiliza la 'Z' para indicar las muestras a las que les falta información. Para encontrar otras iguales, hace esto:

```bash
$ ls *Z.txt
```

```output
NENE01971Z.txt    NENE02040Z.txt
```

Efectivamente, cuando comprueba el registro en su portátil, no hay ninguna profundidad registrada para ninguna de esas muestras. Como es demasiado tarde para obtener la información de otra forma, debe excluir esos dos archivos de su análisis. Podría eliminarlos utilizando `rm`, pero hay algunos análisis que podría hacer más adelante en los que la profundidad no importa, así que en su lugar, tendrá que tener cuidado más adelante para seleccionar los archivos utilizando las expresiones comodín `NENE*A.txt NENE*B.txt`.

::::::::::::::::::::::::::::::::::::::: challenge

## Eliminar archivos innecesarios

Supongamos que desea eliminar los archivos de datos procesados y conservar sólo los archivos sin procesar y el script de procesamiento para ahorrar espacio. Los archivos sin procesar terminan en `.dat` y los archivos procesados terminan en `.txt`. ¿Cuál de las siguientes opciones eliminaría todos los ficheros de datos procesados, y *sólo* los ficheros de datos procesados?

1. `rm ?.txt`
2. `rm *.txt`
3. `rm * .txt`
4. `rm *.*`

::::::::::::::: solution

## Solución

1. Esto eliminaría los archivos `.txt` con nombres de un carácter
2. Esta es la respuesta correcta
3. El shell expandiría `*` para coincidir con todo lo que hay en el directorio actual, por lo que el comando intentaría eliminar todos los ficheros coincidentes y un fichero adicional llamado `.txt`
4. El shell expande `*.*` para que coincida con todos los nombres de fichero que contengan al menos un `.`, incluyendo los ficheros procesados (`.txt`) *y* los ficheros sin procesar (`.dat`)

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::



:::::::::::::::::::::::::::::::::::::::: keypoints

- `wc` cuenta líneas, palabras y caracteres en sus entradas.
- `cat` muestra el contenido de sus entradas.
- `sort` ordena sus entradas.
- `head` muestra por defecto las 10 primeras líneas de su entrada sin argumentos adicionales.
- `tail` muestra por defecto las 10 últimas líneas de su entrada sin argumentos adicionales.
- `command > [file]` redirige la salida de un comando a un archivo (sobreescribiendo cualquier contenido existente).
- `command >> [file]` añade la salida de un comando a un archivo.
- `[first] | [second]` es una pipe: la salida del primer comando se usa como entrada del segundo.
- La mejor manera de usar el shell es usar pipes para combinar programas simples de un solo propósito (filtros).

::::::::::::::::::::::::::::::::::::::::::::::::::



