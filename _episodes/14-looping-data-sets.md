---
title: "Iterando Sobre Datos"
teaching: 5
exercises: 10
questions:
- "¿Cómo puedo procesar muchos data sets con un solo comando?"
objectives:
- "Ser capaz de leer y escribir expresiones globales que coincidan con conjuntos de archivos."
- "Uso de 'glob' para crear listas de archivos."
- "Escribir bucles para realizar operaciones en archivos dando sus nombres en una lista."
keypoints:
- "Usar un bucle `for` para procesar el archivos dando una lista de sus nombres."
- "Usar `glob.glob` para encontrar conjuntos de archivos cuyos nombres coinciden con un patrón."
- "Usar `glob` y `for` para procesar un grupo de archivos."
---

## Usa un bucle `for` para procesar archivos dando una lista de sus nombres.

*   Un nombre de archivo es una cadena de caracteres.
*   Y las listas pueden contener cadenas de caracteres.

~~~
import pandas as pd
for filename in ['data/gapminder_gdp_africa.csv', 'data/gapminder_gdp_asia.csv']:
    data = pd.read_csv(filename, index_col='country')
    print(filename, data.min())
~~~
{: .language-python}
~~~
data/gapminder_gdp_africa.csv gdpPercap_1952    298.846212
gdpPercap_1957    335.997115
gdpPercap_1962    355.203227
gdpPercap_1967    412.977514
⋮ ⋮ ⋮
gdpPercap_1997    312.188423
gdpPercap_2002    241.165877
gdpPercap_2007    277.551859
dtype: float64
data/gapminder_gdp_asia.csv gdpPercap_1952    331
gdpPercap_1957    350
gdpPercap_1962    388
gdpPercap_1967    349
⋮ ⋮ ⋮
gdpPercap_1997    415
gdpPercap_2002    611
gdpPercap_2007    944
dtype: float64
~~~
{: .output}

## Usa [`glob.glob`](https://docs.python.org/3/library/glob.html#glob.glob) para encontrar conjuntos de archivos cuyos nombres coinciden con un patrón.

*  En Unix, el término "globbing" significa "coincidir un conjunto de archivos con un patrón". 
*   Los patrones más comunes son:
    *   `*` significa "coincide con cero o más caracteres"
    *   `?` significa "coincide exactamente con un carácter"
*   Python contiene la biblioteca [`glob`] (https://docs.python.org/3/library/glob.html) para proporcionar la funcionalidad de los patrones de coincidencia
*   La biblioteca [`glob`] (https://docs.python.org/3/library/glob.html) contiene una función también llamada` glob` para encontrar coincidencias con patrones de archivo
*   Por ejemplo, `glob.glob('*.txt')` coincide con todos los archivos en el directorio actual
    cuyos nombres terminan con `.txt`.
*   El resultado es una lista (posiblemente vacía) de cadenas de caracteres.

~~~
import glob
print('all csv files in data directory:', glob.glob('data/*.csv'))
~~~
{: .language-python}
~~~
all csv files in data directory: ['data/gapminder_all.csv', 'data/gapminder_gdp_africa.csv', \n'data/gapminder_gdp_americas.csv', 'data/gapminder_gdp_asia.csv', 'data/gapminder_gdp_europe.csv', \n'data/gapminder_gdp_oceania.csv']
~~~


{: .output}

~~~
print('all PDB files:', glob.glob('*.pdb'))
~~~
{: .language-python}
~~~
all PDB files: []
~~~
{: .output}

## Usa `glob` y` for` para procesar grupos de archivos.

*   Ayuda mucho si los archivos se nombran y almacenan de manera sistemática y consistente
    de forma que patrones simples encuentren los datos correctos.

~~~
for filename in glob.glob('data/gapminder_*.csv'):
    data = pd.read_csv(filename)
    print(filename, data['gdpPercap_1952'].min())
~~~
{: .language-python}
~~~
data/gapminder_all.csv 298.8462121
data/gapminder_gdp_africa.csv 298.8462121
data/gapminder_gdp_americas.csv 1397.717137
data/gapminder_gdp_asia.csv 331.0
data/gapminder_gdp_europe.csv 973.5331948
data/gapminder_gdp_oceania.csv 10039.59564
~~~
{: .output}

*   Esto incluye todos los datos, así como datos por región.
*   Usa un patrón más específico en los ejercicios para excluir todo el conjunto de datos.
*   Pero nota que el mínimo de todo el conjunto de datos también es el mínimo de uno de los conjuntos de datos,
    lo cual es un buen control sobre la corrección.

> ## Determinación de Coincidencias
>
> ¿Cuál de estos archivos * no * coincide con la expresión`glob.glob('data/*as*.csv')`?
>
> 1. `data/gapminder_gdp_africa.csv`
> 2. `data/gapminder_gdp_americas.csv`
> 3. `data/gapminder_gdp_asia.csv`
> 4. 1 and 2 are not matched.
>
> > ## Solución
> >
> > 1 no coincide por el glob.
> {: .solution}
{: .challenge}

> ## Tamaño mínimo del archivo
>
> Modifique este programa para que imprima el número de registros en
> el archivo que tiene la menor cantidad de registros.
>
> ~~~
> import glob
> import pandas as pd
> fewest = ____
> for filename in glob.glob('data/*.csv'):
>     dataframe = pd.____(filename)
>     fewest = min(____, dataframe.shape[0])
> print('smallest file has', fewest, 'records')
> ~~~
> {: .language-python}
> Nota que el [método shape] (https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.shape.html)
> regresa una tupla con el número de filas y columnas del dataframe.
>
> > ## Solución
> > ~~~
> > import glob
> > import pandas as pd
> > fewest = float('Inf')
> > for filename in glob.glob('data/*.csv'):
> >     dataframe = pd.read_csv(filename)
> >     fewest = min(fewest, dataframe.shape[0])
> > print('smallest file has', fewest, 'records')
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Comparando Datos
>
> Escribe un programa que lea en los datasets regionales.
> y grafica el PIB promedio per cápita para cada región a lo largo del tiempo
> en una simple gráfica.
> > ## Solución
> > Esta solución crea una útil leyenda usando el método de cadena [`split`](https://docs.python.org/3/library/stdtypes.html#str.split) método para
> > extraer la `region` de  el path 'data/gapminder_gdp_a_specific_region.csv'. El [`pathlib module`]
> > también proporciona abstracciones útiles para la manipulación de archivos y rutas, como regresar el nombre de un archivo
> > sin la extensión del archivo.
> > ~~~
> > import glob
> > import pandas as pd
> > import matplotlib.pyplot as plt
> > fig, ax = plt.subplots(1,1)
> > for filename in glob.glob('data/gapminder_gdp*.csv'):
> >     dataframe = pd.read_csv(filename)
> >     # extract <region> from the filename, expected to be in the format 'data/gapminder_gdp_<region>.csv'.
> >     # we will split the string using the split method and `_` as our separator,
> >     # retrieve the last string in the list that split returns (`<region>.csv`), 
> >     # and then remove the `.csv` extension from that string.
> >     region = filename.split('_')[-1][:-4] 
> >     dataframe.mean().plot(ax=ax, label=region)
> > plt.legend()
> > plt.show()
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

