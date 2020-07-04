---
title: "Ejecutar y salir"
teaching: 15
exercises: 0
questions:
- "¿Cómo puedo ejecutar programas de Python?"
objectives:
- " Iniciar el servidor JupyterLab." 
- "Crear un nuevo script de Python." 
- "Crear una Libreta Jupyter."
- " Apagar el servidor JupyterLab.."
- "Entender la diferencia entre un script de Python y una Libreta de Jupyter."
- "Crear celdas Markdown en una Libreta."
- "Crear y ejecutar celdas Python en una Libreta."
keypoints:
- "Los scripts de Python son archivos de texto plano."
- "Usa una Libreta Jypiter para editar y correr Python."
- "La Libreta tiene modos de Comandos y Edición."
- "Usa el teclado y el ratón para seleccionar y editar  celdas."
- "La Libreta convertirá Markdown en texto con formato."
- "Markdown hace la mayor parte de lo que hace HTML."
---

## Comenzando con JupyterLab

Mientras que muchos desarrolladores de software a menudo utilizan un entorno de desarrollo integrado (IDE) o un
editor de texto para crear y editar sus programas Python, usaremos [JupyterLab] [jupyterlab]
durante esta lección.

JupyterLab es una aplicación con una interfaz de usuario basada en web desde [Project Jupyter] [jupyter] que
permite trabajar con documentos y actividades como cuadernos Jupyter, editores de texto, terminales,
e incluso componentes personalizados de manera flexible, integrada y extensible. JupyterLab requiere un
navegador razonablemente actualizado (idealmente una versión actual de Chrome, Safari o Firefox); Internet
 Explorer 9 y anteriores *no* son soportados.

 JupyterLab se incluye como parte de la distribución de Python Anaconda. Si  aún no tienes
instalada la distribución de Python de Anaconda, consulta [las instrucciones de configuración] ({{ page.root }}/setup/)
para las instrucciones de instalación.

Aunque JupyterLab es una aplicación basada en web, JupyterLab se ejecuta localmente en tu máquina y 
no requiere una conexión a internet.
*   El servidor JupyterLab envía mensajes a su navegador web.
*   El servidor JupyterLab hace el trabajo y el navegador web muestra el resultado.
*   Escribirás el código en el navegador y verás el resultado cuando la página web hable con el 
    servidor JupyterLab.

> ## ¿JupyterLab? ¿Qué pasa con las Libretas de Jupyter?
> 
 > JupyterLab es la [siguiente nivel en la evolución de Jupyter Notebook] (https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html#overview). Si tienes 
> experiencia trabajando con cuadernos de Jupyter, entonces tendrás una buena idea de qué esperar
> de JupyterLab. 
> 
> Usuarios experimentados con cuadernos de Jupyter interesados ​​en una discusión más detallada de las similitudes y diferencias
> entre las interfaces de usuario de JupyterLab y cuadernos de Jupyter puede encontrar más información en la
> [documentación de la interfaz de usuario de JupyterLab][jupyterlab-ui].
{: .callout}

## Iniciando con JupyterLab

### Mac OS X
Para iniciar el servidor JupyterLab, deberás acceder a la línea de comandos a través de la Terminal.
Hay dos formas de abrir Terminal en Mac.

1. En tu carpeta de Aplicaciones, abre Utilidades y haz doble clic en Terminal
2. Presiona <kbd>Command</kbd> + <kbd>barra espaciadora</kbd> para lanzar Spotlight. Digita `Terminal` y entonces
haz doble clic en el resultado de la búsqueda o presiona <kbd>Enter</kbd>

 Después de iniciar Terminal, escriba el comando para iniciar el servidor JupyterLab.

~~~
$ jupyter lab
~~~
{: .bash}

### Usuarios Windows
 Para iniciar el servidor JupyterLab, necesitará acceder al Prompt de Anaconda.

Presiona <kbd>la Tecla del logotipo de Windows</kbd> y busca  `Anaconda Prompt`, haz clic en el resultado o presione enter.

Después de haber accedido al Prompt de Anaconda, escribe el comando:

~~~
$ jupyter lab
~~~
{: .bash}

A continuación se muestra una captura de pantalla de JupyterLab similar a la que debería abrir en tu
navegador web predeterminado después de iniciar el servidor JupyterLab en Mac OS X o Windows.

<p align='center'>
  <img alt="JupyterLab landing page" src="../fig/0_jupyterlab_landing_page.png" width="750"/>
</p>

## La Interfaz de JupyterLab

JupyterLab tiene muchas características que se encuentran en los entornos de desarrollo integrado (IDE) tradicionales pero
se centra en proporcionar bloques de construcción flexibles para computación interactiva y exploratoria.

 La [Interfaz JupyterLab] (https://jupyterlab.readthedocs.io/en/stable/user/interface.html)
consiste en la barra de menú, una barra lateral izquierda plegable y el área de trabajo principal que contiene pestañas
de documentos y actividades.

### Barra de Menu

 La Barra de Menú en la parte superior de JupyterLab tiene menus de nivel superior que exponen varias acciones
disponibles en JupyterLab junto con sus atajos de teclado (cuando aplica). Los siguientes
menús están incluidos por defecto.

*   **File:** Acciones relacionadas con archivos y directorios tales como:  *New*, *Open*, *Close*, *Save*, etc. El menú *File* también incluye la acción *Quit* usada para apagar el servidor JupyterLab.
*   **Edit:** Acciones relacionadas con edición de documentos y otras actividades como  *Undo*, *Cut*, *Copy*, *Paste*, etc.
*   **View:** Acciones que alteran la apariencia de JupyterLab.
*   **Run:** Acciones para ejecutar código en diferentes actividades tales como cuadernos y consolas de código (discutidas abajo).
*   **Kernel:** Acciones para manejo de núcleos los cuales, como mencionamos arriba, son procesos separados para ejecutar código.
*   **Tabs:** Una lista de los documentos y actividades abiertos en el área de trabajo.
*   **Settings:** Las configuraciones comunes de JupyterLab se pueden configurar usando este menú. También hay una opción  *Advanced Settings Editor*  en el menú desplegable que proporciona un control más detallado de la configuración de JupyterLab y las opciones de configuración.
*   **Help:** Una lista de enlaces de ayuda de JupyterLab y del kernel.

A continuación se muestra una captura de pantalla de la barra de menús predeterminada.

<p align='center'>
    <img alt="JupyterLab Menu Bar" src="../fig/0_jupyterlab_menu_bar.png" width="750"/>
</p>

### Barra lateral izquierda
 

La barra lateral izquierda contiene varias pestañas de uso común, como un explorador de archivos (que muestra
contenido del directorio en el que se lanzó el servidor JupyterLab), una lista de núcleos en ejecución
y terminales, la paleta de comandos y una lista de pestañas abiertas en el área de trabajo principal. Una pantalla de
la barra lateral izquierda predeterminada se muestra a continuación.

<p align='center'>
    <img alt="JupyterLab Left Side Bar" src="../fig/0_jupyterlab_left_side_bar.png" width="250"/>
</p>

La barra lateral izquierda se puede contraer o expandir seleccionando "Show Left Sidebar" en el menú View o
haciendo clic en la pestaña de la barra lateral activa.

### Área principal de Trabajo

El área de trabajo principal en JupyterLab lt permite organizar documentos (cuadernos, archivos de texto, etc.)
y otras actividades (terminales, consolas de códigos, etc.) en paneles de pestañas que pueden redimensionarse o
subdividirse. A continuación se muestra una captura de pantalla de la barra de menús predeterminada.

<p align='center'>
    <img alt="JupyterLab Main Work Area" src="../fig/0_jupyterlab_main_work_area.png" width="750"/>
</p>

Arrastra una pestaña al centro de un panel de pestañas para mover la pestaña al panel. Subdivide un panel de pestañas
arrastrando una pestaña a la izquierda, derecha, arriba o abajo del panel. El área de trabajo tiene una sola
actividad actual. La pestaña de la actividad actual está marcada con un borde superior de color (azul por defecto).

## Creando un script  Python

*   Para comenzar a escribir un nuevo programa de Python, haz clic en el icono Text File bajo el encabezado *Other* en la pestaña Iniciador del Área de trabajo principal.
También puede crear un nuevo archivo de texto sin formato seleccionando *New -> Text File* en el menú *File* en la barra de menú.
* Para convertir este archivo de texto sin formato a un programa de Python, seleccione la opción *Save File As* del menú *File* en la barra de menú y asigna a tu nuevo archivo de texto un nombre que termine con la extensión `.py`.
    *   La extensión `.py` les permite a todos (incluido el sistema operativo) saber que este archivo de texto es un programa de Python.
    *   Esta es una convención, no un requisito.

## Creando una cuaderno de Jupyter 

Para abrir una Libreta nueva, haga clic en el icono de Python 3 debajo del encabezado *Notebook* en la pestaña Launcher en
el área principal de trabajo. También puede crear una Libreta nueva seleccionando *New -> Notebook* desde el menú *File* en la Barra de menú.

Notas adicionales sobre los cuadernos de Jupyter.

  *   Los cuadernos de Jupyter tienen la extensión `.ipynb` para distinguirlos de los programas Python de texto plano.
  *   Los cuadernos pueden ser exportadas como scripts de Python que pueden ser ejecutados desde la línea de comandos.

A continuación se muestra una captura de pantalla de un cuaderno de Jupyter que se ejecuta dentro de JupyterLab. Si estás interesado en
más detalles, mira la [documentación oficial sobre los cuadernos] [jupyterlab-notebook-docs].

<p align='center'>
    <img alt="Example Jupyter Notebook" src="../fig/0_jupyterlab_notebook_screenshot.png" width="750"/>
</p>

> ## Cómo se almacenan
>
> *   Los cuadernos son almacenados en un formato llamado JSON.
> *   Justo como una página web, lo que se guarda se ve diferente a lo que se ve en el navegador. 
> *   Pero este formato permite a Jupyter mezclar código fuente, texto e imágenes, todo en un sólo archivo.
{: .callout}

> ## Organizando documentos en paneles de pestañas
>
>  En el Área de trabajo principal de JupyterLab puedes organizar documentos en paneles de pestañas. Aquí hay un
> ejemplo de la  [documentación oficial][jupyterlab].
> 
> <p align='center'>
>    <img alt="Multi-panel JupyterLab" src="../fig/0_multipanel_jupyterlab_screenshot.png" width="750"/>
> </p>
>
> Primero, crea un archivo de texto, una consola de Python y una ventana de terminal y luego organízalas en tres
>  paneles en el área de trabajo principal. A continuación, crea una libreta, una ventana de terminal y un archivo de texto y 
> luego, organízalas en tres paneles en el área de trabajo principal. Finalmente, crea tu propia combinación de 
> paneles y pestañas. ¿Qué combinación de paneles y pestañas crees que será más útil para tu
 
> flujo de trabajo?
>
> > ## Solución
> >
> > Después de crear las pestañas necesarias, puedes arrastrar una de las pestañas al centro de un panel para 
> > mover la pestaña al panel; a continuación, puedes subdividir un panel de pestañas arrastrando una pestaña hacia la izquierda, 
> > derecha, arriba o bajo del panel.
> {: .solution}
{: .challenge}

## Usar la Libreta Jupyter para editar y ejecutar Python.

*   Si bien es común escribir scripts de Python usando un editor de texto, vamos a usar la [Jupyter Notebook] [jupyter] para el resto de este taller.
* Esto tiene varias ventajas:
    *   Puedes escribir, editar y copiar y pegar fácilmente bloques de código.
    *   Autocompletar (con el tabulador) permite acceder fácilmente a los nombres de las cosas que estás utilizando
        y aprender más sobre ellos
    *   Esto te permite anotar tu código con enlaces, texto de diferentes tamaños, viñetas, etc.
 para que sea más accesible para ti y tus colaboradores.
    *   Esto te permite mostrar figuras al lado del código que las produce
para contar una historia completa del análisis.
*   Cada cuaderno contiene una o más celdas que contienen código, texto o imágenes.

> ## Código vs. Texto
>
> Jupyter mezcla código y texto en diferentes tipos de bloques, llamados celdas. A menudo usamos el término
> "código" que significa "el código fuente del software escrito en un lenguaje como Python".
> Una "celda de código" en una cuaderno es una celda que contiene software;
> una "celda de texto" es una que contiene a prosa ordinaria escrita para seres humanos.
{: .callout}

## Los cuadernos tienen modos Comandos y Edición.

*   Si presionas <kbd>Esc</kbd> y <kbd>Return</kbd> alternadamente, el borde exterior de tu celda de código cambiará de gris a azul.
*   Estos son los modos **Comando** (gris) y **Edición** (azul) de tu cuaderno.
*   El modo de comando te permite editar características a nivel de tu cuaderno, y el modo Editar cambia el contenido de las celdas.
*   Cuando está en modo Comando (esc / gris),
    *   La tecla <kbd>b</kbd>  creará una nueva celda debajo de la celda seleccionada actualmente.
    *   La tecla <kbd>a</kbd> creará una arriba.
    *   La tecla <kbd>x</kbd> borrará la actual celda.
    *   La tecla <kbd>z</kbd> deshará su última operación de celda (que podría ser una eliminación, creación, etc.).
*   Todas las acciones se pueden hacer usando los menús, pero hay muchos atajos de teclado para acelerar las cosas.

> ## Comando Vs. Editar
>
> En la página deJupyter Notebook, ¿estás actualmente en modo de comando o edición?  
> Intercambia entre modos. 
> Usa los atajos para generar una nueva celda. 
> Usa los atajos para borrar una celda
> Usa los atajos para deshacer la última operación de celda que realizaste.
>
> > ## Solución
> >
> > El modo de comando tiene un borde gris y el modo de edición tiene un borde azul. 
> > Usa <kbd>Esc</kbd> y <kbd>Return</kbd> para intercambiar modos
> > Necesitas estar en modo comando (Presiona <kbd>Esc</kbd> si tu celda esta en azul).  Teclea <kbd>b</kbd> o <kbd>a</kbd>.
> > Necesitas estar en modo comando (Presiona <kbd>Esc</kbd> si tu celda es azul).  Digita <kbd>x</kbd>.
> > Necesitas estar en modo comando (Presiona <kbd>Esc</kbd>si tu celda es azul).  Digita <kbd>z</kbd>.
> {: .solution}
{: .challenge}

### Use el teclado y el mouse para seleccionar y editar celdas.

*   Presiona la tecla <kbd>Return</kbd>  convierte el borde en azul y activa el modo Edición, que te permite
    escribir dentro de la celda.
*   Debido a que queremos poder escribir muchas líneas de código en una sola celda,
    presiona la tecla <kbd>Return</kbd>  cuando está en modo Edición (azul) mueve el cursor a la siguiente línea 
    en la celda al igual que en un editor de texto.
*   Necesitamos otra forma de decirle al cuaderno que queremos ejecutar lo que hay en la celda.
*   Presiona <kbd>Shift</kbd>+<kbd>Return</kbd> juntos para ejecutar el contenido de la celda.
*   Ten en cuenta que <kbd>Return</kbd> y <kbd>Shift</kbd>  a la derecha del teclado están
una al lado de la otra.

### La Libreta convertirá Markdown en documentación con formato.

*   Los cuadernos  también pueden mostrar [Markdown][markdown].
    *   Un formato de texto plano simple para escribir listas, enlaces,
         y otras cosas que pueden ir en una página web.
    *   De manera equivalente, un subconjunto de HTML que se parece a lo que enviarías en un correo electrónico antiguo.
*   Convierte la celda actual en una celda Markdown ingresando el modo Comando (<kbd>Esc</kbd>/gray) 
    y presione la tecla <kbd>M</kbd>.
*   `In [ ]:` desaparecerá para mostrar que ya no es una celda de código y podrá escribir
 Markdown..
*   Convierte la celda actual en una celda de Código ingresando el modo Comando (<kbd>Esc</kbd>/gray) y 
    presione <kbd>y la tecla y</kbd>.

### Markdown hace la mayor parte de lo que hace HTML.

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
*   Usa asteriscos
*   para crear
*   listas de viñetas.
~~~
  </div>
  <div class="col-md-6" markdown="1">
*   Usa asteriscos
*   para crear
*   listas de viñetas.
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
1.  Usa números
1.  para crear
1.  listas numeradas.
~~~
  </div>
  <div class="col-md-6" markdown="1">
1.  Usa números
1. para crear
1.  listas numeradas.
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
*   Puedes usar sangrías
\t*  Para crear sublistas 
\t*  del mismo tipo
*  O sublistas
\t1. de diferentes
\t1. tipos
~~~
  </div>
  <div class="col-md-6" markdown="1">
*  Puedes usar sangrías
\t* Para crear sublistas 
\t* del mismo tipo
* O sublistas
\t1. de diferentes
\t1. tipos
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
# Un título de nivel-1
~~~
  </div>
  <div class="col-md-6" markdown="1">
# Un título de nivel-1
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
## Un título de nivel-2 (etc.)
~~~
  </div>
  <div class="col-md-6" markdown="1">
## Un título de nivel-2 (etc.)
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
Los saltos de línea
no importan.

Pero líneas en blanco
crean nuevos párrafos.
~~~
  </div>
  <div class="col-md-6" markdown="1">
Los saltos de línea
no importan.

Pero líneas en blanco
crean nuevos párrafos.
  </div>
</div>

<div class="row">
  <div class="col-md-6" markdown="1">
~~~
[Crea enlaces](http://software-carpentry.org) con `[...](...)`.
O usa el [nombre del enlace][data_carpentry].

[data_carpentry]: http://datacarpentry.org
~~~
  </div>
  <div class="col-md-6" markdown="1">
[Crea enlaces](http://software-carpentry.org) con `[...](...)`.
O usa el [nombre del enlace][data_carpentry].

[data_carpentry]: http://datacarpentry.org
  </div>
</div>

> ## Creando listas en Markdown
>
> Crea una lista anidada en una celda Markdown en un cuaderno que tenga este aspecto:
>
> 1.  Obtener fondos
> 2. Hacer el trabajo.
>     *   Diseñar experimento.
>     *   Recolectar datos.
>     *   Analizar.
> 3.  Escribir.
> 4.  Publicar.
> 
> > ## Solución
> >
> > Este desafío integra tanto la lista numerada como la lista de viñetas. 
> > Tenga en cuenta que la lista de viñetas tiene sangría de 2 espacios para que esté en línea con los elementos de la lista numerada.
> > ~~~
> > 1.  Obtener fondos.
> > 2.  Hacer el trabajo.
> >     *   Diseñar experimento.
> >     *   Recolectar datos.
> >     *   Analizar.
> > 3.  Escribir.
> > 4.  Publicar.
> > ~~~
> {: .solution}
{: .challenge}

> ## Más matemáticas
>
>  ¿Qué se muestra cuando se ejecuta una celda de Python en un cuaderno
> 1ue contiene varios cálculos?
> Por ejemplo, ¿qué sucede cuando esta celda es ejecutada?

>
> ~~~
> 7 * 3
> 2 + 1
> ~~~
> {: .language-python}
> 
> > ## Solución
> >
> > Python devuelve la salida del último cálculo.
> > ~~~
> > 3
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Cambiar una celda existente de código a Markdown
>
> ¿Qué sucede si escribes algo de Python en una celda de código
> y luego lo cambias a una celda Markdown?
> Por ejemplo,
> pon lo siguiente en una celda de código:
>
> ~~~
> x = 6 * 7 + 12
> print(x)
> ~~~
> {: .language-python}
>
> Y entonces corre con <kbd>Shift</kbd>+<kbd>Return</kbd> Para estar seguro de que funciona como una celda de código.
> Ahora vuelve a la celda y usa<kbd>Esc</kbd> entonces <kbd>m</kbd> para cambiar la celda a Markdown
> y "run" esto con <kbd>Shift</kbd>+<kbd>Return</kbd>.
> ¿Qué pasó y cómo podría ser útil?
> 
> > ## Solución
> >
> > El código de Python se trata como texto de Markdown.
> > Las líneas aparecen como si fueran parte de un párrafo contiguo.
> > Esto podría ser útil para activar y desactivar temporalmente las celdas en los cuadernos que se utilizan para múltiples propósitos. 
> > ~~~
> > x = 6 * 7 + 12 print(x)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Ecuaciones
>
> Markdown estándar (como el que estamos usando para estas notas) no mostrará ecuaciones,
> pero Notebook lo hará.
> Crea una nueva celda Markdown
> e introduce lo siguiente:
>
> ~~~
> $\sum_{i=1}^{N} 2^{-i} \approx 1$
> ~~~
>
> (Probablemente sea más fácil copiar y pegar.)
> ¿Qué muestra?
> ¿Qué piensas que hace el subguión, `_`, circunflejo, `^`, y el signo de dólar, `$`?
> 
> > ## Solución
> >
> > El cuaderno muestra la ecuación tal como se representaría a partir de la sintaxis de ecuación de LaTeX.
> > El signo de dólar, `$`, se usa para indicarle a Markdown que el texto intermedio es una ecuación de LaTeX.
> > Si no está familiarizado con LaTeX, el guion bajo, `_`, se usa para subíndices y el circunflejo,` ^ `, se usa para superíndices.
> > Se usa un par de llaves, `{` y `}`, para agrupar el texto de manera que la declaración`i=1` se convierta en el subíndice y `N` se convierta en el superíndice.
> > Similarmente, `-i` está entre llaves para hacer que toda la declaración sea el superíndice de
  `2`.
> > `\sum` y `\approx` son comandos LaTeX  para símbolos de "suma" y "aproximados". 
> {: .solution}
{: .challenge}

## Cerrando JupyterLab

*   En la barra de menú, selecciona el menú "File" y elije "Quit" en la parte inferior del menú desplegable. Se te pedirá que confirmes que deseas cerrar el servidor JupyterLab (¡no olvides guardar tu trabajo!). Haga clic en "Confirm" para cerrar el servidor JupyterLab.
*  Para reiniciar el servidor JupyterLab, deberá volver a ejecutar el siguiente comando desde una terminal.

~~~
$ jupyter lab
~~~

> ## Cerrando JupyerLab
>
> Practica cerrar y reiniciar el servidor JupyterLab.
{: .challenge}
[anaconda]: https://docs.continuum.io/anaconda/install
[jupyterlab-ui]: https://jupyterlab.readthedocs.io/en/stable/user/interface.html
[jupyterlab-notebook-docs]: https://jupyterlab.readthedocs.io/en/stable/user/notebook.html
[markdown]: https://en.wikipedia.org/wiki/Markdown

{% include links.md %}

