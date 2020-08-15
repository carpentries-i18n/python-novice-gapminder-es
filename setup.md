---
layout: page
title: "Configuración"
permalink: /es/setup/
root: /es/_episodes/
---

## Instalando Python usando Anaconda

[Python][python] es un lenguaje muy popular en la computación científica y también es ideal para
la programación en general. La instalación de todos los paquetes científicos
individualmente puede ser un poco difícil, por lo que recomendamos 
[Anaconda][anaconda], un instalador todo en uno.

Independientemente de como elijas instalarlo, por favor asegúrate que instalas la
versión 3.x de Python (e.g., 3.4 está bien). Además, por favor configura tu entorno de Python
al menos un día antes del taller. Si encuentras problemas con el proceso de
instalación, solicita ayuda a los organizadores del taller por correo electrónico así
estás listo para empezar tan pronto como el taller comience.

### Windows - [Vídeo tutorial][video-windows] (en inglés)

1. Abre [https://www.anaconda.com/distribution/][anaconda-windows] en tu navegador web.

2. Descarga el instalador de Python 3 para Windows.

3. Haz doble-click en el ejecutable e instala Python 3 usando la configuración recomendada. Asegúrate que la opción **Register Anaconda as my default Python 3.x** está marcada - debería de ser así en la última versión de Anaconda.

### Mac OS X - [Vídeo tutorial][video-mac] (en inglés)

1. Abre [https://www.anaconda.com/distribution/][anaconda-mac] en tu navegador web.

2. Descarga el instalador de Python 3 para OS X. Estas instrucciones asumen que estás usando el archivo de instalación gráfico `.pkg`.

3. Sigue las instrucciones de instalación de Python 3. Asegúrate que la ubicación de instalación este configurado como "*Install only for me*" (Instalarlo sólo para mi) así Anaconda instalará sus archivos localmente, relativamente a tu directorio de inicio. Instalar el software para todos los usuarios tiende a dar problemas a largo plazo y debe evitarse.


### Linux

Tenga en cuenta que los pasos a continuación requieren que trabajes usando la terminal.
Si encuentras alguna dificultad, por favor solicite ayuda antes de que comience el taller.

1.  Abre [https://www.anaconda.com/distribution/][anaconda-linux] en tu navegador web.

2.  Descarga el instalador de Python 3 para Linux.

3.  Instala Python 3 usando todos los valores predeterminados para la instalación.

    a.  Abre una terminal.

    b.  Navega a la carpeta donde descargaste el instalador

    c.  Escribe

    ~~~
    $ bash Anaconda3-
    ~~~
    {: .bash}

    y pulsa el tabulador.  El nombre del archivo que acabas de descargar debe aparecer.

    d.  Pulsa enter.

    e.  Sigue los pasos de solo-texto. Cuando aparezca el acuerdo de la licencia (habrá dos puntos
        en la parte inferior de la pantalla) pulsa la barra espaciadora hasta que veas el
        final del texto. Escribe `yes` (sí) y pulsa enter para aceptar la licencia. Pulsa
        enter otra vez para aceptar el lugar predeterminado para los archivos. Escribe `yes` y
        pulsa enter para anteponer Anaconda a tu `PATH` (esto hace que la distribución de
        Anaconda sea el Python predeterminado para tu usuario).

## Obteniendo los datos

Los datos que usaremos están tomados del conjunto de datos [gapminder][gapminder].
Para obtenerlos, descarga y descomprime el archivo
[python-novice-gapminder-data.zip]({{ site.baseurl }}/files/python-novice-gapminder-data.zip).
Para seguir el material presentado, debes iniciar el servidor JupyterLab
en el directorio raíz (consulta [Starting JupyterLab] (iniciando JupyterLab)({{ page.root }}/01-run-quit/#starting-jupyterlab)).


[anaconda]: https://www.anaconda.com/
[anaconda-mac]: https://www.anaconda.com/download/#macos
[anaconda-linux]: https://www.anaconda.com/download/#linux
[anaconda-windows]: https://www.anaconda.com/download/#windows
[gapminder]: https://en.wikipedia.org/wiki/Gapminder_Foundation
[jupyter]: http://jupyter.org/
[python]: https://python.org
[video-mac]: https://www.youtube.com/watch?v=TcSAln46u9U
[video-windows]: https://www.youtube.com/watch?v=xxQ0mzZ8UvA

