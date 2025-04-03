---
title: Configuración
---


## Descargar archivos

Necesitas descargar algunos archivos para seguir esta lección.

1. Descarga [shell-lesson-data.zip][archivo zip] y mueve el archivo a tu Escritorio.
2. Descomprime/extrae el archivo. **Haga saber a su instructor si necesita ayuda con este paso**. Deberías terminar con una nueva carpeta llamada **`shell-lesson-data`** en tu Escritorio.

## Instalar software

Si aún no tiene instalado el software de shell, deberá [descargarlo e instalarlo][install_shell].

## Abrir una nueva shell

Después de instalar el software

3. Abre un terminal. Si no estás seguro de cómo abrir un terminal en tu sistema operativo, consulta las siguientes instrucciones.
4. En el terminal escriba `cd` y pulse la tecla <kbd>Return</kbd>. Este paso asegurará que empieces con tu carpeta de inicio como directorio de trabajo.

En la lección, descubrirás cómo acceder a los archivos de datos de esta carpeta.

::::::::::::::::::::::::::::::::::::::::: callout

## Dónde escribir comandos: Cómo abrir un nuevo shell

El shell es un programa que nos permite enviar comandos al ordenador y recibir salida. También se conoce como terminal o línea de comandos.

Algunos ordenadores incluyen un programa Unix Shell por defecto. Los pasos siguientes describen algunos métodos para identificar y abrir un programa Unix Shell si ya tiene uno instalado. También hay opciones para identificar y descargar un programa Unix Shell, un emulador Linux/UNIX o un programa para acceder a un Unix Shell en un servidor.

Si ninguna de las opciones siguientes se ajusta a sus circunstancias, intente una búsqueda en línea de: Unix shell [tu modelo de ordenador] [tu sistema operativo].


::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::: solution

### Windows {#windows}

Los ordenadores con sistemas operativos Windows no tienen instalado automáticamente un programa Unix Shell. En esta lección, te animamos a utilizar un emulador incluido en [Git para Windows][install_shell], que te da acceso tanto a los comandos del shell Bash como a Git.

Una vez instalado, puede abrir un terminal ejecutando el programa Git Bash desde el menú de inicio de Windows.

**Para usuarios avanzados:**

Como alternativa a Git para Windows puede que desee [Instalar el Subsistema de Windows para Linux][wsl] que da acceso a una herramienta de línea de comandos de shell Bash en Windows 10 y superior.

Tenga en cuenta que los comandos del Subsistema Windows para Linux (WSL) pueden diferir ligeramente de los mostrados en la lección o presentados en el taller.

::::::::::::

:::::::::::: solution

### MacOS {#macos}

Para un ordenador Mac que ejecute macOS Mojave o versiones anteriores, el shell Unix predeterminado es Bash. Para un ordenador Mac que ejecute macOS Catalina o versiones posteriores, el shell Unix predeterminado es Zsh. Su shell predeterminado está disponible a través del programa Terminal dentro de su carpeta Utilidades.

Para abrir Terminal, pruebe una o ambas de las siguientes opciones:

- En Finder, selecciona el menú Ir y, a continuación, Utilidades. Localice Terminal en la carpeta Utilidades y ábrala.
- Utiliza la función de búsqueda de ordenadores 'Spotlight' de Mac. Busca por: `Terminal` y pulse <kbd>Return</kbd>.

Para comprobar si su máquina está configurada para utilizar algo distinto de Bash, escriba `echo $SHELL` en la ventana de su terminal.

Si su máquina está configurada para utilizar algo distinto de Bash, puede ejecutarlo abriendo un terminal y escribiendo `bash`.

[Cómo usar Terminal en un Mac][mac-terminal]

::::::::::::

:::::::::::: solution

### Linux {#linux}

El shell Unix por defecto de los sistemas operativos Linux suele ser Bash. En la mayoría de las versiones de Linux, es accesible ejecutando [Gnome Terminal][gnome-terminal] o [KDE Konsole][kde-konsole] o [xterm], que se pueden encontrar a través del menú de aplicaciones o la barra de búsqueda. Si su máquina está configurada para utilizar algo distinto de Bash, puede ejecutarlo abriendo un terminal y escribiendo `bash`.

::::::::::::

[zip-file]: data/shell-lesson-data.zip
[install_shell]: https://carpentries.github.io/workshop-template/install_instructions/#shell
[wsl]: https://learn.microsoft.com/en-us/windows/wsl/install
[mac-terminal]: https://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/
[gnome-terminal]: https://help.gnome.org/users/gnome-terminal/stable/
[kde-konsole]: https://konsole.kde.org/
[xterm]: https://en.wikipedia.org/wiki/Xterm




