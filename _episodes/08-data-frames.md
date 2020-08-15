---
title: "DataFrames de Pandas"
teaching: 15
exercises: 15
questions: 
- "¿Cómo puedo hacer análisis estadístico con datos tabulares?"
objetives:
- "Seleccionar valores individuales de un DataFrame de Pandas"
- "Seleccionar filas enteras o columnas enteras de un DataFrame"
- "Seleccionar un subconjunto de ambas filas y columnas de un DataFrame en una operación singular."
- "Seleccionar un subconjunto de un DataFrame por un booleano singular"
keypoints: 
- "Usa `DataFrame.iloc[...,...]`para seleccionar valores por su localización entera"
- "Usa `:` solo,  para referirte a todas las columnas o a todos los renglones"
- "Selecciona múltiples columnas o filas usando `DataFrame.loc` y un segmento con nombre. "
- "El resultado de cortar puede ser usado en operaciones adicionales"
- "Usa comparaciones para seleccionar datos basados en un valor"
- "Selecciona valores de NaN usando mascaras booleanas"
---

## Nota acerca de  pandas DataFrames/Series

Un  [DataFrame][pandas-dataframe] es una colección de  [Series][pandas-series]; 
El DataFrame es la manera en que pandas representa una tabla,  y una Serie es la estructura de datos que usa 
Pandas para representar una columna.

Pandas esta construido en el top de la biblioteca [Numpy][numpy], la cual en la práctica significa que
la mayoría de los métodos  definidos para Numpy arrays aplican a Series/DataFrames de Pandas.

Lo que hace que pandas sea tan atractivo es la potente interfaz para acceder a registros individuales
de la tabla, el manejo adecuado de valores perdidos y las operaciones de bases de datos relacionales
entre DataFrames.

## Seleccionando valores

Para acceder a un valor en la posición `[i, j]` de un DataFrame, tenemos dos opciones, dependiendo de cuál es el significado de `i` en uso. Recuerda que un DataFrame proporciona un *índice* como una forma para identificar las filas de la tabla;  Una fila, entonces, tiene una *posición* dentro de la tabla, así como una *etiqueta*, que identifica de forma única su *entrada* en el DataFrame.

## Usa `DataFrame.iloc[..., ...]` para seleccionar valores por su (entrada) posición

*   Puedes especificar la localización por un indice numérico de forma análoga a la version2D  de la selección de caracteres en cadenas.

~~~
import pandas as pd
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.iloc[0, 0])
~~~
{: .language-python}
~~~
1601.056136
~~~
{: .output}

## Usa `DataFrame.loc[..., ...]`  para seleccionar  valores por su  (entrada) etiqueta.

*   Puedes especificar la localización por el nombre de la fila de forma análoga a la versión 2D de las claves del diccionario.

~~~
data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
print(data.loc["Albania", "gdpPercap_1952"])
~~~
{: .language-python}
~~~
1601.056136
~~~
{: .output}
## Usa `:`  por si sola para referirte a todas las columnas o todos los renglones.

* Al igual que la notación de segmentación habitual de Python.

~~~
print(data.loc["Albania", :])
~~~
{: .language-python}
~~~
gdpPercap_1952    1601.056136
gdpPercap_1957    1942.284244
gdpPercap_1962    2312.888958
gdpPercap_1967    2760.196931
gdpPercap_1972    3313.422188
gdpPercap_1977    3533.003910
gdpPercap_1982    3630.880722
gdpPercap_1987    3738.932735
gdpPercap_1992    2497.437901
gdpPercap_1997    3193.054604
gdpPercap_2002    4604.211737
gdpPercap_2007    5937.029526
Name: Albania, dtype: float64
~~~
{: .output}

*   Podría dar el mismo resultado imprimiendo `data.loc["Albania"]` (sin el segundo indice).

~~~
print(data.loc[:, "gdpPercap_1952"])
~~~
{: .language-python}
~~~
country
Albania                    1601.056136
Austria                    6137.076492
Belgium                    8343.105127
⋮ ⋮ ⋮
Switzerland               14734.232750
Turkey                     1969.100980
United Kingdom             9979.508487
Name: gdpPercap_1952, dtype: float64
~~~
{: .output}

*   Podría dar el mismo resultado imprimiendo `data["gdpPercap_1952"]`
*   También puede dar el mismo resultado imprimiendo `data.gdpPercap_1952` ( No recomendado, porque es fácil confundir con  la notación `.` por los métodos)

## Selecciona multiples columnas o filas usando `DataFrame.loc`  y un segmento con nombre.

~~~
print(data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972'])
~~~
{: .language-python}
~~~
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy           8243.582340    10022.401310    12269.273780
Montenegro      4649.593785     5907.850937     7778.414017
Netherlands    12790.849560    15363.251360    18794.745670
Norway         13450.401510    16361.876470    18965.055510
Poland          5338.752143     6557.152776     8006.506993
~~~
{: .output}

En el código de arriba, descubrimos que  **slicing usando `loc` es inclusivo en ambos
extremos**,  lo cual  difiere de  **slicing usando `iloc`**, donde el corte indica
todo pero sin incluir el índice final. 


## El Resultado de los cortes pueden ser usados en  otras operaciones.

*   Usualmente no solo imprimimos un corte
*   Todos los operadores estadísticos que trabajan sobre DataFrames completos.
trabajan de igual manera sobre los cortes
Por ejemplo, calcular el max de un corte

~~~
print(data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972'].max())
~~~
{: .language-python}
~~~
gdpPercap_1962    13450.40151
gdpPercap_1967    16361.87647
gdpPercap_1972    18965.05551
dtype: float64
~~~
{: .output}

~~~
print(data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972'].min())
~~~
{: .language-python}
~~~
gdpPercap_1962    4649.593785
gdpPercap_1967    5907.850937
gdpPercap_1972    7778.414017
dtype: float64
~~~
{: .output}

## Usa compariciones para seleccionar datos basados en el valor.

*   La comparación es aplicada elemento por elemento.
*   Regresa un DataFrame con una forma similar de  `True`  y `False`.

~~~
# Usa un subconjunto de datos para mantener la salida legible.
subset = data.loc['Italy':'Poland', 'gdpPercap_1962':'gdpPercap_1972']
print('Subset of data:\n', subset)

# Cuales valores son más grandes que 10000 ?
print('\nWhere are values large?\n', subset > 10000)
~~~
{: .language-python}
~~~
Subset of data:
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy           8243.582340    10022.401310    12269.273780
Montenegro      4649.593785     5907.850937     7778.414017
Netherlands    12790.849560    15363.251360    18794.745670
Norway         13450.401510    16361.876470    18965.055510
Poland          5338.752143     6557.152776     8006.506993

Donde están los valores grandes?
            gdpPercap_1962 gdpPercap_1967 gdpPercap_1972
country
Italy                False           True           True
Montenegro           False          False          False
Netherlands           True           True           True
Norway                True           True           True
Poland               False          False          False
~~~
{: .output}

## Selecciona valores o NaN usando una máscara Booleana.

*   Un marco lleno de Booleanos es llamado algunas veces *mask*  por cómo se puede usar.

~~~
mask = subset > 10000
print(subset[mask])
~~~
{: .language-python}
~~~
             gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
country
Italy                   NaN     10022.40131     12269.27378
Montenegro              NaN             NaN             NaN
Netherlands     12790.84956     15363.25136     18794.74567
Norway          13450.40151     16361.87647     18965.05551
Poland                  NaN             NaN             NaN
~~~
{: .output}

*   Obtendras el valor donde la máscara es verdadera y NaN (no es un número) donde es falsa
* Esto es útil porque los NaNs son ignorados por operadores como max, min, average, etc.

~~~
print(subset[subset > 10000].describe())
~~~
{: .language-python}
~~~
       gdpPercap_1962  gdpPercap_1967  gdpPercap_1972
count        2.000000        3.000000        3.000000
mean     13120.625535    13915.843047    16676.358320
std        466.373656     3408.589070     3817.597015
min      12790.849560    10022.401310    12269.273780
25%      12955.737547    12692.826335    15532.009725
50%      13120.625535    15363.251360    18794.745670
75%      13285.513523    15862.563915    18879.900590
max      13450.401510    16361.876470    18965.055510
~~~
{: .output}

## Group By: cortar-aplicar-combinar

Los métodos de vectorización de pandas y las operaciones de agrupación son características que brindan a los usuarios mucha flexibilidad para analizar sus datos.

Por ejemplo, supongamos que queremos tener una visión más clara de cómo los países europeos se dividen según su PIB (GDP).

1. Podemos echar un vistazo dividiendo los países en dos grupos durante los años encuestados,
aquellos que presentaron un PIB *más alto* que el promedio europeo y aquellos con un *PIB* más *bajo*. 2. Luego estimamos un *puntaje de Riqueza* basado en los valores históricos (de 1962 a 2007), donde contamos cuántas veces un país ha participado en los grupos de PIB *más bajo* o *más alto*

~~~
mask_higher = data > data.mean()
wealth_score = mask_higher.aggregate('sum', axis=1) / len(data.columns)
wealth_score
~~~
{: .language-python}
~~~
country
Albania                   0.000000
Austria                   1.000000
Belgium                   1.000000
Bosnia and Herzegovina    0.000000
Bulgaria                  0.000000
Croatia                   0.000000
Czech Republic            0.500000
Denmark                   1.000000
Finland                   1.000000
France                    1.000000
Germany                   1.000000
Greece                    0.333333
Hungary                   0.000000
Iceland                   1.000000
Ireland                   0.333333
Italy                     0.500000
Montenegro                0.000000
Netherlands               1.000000
Norway                    1.000000
Poland                    0.000000
Portugal                  0.000000
Romania                   0.000000
Serbia                    0.000000
Slovak Republic           0.000000
Slovenia                  0.333333
Spain                     0.333333
Sweden                    1.000000
Switzerland               1.000000
Turkey                    0.000000
United Kingdom            1.000000
dtype: float64
~~~
{: .output}

Finalmente,  para cada grupo en la tabla  `wealth_score` ,  nosotros sumamos sus contribuciones (financieras)
a través de los años encuestados:

~~~
data.groupby(wealth_score).sum()
~~~
{: .language-python}
~~~
          gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \n0.000000    36916.854200    46110.918793    56850.065437    71324.848786   
0.333333    16790.046878    20942.456800    25744.935321    33567.667670   
0.500000    11807.544405    14505.000150    18380.449470    21421.846200   
1.000000   104317.277560   127332.008735   149989.154201   178000.350040   


          gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \n0.000000    88569.346898   104459.358438   113553.768507   119649.599409   
0.333333    45277.839976    53860.456750    59679.634020    64436.912960   
0.500000    25377.727380    29056.145370    31914.712050    35517.678220   
1.000000   215162.343140   241143.412730   263388.781960   296825.131210   


          gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007  
0.000000    92380.047256   103772.937598   118590.929863   149577.357928  
0.333333    67918.093220    80876.051580   102086.795210   122803.729520  
0.500000    36310.666080    40723.538700    45564.308390    51403.028210  
1.000000   315238.235970   346930.926170   385109.939210   427850.333420
~~~
{: .output}


> ## Selección de valores individuales
>
> Supongamos que se ha importado pandas en tu notebook
> y se han cargado los datos del PIB de Gapminder para Europa:
>
> ~~~
> import pandas como pd
>
 > df = pd.read_csv ('data / gapminder_gdp_europe.csv ', index_col =' country ')
 > ~~~
 > {: .language-python} 
>
 > Escribe una expresión para encontrar el PIB per cápita de Serbia en 2007
{: .challenge}
>
> > ## Solución
> > La selección puede ser hecha usando  las etiquetas para ambos, la fila ("Serbia")  y la columna("gdpPercap_2007"):
> > ~~~
> > print(df.loc['Serbia', 'gdpPercap_2007'])
> > ~~~
> > {: .language-python}
> > The output is
> > ~~~
> > 9786.534714
> > ~~~
> >{: .output}
> {: .solution}
{: .challenge}

> ## Grado de corte
>
> 1.  ¿Las dos instrucciones a continuación producen el mismo resultado?
> 2.  Basados en esto,
>    Que regla gobierna que es incluido (o no) en cortes numéricos y cortes de nombres en Pandas?
> 
> ~~~
> print(df.iloc[0:2, 0:2])
> print(df.loc['Albania':'Belgium', 'gdpPercap_1952':'gdpPercap_1962'])
> ~~~
> {: .language-python}
{: .challenge}
> 
> > ## Solución
> > No, ¡ellos no producen la misma salida! La salida de la primera instrucción es:
> > ~~~
> >         gdpPercap_1952  gdpPercap_1957
> > pais                                
> > Albania     1601.056136     1942.284244
> > Austria     6137.076492     8842.598030
> > ~~~
> >{: .output}
> > La segunda instrucción dá:
> > ~~~
> >         gdpPercap_1952  gdpPercap_1957  gdpPercap_1962
> > pais                                                
> > Albania     1601.056136     1942.284244     2312.888958
> > Austria     6137.076492     8842.598030    10750.721110
> > Belgium     8343.105127     9714.960623    10991.206760
> > ~~~
> >{: .output}
> > Claramente, la segunda instrucción produce una columna y una fila adicional comparado a la primera instrucción.  
> >¿Qué conclusión podemos sacar? Vemos que un corte numérico, 0: 2, *omite* el índice final (es decir, el índice 2) 
> > en el rango proporcionado,
> > mientras un corte con nombre, 'gdpPercap_1952':'gdpPercap_1962', *incluye* el elemento final.
> {: .solution}
{: .challenge}

> ## Reconstruyendo Datos
>
> Explica que hace cada linea en el siguiente programa corto:
> ¿Que hay en  `first`, `second`, etc.?
>
> ~~~
> first = pd.read_csv('data/gapminder_all.csv', index_col='country')
> second = first[first['continent'] == 'Americas']
> third = second.drop('Puerto Rico')
> fourth = third.drop('continent', axis = 1)
> fourth.to_csv('result.csv')
> ~~~
> {: .language-python}
{: .challenge}
>
> > ## Solución
> > Repasemos este código línea por línea.
> > ~~~
> > first = pd.read_csv('data/gapminder_all.csv', index_col='country')
> > ~~~
> > {: .language-python}
> > Esta linea carga el set de datos conteniendo los datos del PIB (GDP) de todos los países dentro de un DataFrame llamado
> > `first`. El parámetro `index_col='country'`  selecciona cual columna usar como las  
> > etiquetas de las filas en el dataframe.  
> > ~~~
> > second = first[first['continent'] == 'Americas']
> > ~~~
> > {: .language-python}
> > Esta linea hace una selección: solo se extraen aquellas filas de `first` para los cuales la columna 'continent' coincide con 
> > 'Americas'. Nota como la expresión Booleana dentro de los  paréntesis, 
> > `first['continent'] == 'Americas'`, es usada para seleccionar solo aquellas filas donde la expresión es verdadera. 
> > Intenta imprimir esta expresión! ¿Puedes imprimir  también los valores individuales de los elementos True/False? 
> > (sugerencia: Primero asigna la expresión a una variable)
> > ~~~
> > third = second.drop('Puerto Rico')
> > ~~~
> > {: .language-python}
> > Como sugiere la sintaxis, esta linea remueve la fila de `second`  donde la etiqueta es 'Puerto Rico'. El 
> > resultado DataFrame `third` tiene una fila menos que el DataFrame original `second`.
> > ~~~
> > fourth = third.drop('continent', axis = 1)
> > ~~~
> > {: .language-python}
> > Otra vez aplicamos la función drop, pero en este caso no estamos removiendo una fila sino una columna completa.  
> > Para lograr esto, necesitamos especificar también el parámetro `axis` (queremos remover la segunda columna 
> > la cual tiene el indice 1).
> > ~~~
> > fourth.to_csv('result.csv')
> > ~~~
> > {: .language-python}
> > El paso final es escribir los datos que hemos trabajado en un archivo csv. Pandas hace esto muy facil 
> > con la función `to_csv()`.  El único argumento requerido por la función es el nombre del archivo. Nota que el 
> > archivo será escrito en el directorio en el cual tu hayas iniciado la sesión de Jupyter o Python.
> {: .solution}
{: .challenge}

> ## Seleccionando  Indices
>
> Explica en términos simples que hace `idxmin` y `idxmax` en el breve programa a continuación.
> ¿Cuándo usarías estos métodos?
>
> ~~~
> data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
> print(data.idxmin())
> print(data.idxmax())
> ~~~
> {: .language-python}
{: .challenge}
>
> > ## Solución
> > Por cada columna en `data`, `idxmin` retornará el indice del valor correspondiente al mínimo de cada columna:
> > `idxmax` hará lo mismo para el valor máximo de cada columna.
> >
> > Tu puedes usar estas funciones, siempre que quieras obtener el indice de la fila con el mínimo / máximo  valor y no el valor mínimo /máximo actual. 
> {: .solution}
{: .challenge}

> ## Practica con Selección
>
> Asume que Pandas ha sido importado y los datos de GDP de Gapminder para Europe han sido cargados.
> Escribe una expresión para seleccionar cada uno de los siguientes:
>
> 1.  GDP per capita para todos los países en 1982.
> 2.  GDP per capita para Denmark para todos los años.
> 3.  GDP per capita para todos los países para los años  *después de* 1985.
> 4.  GDP per capita para cada país en 2007 como un múltiple de 
>     GDP per capita para aquellos países en  1952.
{: .challenge}
>
> > ## Solución
> > 1:
> > ~~~
> > data['gdpPercap_1982']
> > ~~~
> > {: .language-python}
> >
> > 2:
> > ~~~
> > data.loc['Denmark',:]
> > ~~~
> > {: .language-python}
> >
> > 3:
> > ~~~
> > data.loc[:,'gdpPercap_1985':]
> > ~~~
> > {: .language-python}
> > Pandas es lo suficientemente inteligente como para reconocer el número al final de la etiqueta de la columna y no te da un error, aunque en realidad no existe una columna llamada `gdpPercap_1985`. Esto es útil si se agregan nuevas columnas al archivo CSV después.
> >
> > 4:
> > ~~~
> > data['gdpPercap_2007']/data['gdpPercap_1952']
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}


> ## Usando la función dir para ver los métodos disponibles
>
> Python incluye una función `dir`  que puede ser usada para desplegar todas los métodos disponibles (funciones) dentro de un objeto de datos. Como un ejemplo,  las funciones disponibles para una [list data type](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists) son:
> ~~~
> potatoes = ["Russet", "Norkota", "Yukon Gold", "Pontiac"]
> dir(potatoes)
> ~~~
> {: .language-python}
>
> Este comando regresa:
> ~~~
> ['__add__',
> ...
> '__subclasshook__',
>  'append',
>  'clear',
>  'copy',
>  'count',
> 'extend',
> 'index',
> 'insert',
> 'pop',
> 'remove',
> 'reverse',
> 'sort']
> ~~~
> {: .language-python}
>
> Las funciones con doble guion bajo pueden ser ignoradas por ahora; las  funciones que no están bordeadas por un doble guion bajo son la *interface publica*  de la [list type](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists). Así, si tu quieres ordenar la lista de patatas, acorde a  `dir` podrías intentar,
> ~~~
> potatoes.sort()
> ~~~
> {: .language-python}
>
> Asume que  Pandas ha sido importado y los datos del PIB (GDP) de Gapminder para Europa han sido cargados como  `data`.  Entonces, usa `dir` para encontrar la función para imprimir la media del PIB per-capita a través de todos los países Europeos  por cada año de información disponible.  
{: .challenge}
>
> > ## Solución
> >  Entre muchas opciones, dir enumera la función `median()` como una posibilidad. Así,
> > ~~~
> > data.median()
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}


> ## Interpretación
>
> Las fronteras de Polonia se han mantenido estables desde 1945,
> pero cambió varias veces en los años anteriores.
> ¿Cómo manejarías esto si estuvieras creando una tabla de PIB per cápita para Polonia
> para todo el siglo XX?
{: .challenge}


[pandas-dataframe]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html
[pandas-series]: https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.html
[numpy]: http://www.numpy.org/

