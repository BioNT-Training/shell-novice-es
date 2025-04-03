---
title: Discusión
---


## Sopa de letras

Si el comando para saber quiénes somos es `whoami`, el comando para saber dónde estamos debería llamarse `whereami`, ¿por qué es `pwd`? La respuesta habitual es que a principios de los 70, cuando se empezó a desarrollar Unix, cada pulsación de tecla contaba: los dispositivos de la época eran lentos, y el retroceso en un teletipo era tan doloroso que reducir el número de pulsaciones para reducir el número de errores de escritura era en realidad una victoria para la usabilidad. La realidad es que los comandos se añadieron a Unix uno a uno, sin ningún plan maestro, por personas que estaban inmersas en su jerga. El resultado es tan inconsistente como la ortografía roolz uv Inglish, pero ahora estamos atascados con ella.

## Códigos de control de trabajo

El shell acepta algunos comandos especiales que permiten a los usuarios interactuar con procesos o programas en ejecución. Puedes introducir cada uno de estos "códigos de control" manteniendo pulsada la tecla `Ctrl` y pulsando a continuación uno de los caracteres de control. En otros tutoriales, puede que veas el término `Control` o el `^` utilizado para representar la tecla `Ctrl` (por ejemplo, las siguientes son todas equivalentes `Ctrl-C`, `Ctrl+C`, `Control-C`, `Control+C`, `^C`).

- `Ctrl-C`: interrumpe y cancela un programa en ejecución. Esto es útil si quieres cancelar un comando que está tardando demasiado en ejecutarse.

- `Ctrl-D`: indica el final de un archivo o flujo de caracteres que estás introduciendo en la línea de comandos. Por ejemplo, antes vimos que el comando `wc` cuenta líneas, palabras y caracteres en un archivo. Si escribimos `wc` y pulsamos Intro sin dar un nombre de archivo, `wc` asumirá que queremos analizar todo lo que escribamos a continuación. Después de escribir nuestra obra magna directamente en el intérprete de comandos, podemos escribir Ctrl-D para decirle a `wc` que hemos terminado y que nos gustaría ver los resultados del recuento de palabras.

- `Ctrl-Z`: Suspende un proceso pero no lo termina. A continuación, puede utilizar el comando `fg` para reiniciar el trabajo en primer plano.

Para los nuevos usuarios del shell, todos estos códigos de control pueden parecer tener el mismo efecto: hacen que las cosas "desaparezcan" Pero es útil entender las diferencias. En general, si algo ha ido mal y sólo quieres recuperar el prompt de tu shell, es mejor usar `Ctrl-C`.

## Otros Shells

Antes de que Bash se popularizara a finales de los noventa, los científicos usaban ampliamente (y algunos todavía usan) otro shell, C-shell, o Csh. Bash y Csh tienen características similares, pero sus reglas sintácticas son diferentes y esto las hace incompatibles entre sí. Desde entonces han aparecido algunos otros shells, incluyendo ksh, zsh, y algunos otros; en su mayoría son compatibles con Bash, y Bash es el shell por defecto en la mayoría de las implementaciones modernas de Unix (incluyendo la mayoría de los paquetes que proporcionan herramientas similares a Unix para Windows) pero si obtienes errores extraños en scripts de shell escritos por colegas, comprueba para qué shell fueron escritos.

## Configuraciones Bash

¿Quieres personalizar rutas, variables de entorno, alias y otros comportamientos de tu shell? Esta excelente entrada del blog "[Bash Configurations Demystified][bash-demystified]" de Dalton Hubble cubre consejos, trucos y cómo evitar peligros.

[bash-demystified]: https://blog.dghubble.io/posts/.bashprofile-.profile-and-.bashrc-conventions/




