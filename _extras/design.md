---
layout: page
title: "Diseño de la lección"
permalink: /design/
---

> ## Se busca ayuda
> {:.no_toc}
>
> ** Estamos completando los ejercicios [a continuación] (# etapa-3-plan-de-enseñanza)
> para hacer que el plan de la lección sea más concreto.
> Las contribuciones (tanto en forma de **pull request** con ejercicios completados,
> y comentarios sobre ejercicios específicos, orden y horarios) son muy apreciadas. **
{: .callout}

## Proceso utilizado

> El consejo de Michael Pollan si él enseñara programación en R o Python:
>
> 1. Escribir código.
> 2. No demasiado.
> 3. Principalmente gráficos.
>
> - [Michael Koontz](https://twitter.com/_mikoontz/status/758021742078025728)
{: .quotation}

Esta lección fue desarrollada usando una variante reducida del proceso "Comprensión por diseño".
Las secciones principales son:

1. Suposiciones sobre la audiencia, tiempo, etc.
(El borrador actual también incluye algunas conclusiones y decisiones en  
esta sección, que deben ser consideradas).

2.   Resultados deseados:
    objetivos generales, evaluaciones sumativas al medio día, lo que las estudiantes podrán hacer, lo que las estudiantes aprenderán.

3. Plan de aprendizaje:
cada episodio tiene un encabezado que resume lo que se cubrirá,
luego el tiempo estimado que se dedicará a la enseñanza y a los ejercicios,
mientras que los ejercicios se muestran en puntos.

## Etapa 1: Suposiciones

* Audiencia
    *   Estudiantes de postgrado de varias disciplinas desde astronomía hasta zoología.
    *   Personas que hayan manejado datos en planillas de cálculo y herramientas interactivas como SAS
    *   Personas que *no* han programado más allá de CPD (copiar-pegar-desesperarse)
*   Restricciones
    *   Un día completo de 09:00-16:30
        *   06:15 horas de clase
        *   0:45 almuerzo
        *   0:30 tiempo total para dos pausas
    *   Las estudiantes usan herramientas intaladas en sus propias máquinas
        *   Pueden usar VMs o recursos en la nube si la instructora lo decide
        *   Deben tener una instalación local como opción
    *   No depende de otros módulos de las Carpentries
        *   Particularmente, no requiere conocimiento de la línea de comandos o sistemas de control de versiones
    *   Usa Jupyter Notebooks
        *   La herramienta es usada por muchos instructores
        *   No hay alguna alternativa
        *   Y significa que incluso las personas que hayan visto algo de Python con anterioridad
               probablemente aprenderán algo
* Ejemplo motivador
    * Creación de gráficos en 2D adecuados para su inclusión en publicaciones
    * Motiva a casi todos
    * Hace que la lección sea utilizable por ambas Carpentries
        * Y significa que incluso las personas que han visto un poco de Python antes
           probablemente aprenderá algo
* Datos
    * Utiliza los datos de gapminder en la lección
    * Dividido en múltiples archivos por continente
    * Hacer que la salida de los ejemplos sea más ordenada
      (por ejemplo, usar Australia/New Zealand, que son sólo dos líneas)
    * Y permite ejemplos que muestran el uso de múltiples conjuntos de datos
* Céntrarse en **Pandas** en lugar de NumPy
    * Hace que la lección sea utilizable tanto por Software Carpentry y Data Carpentry
    * Es probable que los principiantes deseen una demostración de análisis de datos
    * Y personas con alguna experiencia previa:
        * aceptarán el análisis de datos como una tarea auténtica,
        * y es poco probable que hayan utilizado Pandas,
          entonces ellos también tendrán algo útil de la lección
* Los desafíos en su mayoría *no* serán "escribir este código desde cero"
    * Se desea que haya muchos ejercicios cortos que se pueden terminar en el tiempo asignado
    * Utiliza MCQ (preguntas de selección múltiple), rellenar los espacios en blanco, problemas de Parsons, "modifique este código", etc.

## Etapa 2: Resultados deseados

### Preguntas

¿Cómo puedo...

*   ...leer datos tabulares?
*   ...graficar un vector de valores?
*   ...crear una gráfica de series de tiempo?
*   ...crear una gráfica para cada conjunto de datos?
*   ...extraer datos de un conjunto de datos para graficar?
*   ...escribir programas que pueda leer y reutilizar en el futuro?

### Habilidades

Yo puedo...

*   ...escribir scripts cortos usando bucles y condicionales.
*   ...escribir funciones con un número fijo de parámetros que retornan un resultado.
*   ...importar bibliotecas usando aliases y refererenciar al contenido de la biblioteca.
*   ...hacer extracciones de datos simples y formatear datos usando Pandas.

### Conceptos

Yo sé...

*   ...que un programa es una herramienta para el análisis de datos
    *   Necesita ser validado/calibrado antes/durante el uso
    *   Hace los análisis reproducibles, revisables, compartibles
*   ...que los programas son escritos para personas no para computadoras
    *   Usar nombres de variable significativos
    *   Usar modularidad para legibilidad y reutilización
    *   Evitar duplicación
    *   Documentar el propósito y el uso
*   ...que no hay resultados mágicos y que los programas que usan no son diferentes
de los que ellas hacen
* ... cómo asignar valores a las variables
* ... que son números enteros, flotantes, cadenas, arreglos en NumPy y dataframes de Pandas
* ... cómo rastrear la ejecución de un bucle `for`
* ... cómo rastrear la ejecución de sentencias `if` /` else`
* ... cómo crear e indexar listas
* ... cómo crear e indexar arreglos de NumPy
* ... cómo crear e indexar dataframes en Pandas
* ... cómo crear gráficas de series de tiempo
* ... la diferencia entre definir y llamar a una función
* ... dónde encontrar documentación sobre bibliotecas estándar
* ... cómo averiguar qué más ofrece Python científico

## Etapa 3: Plan de aprendizaje

### Evaluación sumativa

*   A la mitad de la lección: crear una gráfica de series de tiempo por cada archivo de datos en una carpeta
*   Final: extraer datos de un DataFrame de Pandas
    y  crear gráficas de series de tiempo comparables de varias líneas

### [Correr y salir interactivamente]({{page.root}}/01-run-quit/) (9:00)

*   Enseñanza: 15 min (debido a problemas de configuración)
    *    Iniciar Jupyter Notebooks, crear nuevos cuadernos y salir de Notebook.
    *   Crear celdas de Markdown en un cuaderno.
    *   Crear y correr celdas de Python en un cuaderno.
*   Desafíos: 0 min (contando el tiempo de enseñanza - sin ejercicios separados)
    *   Crear listas en Markdown
    *   ¿Qué se muestra cuando varias expresiones se escriben en una celda?
    *   Cambiar el tipo de una celda existente de código a Markdown
    *   Formatear ecuaciones estilo LaTeX

### [Variables y Asignaciones]({{page.root}}/02-variables/) (9:15)

*   Enseñanza: 10 min
    *   Escribir programas que asignan valores escalares a variables y hacen cálculos con esos valores.
    *   Rastrear cambios en los programas que usan asignaciones de escalares.
*   Desafíos: 10 min
    *   Rastrear la ejecución de intercambio de código de dos valores usando variables intermedias.
    *   Predecir el valor final de una variable después de varias asignaciones.
    *   ¿Qué pasa si tratas de indexar un número?
    *   ¿Qué nombre es mejor para una variable `m`, `min`, or `minutos`?
    *   ¿Qué producen los siguentes cortes?

### [Tipos de Datos y Conversión de tipo de datos]({{page.root}}/03-types-conversion/) (09:35)

*   Enseñanza: 10 min
    *   Explicar la diferencia entre los enteros y los números de punto flotante.
    *   Explicar la diferencia entre números y las cadenas de caracteres.
    *   Usar funciones incorporadas para convertir enteros, números de punto flotante y secuencias de caracteres.
*   Desafíos: 10 min
    *   ¿Qué tipo de dato es 3.4?
    *   ¿Qué tipo de dato es 3.25 + 4?
    *   ¿Qué tipo de dato usarías para representar:
        *   Número de días desde el inicio del año?
        *   El tiempo que ha pasado desde el inicio del año?
        *   Etc.
    *   ¿Cómo puedes usar `//` (división de enteros) y `%` (módulo)?
    *   ¿Qué hace `int("3.4")`?
    *   Dados estos números de punto flotante, enteros, y secuencias de caracteres, ¿qué expresiones mostrarán un resultado en particular?
    *   ¿Qué esperas que `1+2j + 3` produzca?

### [Funciones incorporadas y ayuda]({{page.root}}/04-built-in/) (09:55)

*   Enseñanza: 15 min
    *   Explicar el propósito de las funciones.
    *   Llamar correctamente las funciones incorporadas de Python.
    *   Anidar correctamente las llamadas a las funciones incorporadas.
    *   Usar la ayuda para mostras documentación de las funciones incorporadas.
    *   Describe correctamente situaciones en las que ocurren **SyntaxError** y **NameError**.
*   Desafíos: 10 min
    *   Explica el orden de las operaciones en la siguiente expresión compleja.
    *    ¿Qué producirá cada combinación anidada de llamadas `min` y` max`?
    *   ¿Por qué `max` y `min` no devuelven `None` cuando no se presentan argumentos?
    *   Dado lo que hemos visto hasta ahora,
         ¿Qué expresión de índice obtendrá el último carácter en una secuencia de caracteres?

### [Café]({{page.root}}/05-coffee/): 15 min (10:20)

### [Bibliotecas]({{page.root}}/06-libraries/) (10:35)

*   Enseñanza: 10 min
    *   Explica qué son las bibliotecas de software y por qué los programadores las crean y usan.
    *   Escribe programas que importen y usen bibliotecas de la biblioteca estándar de Python.
    *   Busca y lee la documentación para bibliotecas estándar de forma interactiva (en el intérprete) y en línea.
*   Desafíos: 10 min
    *   ¿Qué función de la biblioteca matemática estándar podrías usar para calcular una raíz cuadrada?
    *   ¿Qué biblioteca usarías para seleccionar un valor aleatorio de los datos?
    *   Si `help(math)` produce un error, ¿qué has olvidado hacer?
    *  Completa los espacios en blanco en el código a continuación para que la importación y el programa se ejecuten.

### [Lectura de Datos Tabulados]({{page.root}}/07-reading-tabular/) (10:55)

*   Enseñanza: 10 min
    *   Importar la biblioteca Pandas.
    *   Usar Pandas para cargar un conjunto de datos CSV simple.
    *   Obtener información básica sobre un DataFrame de Pandas.
*   Desafíos: 10 min
    *   Leer los datos de las Américas y mostrar sus estadísticas resumidas.
    *   ¿Qué hacen `.head` y `.tail`?
    *  ¿Qué secuencia de caracteres debes pasar a `read_csv` para leer archivos de otros directorios?
    *   ¿Cómo puedes *escribir* datos CSV?

### [DataFrames]({{page.root}}/08-data-frames/) (11:15)

*   Enseñanza: 15 min
    *   Seleccionar valores individuales de un dataframe de Pandas.
    *   Seleccionar filas o columnas enteras de un dataframe.
    *   Seleccionar un subconjunto de filas y columnas de un dataframe en una sola operación.
    *   Seleccionar un subconjunto de un dataframe por un único criterio booleano.
*   Desafíos: 15 min.
    *   Escribir una expresión para encontrar el PIB per cápita de Serbia en 2007.
    *   ¿Qué regla rige lo que se incluye (o no) en cortes numéricos y con nombre en Pandas?
    *   ¿Qué hace cada línea en el siguiente programa corto?
    *  ¿Qué hacen `idxmin` e` idxmax`?
    *   Escriba expresiones para obtener el PIB per cápita para todos los países en 1982,
    para todos los países *después de* 1985,
    etc.
    * Dada la forma en que sus fronteras han cambiado desde 1900,
    ¿Qué harías si te pidieran crear una tabla de PIB per cápita para Polonia?
    para el siglo veinte?

### [Graficación]({{page.root}}/09-plotting/) (11:45)

*   Enseñanza: 15 min
    *   Cree un gráfico de series de tiempo que muestre un único conjunto de datos.
    *   Cree un gráfico de dispersión que muestre la relación entre dos conjuntos de datos.
*   Ejercicio: 15 min.
    *   Complete los espacios en blanco para graficar el PIB mínimo per cápita a lo largo del tiempo para los países europeos.
    *   Modifique el ejemplo para crear un gráfico de dispersión del PIB per cápita en los países asiáticos.
    *   Explique qué hace cada argumento de `plot` en el siguiente ejemplo.

### [Almuerzo]({{page.root}}/10-lunch/) (12:15): 45 min

### [Listas]({{page.root}}/11-lists/) (13:00)

*   Enseñanza: 10 min
    *   Explique por qué los programas necesitan colecciones de valores.
    *   Escriba programas que creen listas planas, indexe, fraccione y modifique mediante asignaciones y llamadas a métodos.
*   Desafíos: 10 min
    *  Complete los espacios en blanco para que el programa produzca el resultado que se muestra.
    *   ¿Cuán grandes son los siguientes cortes?
    *   ¿Qué imprimen las expresiones de índice negativo?
    *   ¿Qué hace `stride` en un corte?
    *   ¿Cómo se manejan los límites de rango en los cortes?
    *   ¿Cuál es la diferencia en ordenar usando estas dos maneras?
    *   ¿Cuál es la diferencia entre `nuevo = viejo` y `nuevo = viejo[:]`?

### [Bucles]({{page.root}}/12-for-loops/) (13:20)

*   Enseñanza: 10 min
    *   Explicar para que son usados los bucles.
    *   Rastrear la ejecución de un bucle simple (no anidado) y correctamente indicar el estado de los valores de cada variable en cada interación.
    *   Escribir bucles que usan un patrón acumulador para agregar valores.
*   Desafíos: 15 min.
    *   ¿Un error de indentación es un error de syntax o runtime?
    *   Rastrear que líneas del programa son ejecutadas y en qué orden.
    *   Llenar los espacios en blanco en este program para invertir la secuencia de caracteres.
    *   Llenar los espacios en blanco en estos ejemplos para ganar práctica en valores acumulados.
    *   Reordenar e indentar estas líneas para calcular la suma cumulativa de los valores de la lista.

### [Iterando Sobre Datos]({{page.root}}/13-looping-data-sets/) (13:45)

*   Desafíos: 15 min.
    *   Ser capaz de leer y escribir expresiones **glob** que encuentren un conjunto de archivos.
    *   Usar `glob` para crear listas de archivos.
    *   Escribir bucles para realizar operaciones en archivos, dada una lista con sus nombres.
*   Desafíos: 10 min
    *  ¿Qué archivos no se encuentran con una expresión **glob**?
    *   Modificar este programa para mostrar el número de filas en el archivo más pequeño.
    *   Escribir un programa que lea y visualice todos los datos regionales.

### [Escribiendo Funciones]({{page.root}}/14-writing-functions/) (14:00)

*   Enseñanza: 10 min
    *   Explicar e identificar la diferencia entre definir y llamar una función.
    *   Escribir una función que recibe un número definido de argumentos y produce un resultado.
*   Desafíos: 15 min.
    *   Este código define y llama a una función - ¿Qué muestra cuando se ejecuta?
    *   Explicar por que este programa muestra cosas en un orden particular.
    *   Llenar los espacios en blanco para crear una función que encuentra el valor mínimo en un archivo de datos.
    *   Llenar los espacios en blanco para crear una función que encuentre el primer valor negativo en una lista.
        ¿Qué hace la función si la lista está vacía?
    *   ¿Porqué es importante pasar argumentos nombrando los parámetros correspondientes?
    *   Llena los espacios en blanco y convierte este código en una función.

### [Alcance de una variable]({{page.root}}/15-scope/) (14:25)

*   Enseñanza: 10 min
    *   Identificar variables locales y globales.
    *   Identificar parámetros como variables locales.
    *   Leer un rastreo y determinar el archivo, la función y el número de línea donde el error ha ocurrido.
*   Desafíos: 10 min
    *   Rastrear los cambios de valores en el programa,
        siendo cuidadosa en distinguir valores locales de globales.

### [Café]({{page.root}}/16-coffee/) (14:45): 15 min

### [Condicionales]({{page.root}}/17-conditionals/) (15:00)

*   Enseñanza: 10 min
    *   Escribir correctamente programas que usan declaraciones if y else y expresiones booleanas (sin operadores lógicos).
    *   Rastrear la ejecución de condicionales no anidados y condicionales dentro de bucles.
*   Desafíos: 15 min.
    *   Rastrear la ejecución de esta declaración condicional.
    *   Llena los espacios en blanco para que esta función remplace los valores negativos por ceros.
    *   Modifica este programa para que sólo procese archivos de menos de 50 registros.
    *   Modifica este programa para que siempre encuentre el valor máximo y mínimo en una lista
        sin importar los valores en la lista.

### [Estilo de Programación]({{page.root}}/18-style/) (15:25)

*   Enseñanza: 15 min
    *   ¿Cómo puedo hacer mis programas más legibles?
    *   ¿Cómo formatean su código la mayoría de los programadores?
    *  ¿Cómo pueden los programas revisar sus operaciones?
*   Desafíos: 15 min.
    *   ¿Qué líneas en este código estarán disponibles como ayuda online?
    *   Convertir los comentarios de un programa en docstrings.
    *   Reescribir este pequeño programa para que sea más fácil de leer.

### [Cerrar]({{page.root}}/19-wrap/) (15:55)

*   Enseñanza: 20 min
    *   Nombrar y localizar sitios web de la comunidad científica de Python para software, talleres, y ayuda.
*   Desafíos: 0 min
    *   Ninguno.

### [Retroalimentación]({{page.root}}/20-feedback/) (16:15)

*   Enseñanza: 0 min
*   Desafíos: 15 min.
    *   Recopilar comentarios

### Fin (16:30)

