---
title: Notas del instructor
---


- ¿Por qué aprendemos a usar el shell?
  - Permite a los usuarios automatizar tareas repetitivas
  - Y capture pequeños pasos de manipulación de datos que normalmente no se registran
    para que la investigación sea reproducible
- El problema
  - Ejecutar el mismo flujo de trabajo en varias muestras puede ser innecesariamente
    laborioso
  - Manipulación manual de ficheros de datos:
    - a menudo no se recoge en la documentación
    - es difícil de reproducir
    - es difícil de solucionar, revisar o mejorar
- El Shell
  - Los flujos de trabajo pueden automatizarse mediante el uso de scripts de shell
  - Los comandos incorporados permiten manipular fácilmente los datos (por ejemplo,
    ordenar, grep, etc.)
  - Cada paso puede ser capturado en la secuencia de comandos de shell y permitir la
    reproducibilidad y fácil solución de problemas

## Total

Mucha gente se ha preguntado si deberíamos seguir enseñando el shell. Después de todo,
cualquiera que quiera renombrar varios miles de archivos de datos puede hacerlo
fácilmente de forma interactiva en el intérprete de Python, y cualquiera que esté
haciendo un análisis de datos serio probablemente va a hacer la mayor parte de su
trabajo dentro de IPython Notebook o R Studio. Entonces, ¿por qué enseñar el shell?

La primera respuesta es: "Porque muchas otras cosas dependen de ello" La instalación de
software, la configuración del editor predeterminado y el control de máquinas remotas
suelen presuponer una familiaridad básica con el intérprete de órdenes y con conceptos
relacionados como la entrada y salida estándar. Muchas herramientas también utilizan su
terminología (por ejemplo, los comandos mágicos `%ls` y `%cd` en IPython).

La segunda respuesta es: "Porque es una manera fácil de introducir algunas ideas
fundamentales sobre cómo usar los ordenadores" Cuando enseñamos a la gente a utilizar el
shell de Unix, les enseñamos que deben hacer que el ordenador repita las cosas (mediante
el tabulador, `!` seguido de un número de comando y bucles `for`) en lugar de repetirlas
ellos mismos. También les enseñamos a tomar las cosas que han descubierto que hacen con
frecuencia y guardarlas para su posterior reutilización (a través de shell scripts), a
dar nombres sensatos a las cosas, y a escribir un poco de documentación (como
comentarios en la parte superior de los shell scripts) para hacer la vida de sus futuros
yos mejor.

La tercera respuesta es: "Porque permite utilizar muchas herramientas y recursos
informáticos específicos del campo a los que los investigadores no pueden acceder de
otro modo" Familiarizarse con el shell es muy útil para acceder remotamente a las
máquinas, utilizar la infraestructura informática de alto rendimiento y ejecutar nuevas
herramientas especializadas en muchas disciplinas. Aquí no enseñamos HPC o habilidades
específicas de dominio, sino que sentamos las bases para el desarrollo posterior de
estas habilidades. En particular, la comprensión de la sintaxis de los comandos, las
banderas y los sistemas de ayuda es útil para las herramientas específicas de dominio y
la comprensión del sistema de archivos (y cómo navegar por él) es útil para el acceso
remoto.

Por último, y quizás lo más importante, enseñar a la gente el shell nos permite
enseñarles a pensar en la programación en términos de composición de funciones. En el
caso de la shell, esto toma la forma de tuberías en lugar de llamadas a funciones
anidadas, pero la idea central de "piezas pequeñas, unidas sin apretar" es la misma.

Todo este material se puede cubrir en tres horas siempre que los alumnos que utilicen
Windows no se encuentren con obstáculos como:

- no ser capaz de averiguar dónde está su directorio de inicio (sobre todo si están
  usando Cygwin);
- no poder ejecutar un editor de texto plano; y
- el shell que rechaza ejecutar scripts que incluyen terminaciones de línea DOS.

## Preparándose para enseñar

- Utilice el directorio `data` para los ejercicios del taller y los ejemplos de
  codificación en vivo. Puede clonar el directorio shell-novice o utilizar el botón
  *Descargar ZIP* de la derecha para obtener el [repositorio Git] completo
  (https://github.com/swcarpentry/shell-novice). Ahora también proporcionamos un archivo
  zip del directorio `data` en la [Página de configuración](../learners/setup.md).

- Sitio web: se han utilizado diversas prácticas.

  - Opción 1: Puede dar enlaces a los alumnos antes de la lección para que puedan
    seguirla, ponerse al día y ver ejercicios (sobre todo si sigue el contenido de la
    lección sin muchos cambios).
  - Opción 2: No muestre el sitio web a los alumnos durante la clase, ya que puede
    distraerles: los alumnos pueden leer en lugar de escuchar, y tener otra ventana
    abierta supone una carga cognitiva adicional.
  - En cualquier caso, asegúrese de señalar el sitio web como referencia posterior al
    taller.

- Contenido: A menos que disponga de un tiempo realmente generoso (más de 4 horas), es
  probable que no cubra TODO el material de esta lección en una sola sesión de medio
  día. Planifique con antelación lo que podría saltarse, lo que realmente desea
  enfatizar, etc.

- Ejercicios: Piense de antemano cómo va a gestionar los ejercicios durante la clase.
  ¿Cómo los va a asignar (página web, diapositiva, folleto)? ¿Quiere que todo el mundo
  lo intente y luego usted muestre la solución? ¿Que un alumno muestre la solución? ¿Que
  los grupos hagan cada uno un ejercicio diferente y presenten sus soluciones?

- La [Página de referencia](../learners/reference.md) puede imprimirse y entregarse a
  los alumnos como referencia, a su elección.

- Otros preparativos: Siéntase libre de añadir sus propios ejemplos o comentarios al
  margen, pero sepa que no debería ser necesario: los temas y comandos pueden enseñarse
  tal y como se dan en las páginas de las lecciones. Si crees que hay un lugar donde la
  lección es deficiente, no dudes en presentar un problema o enviar una solicitud.

## Notas didácticas

- ¡Un recurso en línea genial! [http://explainshell.com/](https://explainshell.com/)
  diseccionará cualquier comando shell que escribas y mostrará texto de ayuda para cada
  pieza. Otra buena herramienta manual podría ser [http://tldr.sh/](https://tldr.sh/)
  con manuales cortos y muy descriptivos para comandos shell, útil especialmente en
  Windows mientras se usa Git BASH donde `man` no puede funcionar.

- Otro recurso en línea superguay es
  [http://www.shellcheck.net](https://www.shellcheck.net), que comprobará los scripts de
  shell (tanto los cargados como los introducidos) en busca de errores comunes.

- Recursos para "dividir" tu shell de modo que los comandos recientes permanezcan a la
  vista:
  [https://github.com/rgaiacs/swc-shell-split-window](https://github.com/rgaiacs/swc-shell-split-window).

- Completar tabulaciones parece poca cosa: no lo es. Reejecutar viejos comandos usando
  `!123` o `!wc` tampoco es poca cosa, y tampoco lo son la expansión de comodines y los
  bucles `for`. Cada uno de ellos es una oportunidad para repetir una de las grandes
  ideas de la Carpintería del Software: si el ordenador *puede* repetirlo, es casi
  seguro que algún programador en algún lugar habrá construido alguna forma para que el
  ordenador *pueda* repetirlo.

- Construir una cadena con cuatro o cinco etapas, ponerla en un script de shell para
  reutilizarla y llamar a ese script dentro de un bucle `for`, es una gran oportunidad
  para mostrar cómo "siete más o menos dos" se conecta a la programación. Una vez que
  hemos descubierto cómo hacer algo medianamente complicado, lo hacemos reutilizable y
  le damos un nombre para que sólo ocupe un espacio en la memoria de trabajo en lugar de
  varios. También es una buena oportunidad para hablar de programación exploratoria: en
  lugar de diseñar un programa de antemano, podemos hacer algunas cosas útiles y luego
  decidir retroactivamente cuáles merece la pena encapsular para reutilizarlas en el
  futuro.

- Si todo va bien, puede hacer hincapié en que las extensiones de archivo están ahí
  esencialmente para ayudar a los ordenadores (y a los lectores humanos) a entender el
  contenido de los archivos y no son un requisito de los archivos (tratado brevemente en
  [Navegación por archivos y directorios](../episodios/02-filedir.md)). Esto se puede
  hacer en la sección [Pipes and Filters](../episodes/04-pipefilter.md) mostrando que se
  puede redirigir la salida estándar a un fichero sin la extensión .txt (por ejemplo,
  lengths), y que el fichero resultante sigue siendo un fichero de texto perfectamente
  utilizable. Señale que si hace doble clic en la GUI, el ordenador probablemente le
  preguntará qué quiere hacer.

- Tenemos que omitir muchas cosas importantes debido a las limitaciones de tiempo,
  incluyendo permisos de archivos, control de trabajos y SSH. Si los alumnos ya
  entienden el material básico, esto se puede cubrir en su lugar utilizando las
  lecciones en línea como guía. Estas limitaciones también tienen consecuencias
  posteriores:

- Es difícil hablar de `#!` (shebang) sin hablar primero de permisos, cosa que no
  hacemos.`#!` también es [bastante complicado][shebang], así que aunque habláramos de
  permisos, probablemente no querríamos hablar de `#!`.

- La instalación de Bash y de un conjunto razonable de comandos Unix en Windows siempre
  conlleva algunos problemas y frustraciones. Consulte el último conjunto de directrices
  de instalación para obtener consejos y pruébelo usted mismo *antes* de impartir una
  clase.

- Por defecto, puede que tengas una larga cadena de información adjunta a tu símbolo del
  sistema en Git Bash. Para reducir el "ruido" y proceder con un prompt más ordenado,
  introduce el comando:

  ```bash
  PS1='$ '
  ```

- En máquinas Windows si `nano` no ha sido correctamente instalado con el [Software Carpentry Windows Installer][windows-installer]
  es posible usar `notepad` como alternativa. Habrá una interfaz GUI y los
  finales de línea se tratarán de forma diferente, pero por lo demás, para los
  propósitos de esta lección, `notepad` y `nano` pueden usarse casi
  indistintamente.

- En Windows, parece que:

  ```bash
  $ cd
  $ cd Desktop
  ```

  siempre pondrá a alguien en su escritorio (a menos que su máquina esté respaldada
  usando OneDrive de la empresa, ver siguiente punto). Haga que creen allí el directorio
  de ejemplo para los ejercicios de shell, de modo que puedan encontrarlo fácilmente y
  ver cómo evoluciona.

- Si una máquina Windows está respaldada con OneDrive empresarial, su escritorio GUI
  puede ser renderizado desde una carpeta dentro de OneDrive, que no coincidirá con el
  contenido de `~/Desktop`. El escritorio de OneDrive debería ser accesible usando uno
  de los siguientes comandos (si el nombre de la empresa no está claro, busque en la
  salida de `ls` para encontrar la carpeta correcta):

  ```bash
  $ cd "~/OneDrive - Name Of Enterprise/Desktop"
  $ cd "C:/Users/Username/OneDrive - Name Of Enterprise/Desktop"
  ```

  Una forma de detectar si el ordenador utiliza este tipo de configuración es mirar los
  archivos, carpetas o enlaces del escritorio. Normalmente, el icono contiene un símbolo
  de acceso directo/flecha si se trata de un enlace, o simplemente el icono si el
  archivo está guardado en la carpeta `Desktop`. Los archivos sincronizados con OneDrive
  contienen un símbolo adicional que indica el estado de la sincronización (normalmente
  flechas azules para "sincronización pendiente" o una marca verde para "sincronizado").

- Manténgase dentro de los comandos compatibles con POSIX, como hacen todos los
  materiales de enseñanza. Tu shell particular puede tener extensiones más allá de POSIX
  que no están disponibles en otras máquinas, especialmente los emuladores bash por
  defecto de macOS y bash de Windows. Por ejemplo, POSIX `ls` no tiene una opción
  `--ignore=` o `-I`, y POSIX `head` toma `-n 10` o `-10`, pero no la forma larga de
  `--lines=10`.

## Windows

Instalar Bash y un conjunto razonable de comandos Unix en Windows siempre conlleva
algunos problemas y frustraciones. Por favor, consulte el último conjunto de directrices
de instalación para obtener consejos, y pruébelo usted mismo *antes* de dar una clase.
Las opciones que hemos explorado incluyen:

1. [msysGit](https://msysgit.github.io/) (también llamado "Git Bash"),
2. [Cygwin](https://www.cygwin.com/),
3. utilizando una máquina virtual de escritorio, y
4. hacer que los alumnos se conecten a una máquina Unix remota (normalmente una VM en la
   nube).

Cygwin era la opción preferida hasta mediados de 2013, pero una vez que empezamos a
enseñar Git, msysGit demostró funcionar mejor. Las máquinas virtuales de escritorio y
las VM basadas en la nube funcionan bien para los alumnos técnicamente sofisticados, y
pueden reducir la instalación y la configuración al inicio del taller, pero:

1. no funcionan bien en máquinas poco potentes,
2. son confusas para los novatos (porque cosas tan simples como copiar y pegar funcionan
   de forma diferente),
3. los alumnos abandonan el taller sin un entorno de trabajo en el sistema operativo de
   su elección, y
4. es posible que los alumnos se presenten sin haber descargado la máquina virtual o que
   la red inalámbrica se caiga (o se congestione) durante la clase.

Utilices lo que utilices, por favor *pruébalo tú mismo* en una máquina Windows *antes*
de tu taller: las cosas siempre pueden haber cambiado a tus espaldas desde tu último
taller. Y, por favor, utilice también nuestro [Software Carpentry Windows Installer][windows-installer].

[shebang]: https://www.in-ulm.de/~mascheck/various/shebang/
[windows-installer]: https://github.com/swcarpentry/windows-installer




