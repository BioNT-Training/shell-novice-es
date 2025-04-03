---
title: Resumen de comandos básicos
---


## Resumen de comandos básicos

| Action       | Files | Folders      |
| ------------ | ----- | ------------ |
| Inspect      | ls    | ls           |
| View content | cat   | ls           |
| Navigate to  |       | cd           |
| Move         | mv    | mv           |
| Copy         | cp    | cp -r        |
| Create       | nano  | mkdir        |
| Delete       | rm    | rmdir, rm -r |

## Jerarquía del sistema de ficheros

Lo que sigue es una visión general de un sistema de ficheros Unix estándar. La jerarquía exacta depende de la plataforma. Su estructura de archivos/directorios puede diferir ligeramente:

![](fig/standard-filesystem-hierarchy.svg){alt='Jerarquía del sistema de ficheros de Linux'}

## Glosario

[ruta absoluta]{#ruta-absoluta} : Una [ruta](#ruta) que hace referencia a una ubicación concreta en un sistema de archivos. Las rutas absolutas suelen escribirse con respecto al [directorio raíz](#root-directory) del sistema de archivos, y comienzan por "/" (en Unix) o "\\" (en Microsoft Windows). Véase también: [ruta relativa](#relative-path).

[argumento]{#argument} : Valor dado a una función o programa cuando se ejecuta. El término se utiliza a menudo de forma intercambiable (e inconsistente) con [parámetro](#parameter).

[comando shell]{#comando-shell} : Ver [shell](#shell)

[command-line interface]{#interfaz de línea de comandos} : Interfaz de usuario basada en la introducción de comandos, normalmente en un [REPL](#read-evaluate-print-loop). Véase también: [interfaz gráfica de usuario](#graphical-user-interface).

[comment]{#comment} : Un comentario en un programa que pretende ayudar a los lectores humanos a entender lo que está pasando, pero que es ignorado por el ordenador. Los comentarios en Python, R, y el shell de Unix comienzan con un carácter `#` y van hasta el final de la línea; los comentarios en SQL comienzan con `--`, y otros lenguajes tienen otras convenciones.

[directorio de trabajo actual]{#directorio-de-trabajo-actual} : El directorio a partir del cual se calculan las [rutas relativas](#relative-path); equivalentemente, el lugar donde se buscan los ficheros referenciados sólo por su nombre. Cada [proceso](#proceso) tiene un directorio de trabajo actual. Se suele hacer referencia al directorio de trabajo actual utilizando la notación abreviada `.` (pronunciado "punto").

[sistema de archivos]{#file-system} : Conjunto de archivos, directorios y dispositivos de E/S (como teclados y pantallas). Un sistema de ficheros puede estar repartido en muchos dispositivos físicos, o muchos sistemas de ficheros pueden estar almacenados en un único dispositivo físico; el [sistema operativo](#operating-system) gestiona el acceso.

[filename extension]{#filename-extension} : La parte del nombre de un archivo que viene después del carácter final ".". Por convención, identifica el tipo de archivo: `.txt` significa "archivo de texto", `.png` significa "archivo gráfico de red portátil", etcétera. La mayoría de los sistemas operativos no aplican estas convenciones: es perfectamente posible (¡pero confuso!) nombrar un archivo de sonido MP3 `homepage.html`. Dado que muchas aplicaciones utilizan extensiones de nombre de archivo para identificar el [tipo MIME](#tipo-mime) del archivo, nombrar mal los archivos puede hacer que esas aplicaciones fallen.

[filter]{#filter} : Programa que transforma un flujo de datos. Muchas herramientas de línea de comandos de Unix están escritas como filtros: leen datos de la [entrada estándar](#entradaestándar), los procesan y escriben el resultado en la [salida estándar](#salidaestándar).

[for loop]{#for-loop} : Un bucle que se ejecuta una vez por cada valor en algún tipo de conjunto, lista o rango. Véase también: [bucle while](#buclewhile).

[interfaz gráfica de usuario]{#graphical-user-interface} : Interfaz de usuario basada en la selección de elementos y acciones desde una pantalla gráfica, normalmente controlada mediante el uso de un ratón. Véase también: [interfaz de línea de comandos](#command-line-interface).

[home directory]{#home-directory} : El directorio por defecto asociado a una cuenta en un sistema informático. Por convención, todos los archivos de un usuario se almacenan en su directorio home o debajo de él.

[bucle]{#bucle} : Conjunto de instrucciones que se ejecutan varias veces. Consiste en un [cuerpo de bucle](#cuerpo-de-bucle) y (normalmente) una condición para salir del bucle. Véase también [bucle for](#buclefor) y [bucle while](#buclewhile).

[loop body]{#loop-body} : Conjunto de sentencias o comandos que se repiten dentro de un [bucle for](#buclefor) o [bucle while](#buclewhile).

[MIME type]{#mime-type} : Los tipos MIME (Multi-Purpose Internet Mail Extensions) describen diferentes tipos de archivos para su intercambio en Internet, por ejemplo, imágenes, audio y documentos.

[sistema operativo]{#operating-system} : Software que gestiona las interacciones entre usuarios, hardware y software [procesos](#process). Ejemplos comunes son Linux, macOS y Windows.

[option]{#opción} : Una forma de especificar un argumento o ajuste a un programa de línea de comandos. Por convención, las aplicaciones Unix utilizan un guión seguido de una sola letra, como `-v`, o dos guiones seguidos de una palabra, como `--verbose`, mientras que las aplicaciones DOS utilizan una barra, como `/V`. Dependiendo de la aplicación, una opción puede ir seguida de un único argumento, como en `-o /tmp/output.txt`.

[parameter]{#parameter} : Una variable nombrada en la declaración de una función que se utiliza para contener un valor pasado en la llamada. El término se utiliza a menudo indistintamente (e inconsistentemente) con [argumento](#argumento).

[directorio-padre]{#directorio-padre} : El directorio que "contiene" al directorio en cuestión. Cada directorio en un sistema de archivos excepto el [directorio raíz](#directorio-raíz) tiene un padre. Se suele hacer referencia al directorio padre utilizando la notación abreviada `..` (pronunciado "dot dot").

[ruta]{#ruta} : Descripción que especifica la ubicación de un archivo o directorio dentro de un [sistema de archivos](#sistema-de-archivos). Véase también: [ruta absoluta](#ruta-absoluta), [ruta relativa](#ruta-relativa).

[pipe]{#tubería} : Una conexión desde la salida de un programa a la entrada de otro. Cuando dos o más programas están conectados de esta manera, se les llama "pipeline".

[proceso]{#process} : Una instancia en ejecución de un programa, que contiene código, valores de variables, archivos abiertos y conexiones de red, etc. Los procesos son los "actores" que gestiona el [sistema operativo](#operating-system); normalmente ejecuta cada proceso durante unos milisegundos cada vez para dar la impresión de que se están ejecutando simultáneamente.

[prompt]{#prompt} : Carácter o caracteres mostrados por un [REPL](#read-evaluate-print-loop) para mostrar que está esperando su siguiente comando.

[quoting]{#quoting} : (en el shell): Uso de comillas de varios tipos para evitar que el shell interprete caracteres especiales. Por ejemplo, para pasar la cadena `*.txt` a un programa, suele ser necesario escribirla como `'*.txt'` (con comillas simples) para que el shell no intente expandir el comodín `*`.

[bucle de lectura-evaluación-impresión]{#read-evaluate-print-loop} : (REPL): Una [interfaz de línea de comandos](#command-line-interface) que lee un comando del usuario, lo ejecuta, imprime el resultado y espera otro comando.

[redirect]{#redirect} : Para enviar la salida de un comando a un archivo en lugar de a la pantalla o a otro comando, o equivalentemente para leer la entrada de un comando desde un archivo.

[expresión regular]{#regular-expression} : Un patrón que especifica un conjunto de cadenas de caracteres. Las expresiones regulares se suelen utilizar para encontrar secuencias de caracteres en cadenas.

[ruta relativa]{#relative-path} : Una [ruta](#path) que especifica la ubicación de un archivo o directorio con respecto al [directorio de trabajo actual](#current-working-directory). Cualquier ruta que no comience con un carácter separador ("/" o "\\") es una ruta relativa. Véase también: [ruta absoluta](#ruta-absoluta).

[directorio raíz]{#root-directory} : El directorio más alto en un [sistema de archivos](#file-system). Su nombre es "/" en Unix (incluyendo Linux y macOS) y "/" en Microsoft Windows.

[shell]{#shell} : Una [interfaz de línea de comandos](#interfaz de línea de comandos) como Bash (la Bourne-Again Shell) o la shell DOS de Microsoft Windows que permite a un usuario interactuar con el [sistema operativo](#sistema operativo).

[shell script]{#shell-script} : Conjunto de comandos [shell](#shell) almacenados en un archivo para su reutilización. Un script de shell es un programa ejecutado por el shell; el nombre "script" se utiliza por razones históricas.

[standard input]{#standard-input} : El flujo de entrada por defecto de un proceso. En aplicaciones interactivas de línea de comandos, suele estar conectado al teclado; en una [tubería](#pipe), recibe datos de la [salida estándar](#standard-output) del proceso precedente.

[standard output]{#standard-output} : El flujo de salida por defecto de un proceso. En aplicaciones interactivas de línea de comandos, los datos enviados a la salida estándar se muestran en la pantalla; en una [tubería](#pipe), se pasan a la [entrada estándar](#standard-input) del siguiente proceso.

[subdirectorio]{#sub-directorio} : Un directorio contenido dentro de otro directorio.

[tab-completion]{#tab-completion} : Característica de muchos sistemas interactivos por la que, al pulsar la tecla Tab, se completa automáticamente la palabra o comando actual.

[variable]{#variable} : Un nombre en un programa que está asociado con un valor o una colección de valores.

[bucle while]{#buclewhile} : Un bucle que sigue ejecutándose mientras alguna condición sea cierta. Véase también: [bucle for](#buclefor).

[wildcard]{#wildcard} : Carácter utilizado en la concordancia de patrones. En el shell Unix, el comodín `*` coincide con cero o más caracteres, de modo que `*.txt` coincide con todos los archivos cuyos nombres terminan en `.txt`.

## Referencias externas

### Abrir un terminal

- [Cómo usar Terminal en un Mac](https://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/)
- [Git para Windows](https://git-for-windows.github.io/)
- [Cómo instalar la herramienta de línea de comandos Bash shell en Windows 10](https://www.windowscentral.com/how-install-bash-shell-command-line-windows-10)
- [Instalación y uso de Linux Bash Shell en Windows 10](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/)
- [Uso del Bash Shell de Windows 10](https://www.howtogeek.com/265900/everything-you-can-do-with-windows-10s-new-bash-shell/)
- [Usando un emulador UNIX/Linux (Cygwin) o un cliente Secure Shell (SSH) (Putty)](https://faculty.smu.edu/reynolds/unixtut/windows.html)

### Manuales

- [Manuales GNU](https://www.gnu.org/manual/manual.html)
- [Utilidades básicas de GNU](https://www.gnu.org/software/coreutils/manual/coreutils.html)

### Varios

- [Giro del Pacífico Norte](https://en.wikipedia.org/wiki/North_Pacific_Gyre)
- [Gran mancha de basura del Pacífico](https://en.wikipedia.org/wiki/Great_Pacific_Garbage_Patch)
- ['Garantizar la longevidad de la información digital', por Jeff Rothenberg](https://www.clir.org/pubs/archives/ensuring.pdf)
- [Haikus de errores informáticos](https://wiki.c2.com/?ComputerErrorHaiku)
- [Cómo nombrar bien los archivos, por Jenny Bryan](https://speakerdeck.com/jennybc/how-to-name-files)


