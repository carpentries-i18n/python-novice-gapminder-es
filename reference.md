---
layout: reference
permalink: /es/reference/
root: /es/_episodes/
---

## Referencia

## [Iniciando y Saliendo]({{ page.root }}/01-run-quit/)
- Los archivos de Python tienen la extensión `.py`.
- Se pueden escribir en un archivo de texto o en una [libreta de Jupyter][jupyter].
  - Los cuadernos de Jupyter tienen la extensión `.ipynb`
  - Los cuadernos de Jupyter se pueden abrir desde [Anaconda](https://docs.continuum.io/anaconda/install) o través de la línea de comandos usando `$ jupyter notebook`
    - Markdown y HTML están permitidos en las celdas de markdown para documentar código.

## [Variables y Asignación]({{ page.root }}/02-variables/)
- Las variables se guardan usando `=`.
  - Las cadenas de texto se definen con comillas `'...'`.
  - Los números enteros y de punto flotante se definen sin comillas.
- Las variables pueden contener letras, números y guiones bajos `_`.
  - No pueden empezar con un número.
  - Las variables que empiezan con un guion bajo deben evitarse.
- Usa `print(...)` para ver los valores como texto.
- Puedes usar indexación en cadenas de texto.
  - La indexación empieza en 0.
  - Las posiciones se definen entre corchetes `[posición]` después del nombre de la variable.
  - Toma un corte usando `[inicio:hasta]`. Esto genera una copia de dicha parte de la cadena de texto original.
    - `inicio` es el índice del primer elemento.
    - `hasta` es el índice del elemento posterior al último deseado.
- Usa `len(...)` para encontrar la longitud de una variable o cadena de texto.

## [Tipos de datos y conversión de tipos]({{ page.root }}/03-types-conversion/)
- Cada valor es de un tipo. Esto controla qué se puede hacer con ello.
  - `int` representa un entero
  - `float` representa un número de punto flotante.
  - `str` representa una cadena de texto.
- Para determinar el tipo de una variable, usa la función de Python `type(...)`, incluyendo el nombre de la variable entre los paréntesis.
- Cambiando cadenas de texto:
  - Usa `+` para concatenar cadenas.
  - Usa `*` para repetir una cadena.
  - Números y cadenas no pueden añadirse entre ellos.
    - Convertir una cadena a un entero: `int(...)`.
    - Convertir un entero a una cadena: `str(...)`.

## [Funciones integradas y Ayuda]({{ page.root }}/04-built-in/)
- Para añadir un comentario, situa una `#` antes de la cosa que no quieres que se ejecute.
- Funciones incorporadas de uso común:
  - `min()` encuentra el valor más pequeño.
  - `max()` encuentra el valor más grande.
  - `round()` redondea un número de punto flotante.
  - `help()` muestra la documentación de la función entre los paréntesis.
    - Otra manera de obtener ayuda es manteniendo la tecla `shift` y pulsando `tab` en una libreta de Jupyter.

## [Bibliotecas]({{ page.root }}/06-libraries/)
- Importando una biblioteca:
  - Usa `import ...` para cargar una bibiloteca.
  - Refierete a esta biblioteca usando `nombre_modulo.nombre_cosa`.
    - `.` significa 'parte de'.
- Para importar un elemento específico de una biblioteca: `from ... import ...` (de la biblioteca importa elemento)
- Para importar una biblioteca con un alias: `import ... as ...` (importa ... como ...)
- Importando la biblioteca de matemáticas: `import math`
  - Ejemplo de referencia a un elemento con el nombre del módulo: `math.cos(math.pi)`.
- Importando la biblioteca de visualización con un alias: `import matplotlib as mpl`

## [Lectura de datos tabulados en DataFrames]({{ page.root }}/07-reading-tabular/)
- Usa la biblioteca pandas para hacer estadística de datos tabulados. Cárgala con `import pandas as pd`.
  - Para leer de un csv: `pd.read_csv()`, incluyendo el camino al fichero entre los paréntesis.
    - Para especificar qué valores de columna deben usarse como cabecera de las filas:  `pd.read_csv('camino', index_col='nombre de columna')`, donde camino y nombre de columna debe cambiarse por los valores correspondientes.
- Para obtener más información sobre un DataFrame, usa `DataFrame.info`, cambiando `DataFrame` con el nombre de la variable de tu DataFrame.
- Usa `DataFrame.columns` para ver los nombres de las columnas.
- Usa `DataFrame.T` para transponer un DataFrame.
- Usa `DataFrame.describe` para obtener un resumen estadístico de tus datos.

## [DataFrames de Pandas]({{ page.root }}/08-data-frames/)
- Selecciona datos usando `[i,j]`
  -  Para seleccionar por la posición de entrada: `DataFrame.iloc[..., ...]`
    - Esto incluye todo excepto el índice final.
  - Para seleccionar por la etiqueta de entrada: `DataFrame.loc[..., ...]`
    - Puedes seleccionar múltiple filas o columnas a través de una lista de etiquetas.
    - Esto incluye ambos límites.
  - Usa `:` para selecionar toda las filas o columnas.
- Puedes seleccionar también datos basados en valores usando `True` y `False`. Esto es una máscara Booleana.
  - `mask = subconjunto > 10000`
  - Podemos usar esto para seleccionar valores.
- Para usar una operación selecciona-usa-combina lo hacemos con `data.apply(lambda x: x > x.mean())` donde `mean()` puede ser cualquier operación que quisiéramos aplicar a `x`.

## [Visualizando]({{ page.root }}/09-plotting/)
- La biblioteca de visualización más usada es `matplotlib`.
  - Normalmente se importa usando `import matplotlib.pyplot as plt`.
  - Para graficar usamos el comando `plt.plot(time, position)`.
  - Para crear una leyenda usa `plt.legend(['label1', 'label2'], loc='upper left')`
    - Puedes también definir las etiquetas dentro del comando `plot` usando `plt.plot(time, position, label='label')`. Para mostrar la leyenda, usa `plt.legend()`
  - Para etiquetar los ejes x e y usa `plt.xlabel('label')` y `plt.ylabel('label')`.
- Los DataFrames de Pandas se pueden visualizar usando `DataFrame.plot()`. Cualquier operación que se puede usar sobre un DataFrame se le puede aplicar mientras se grafica.
  - Para crear una gráfica de barras `data.plot(kind='bar')`

~~~
import matplotlib.puplot as plot
plt.plot(time, position, label='label')
plt.xlabel('x axis label')
plt.ylabel('y axis label')
plt.legend()
~~~
{: .language-python}

## [Listas]({{ page.root }}/11-lists/)
- Definidas entre `[...]` y separadas por `,`.
  - Una lista vacía se puede crear usando `[]`.
- Puedes usar `len(...)` para obtener cuántos valores hay en una lista.
- Puedes indexar como se ha hecho en las lecciones previas.
  - Indexar se puede usar para reasignar valores `nombre_lista[0] = valor_nuevo`.
- Para añadir un elemento a una lista usa `nombre_lista.append()`, con el elemento a añadir entre paréntesis.
- Para combinar dos listas usa `nombre_lista_1.extend(nombre_lista_2)`.
- Para eliminar un elemento de una lista usa `del nombre_lista[index]`.

## [Bucles For]({{ page.root }}/12-for-loops/)
- Empieza un bucle for con `for numero in [1,2,3]:`, con las líneas a continuación indentadas.
  - `[1, 2, 3]` se considera la colección.
  - `numero` es la variable del bucle.
  - La acción que sigue la colección es el cuerpo.
- Para iterar sobre una secuencia de números usa `range(inicio, end)`

~~~
for numero in range(0,5):
  print(numero)
~~~
{: .language-python}

## [Condicionales]({{ page.root }}/13-conditionals/)
- Se definen similarmente a los bucles, usando `if variable condicional valor:`.
  - Por ejemplo, `if variable > 5:`.
- Usa `elif:` para condiciones adicionales.
- Usa `else:` para cuando la condición `if` no es verdad.
- Puedes combinar más de una condición usando `and` (y) u `or` (o).
- A menudo se usan en combinación con los bucles for.
- Condiciones que se pueden usar:
  - `==` igual a.
  - `>=` mayor o igual a.
  - `<=` menor o igual a.
  - `>` mayor que.
  - `<` menor que.

~~~
for m in [3, 6, 7, 2, 8]:
  if m > 5:
    print(m, 'es mayor')
  elif m == 5:
    print(m, 'is 5')
  else:
    print(m, 'es menor')
~~~
{: .language-python}

## [Iterando Sobre Conjunto de Datos]({{ page.root }}/14-looping-data-sets/)
- Usa un bucle for: `for archivo in [archivo1, archivo2]:`
- Para encontrar un conjunto de archivos usando un patrón usa `glob.glob`
  - Debes de importarlo primero usando `import glob`.
  - `*` indica que "coincida con cero o más caracteres"
  - `?` indica que "coincida con exactamente un caracter"
    - Por ejemplo: `glob.glob(*.txt)` encontrará todos los archivos que terminen con `.txt` en el directorio actual.
- Combina ambos escribiendo un bucle usando: `for archivo in glob.glob(*.txt):`

~~~
for archivo in glob.glob(*.txt):
  data = pd.read_csv(archivo)
~~~
{: .language-python}

## [Escribiendo funciones]({{ page.root }}/16-writing-functions/)
- Define una función usando `def nombre_funcion(parametros):`. Cambia `parametros` con las variables a usar cuando la función se ejecute.
- Ejecútala usando `nombre_funcion(parametros)`.
- Para devolver un resultado al que la llama, usa `return ...` dentro de la función.

~~~
def suma_numeros(a, b):
  resultado = a + b
  return resultado

suma_numeros(1, 4)
~~~
{: .language-python}

## [Alcance de una Variable]({{ page.root }}/17-scope/)
- Una variable local se define en una función y sólo puede verse y usarse dentro de dicha función.
- Una variable global se define fuera de una función y puede verse o usarse en cualquier lugar después de su definición.

## [Estilo de Programación]({{ page.root }}/18-style/)
- Documenta tu código.
- Usa nombres de variables que sean claros y significativos.
- Sigue [la guía de estilos PEP8](https://www.python.org/dev/peps/pep-0008) cuando escribas tus programas.
- Usa aserciones para comprobar errores internos.
- Usa docstrings para proporcionar ayuda.

## Glosario

{:auto_ids}
Argumentos
:     Valores pasados a las funciones.

Array
:     Un contenedor con elementos del mismo tipo.

Booleano
:     Un objeto compuesto de `True` (verdadero) y `False` (falso).

DataFrame
:     La forma en que Pandas representa una tabla; una colección de series.

Elemento
:     Un artículo en una lista o un array. Para una cadena, son los caracteres individuales.

Función
:     Un bloque de código que se puede llamar y reusar en otras partes.

Variable global
:     Una variable definida fuera de una función que se puede usar en cualquier sitio.

Índice
:     La posición de un elemento dado.

Libreta de Jupyter
:     Entorno interactivo de programación que permite combinar código y markdown.

Biblioteca
:     Una colección de archivos con funciones usados por otros programas.

Variable Local
:     Una variable definida dentro de una función que sólo puede ser usada dentro de dicha función.

Máscara
:     Un objeto booleano usado para seleccionar datos de otro objeto.

Método
:     Una acción ligada a un objeto en particular. Se le llama usando `objeto.metodo`.

Módulos
:     Los archivos dentro de una biblioteca con funciones usadas por otros programas.

Parámetros
:     Variables usadas cuand se ejecuta una función.

Series
:     Una estructura de datos de Pandas que representa una columna.

Subcadena
:     Una parte de una cadena de texto.

Variables
:     Nombres para valores.

{% include links.md %}

