---
title: "Lectura de Datos Tabulares en DataFrames"
teaching: 10
exercises: 10
questions:
- "¿Cómo puedo leer datos tabulares?"
objectives:
- "Importar la biblioteca Pandas."
- "Usar Pandas para cargar un conjunto de datos CSV simple."
- "Obtener información básica sobre un DataFrame de Pandas."
keypoints:
- "Utiliza la biblioteca Pandas para obtener estadísticas básicas de los datos tabulares".
- "Utiliza `index_col` para especificar los valores de la columna que deben usarse como fila de encabezado."
- "Utiliza `DataFrame.info` para obtener más información sobre un dataframe."
- "La variable `DataFrame.columns` almacena información sobre las columnas del dataframe."
- "Utiliza `DataFrame.T` para transponer un dataframe."
- "Utiliza `DataFrame.describe` para obtener estadísticas resumidas sobre los datos."
---
## Utiliza la biblioteca Pandas para hacer estadísticas sobre datos tabulares.

*   Pandas es una biblioteca de Python ampliamente utilizada para estadísticas, particularmente en datos tabulares.
*   Toma prestadas muchas características de los R's dataframes.
    *   Una tabla de 2-dimensiones cuyas columnas tienen nombres
        y potencialmente tienen diferentes tipos de datos.
*   Carga con `import pandas as pd`. El alias pd se usa comúnmente para pandas.
*   Lea un archivo de datos de valores separados por comas (CSV) con `pd.read_csv`.
  *   Argumento es el nombre del archivo para lectura.
  *   Asigna el resultado a una variable para almacenar los datos que se leyeron.

~~~
import pandas as pd

data = pd.read_csv('data/gapminder_gdp_oceania.csv')
print(data)
~~~
{: .language-python}
~~~
       country  gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  \n0    Australia     10039.59564     10949.64959     12217.22686
1  New Zealand     10556.57566     12247.39532     13175.67800


   gdpPercap_1967  gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  \n0     14526.12465     16788.62948     18334.19751     19477.00928
1     14463.91893     16046.03728     16233.71770     17632.41040


   gdpPercap_1987  gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  \n0     21888.88903     23424.76683     26997.93657     30687.75473
1     19007.19129     18363.32494     21050.41377     23189.80135


   gdpPercap_2007
0     34435.36744
1     25185.00911
~~~
{: .output}

*   Las columnas en un dataframe son las variables observadas, y las filas son las observaciones.
*   Pandas usa la barra invertida `\` para mostrar líneas ajustadas cuando la salida es demasiado ancha para caber en la pantalla.

> ## Archivo no encontrado
>
> Nuestras lecciones almacenan sus archivos de datos en un subdirectorio `data`,
> razón por la cual la ruta al archivo es `data/gapminder_gdp_oceania.csv`.
> Si olvida incluir `data/`,
> o si lo incluye pero su copia del archivo está en otro lugar,
> obtendrá un [runtime error]({{ page.root }}/04-built-in/#runtime-error)
> que termina con una línea como esta:
>
> ~~~
> OSError: File b'gapminder_gdp_oceania.csv' does not exist
> ~~~
> {: .error}
{: .callout}

## Utiliza `index_col` para especificar los valores de que columna deben usarse como fila de encabezado.

*   Los encabezados de fila son números (0 y 1 en este caso).
*   Indexar por país.
*   Pase el nombre de la columna a `read_csv` como su parámetro `index_col` para hacer esto.

~~~
data = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')
print(data)
~~~
{: .language-python}
~~~
             gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \ncountry
Australia       10039.59564     10949.64959     12217.22686     14526.12465
New Zealand     10556.57566     12247.39532     13175.67800     14463.91893


             gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \ncountry
Australia       16788.62948     18334.19751     19477.00928     21888.88903
New Zealand     16046.03728     16233.71770     17632.41040     19007.19129


             gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007
country
Australia       23424.76683     26997.93657     30687.75473     34435.36744
New Zealand     18363.32494     21050.41377     23189.80135     25185.00911
~~~
{: .output}

## Utiliza `DataFrame.info` para obtener más información sobre un dataframe.

~~~
data.info()
~~~
{: .language-python}
~~~
<class 'pandas.core.frame.DataFrame'>
Index: 2 entries, Australia to New Zealand
Data columns (total 12 columns):
gdpPercap_1952    2 non-null float64
gdpPercap_1957    2 non-null float64
gdpPercap_1962    2 non-null float64
gdpPercap_1967    2 non-null float64
gdpPercap_1972    2 non-null float64
gdpPercap_1977    2 non-null float64
gdpPercap_1982    2 non-null float64
gdpPercap_1987    2 non-null float64
gdpPercap_1992    2 non-null float64
gdpPercap_1997    2 non-null float64
gdpPercap_2002    2 non-null float64
gdpPercap_2007    2 non-null float64
dtypes: float64(12)
memory usage: 208.0+ bytes
~~~
{: .output}

*   Este es un `DataFrame`
*   Dos filas llamadas `'Australia'` y `'Nueva Zelanda'`
*   Doce columnas, cada una de las cuales tiene dos valores de punto flotante de 64 bits.
    *   Más adelante hablaremos de valores nulos, que se utilizan para representar observaciones faltantes.
*   Utiliza 208 bytes de memoria.

##  La variable `DataFrame.columns` almacena información sobre las columnas del dataframe.

*   Ten en cuenta que se trata de datos, *no* de un método.
    *   Como `math.pi`.
    *   Por lo tanto, no uses `()` para intentar llamarlo.
*   Se llama *variable miembro*, o simplemente *miembro*.

~~~
print(data.columns)
~~~
{: .language-python}
~~~
Index(['gdpPercap_1952', 'gdpPercap_1957', 'gdpPercap_1962', 'gdpPercap_1967',
       'gdpPercap_1972', 'gdpPercap_1977', 'gdpPercap_1982', 'gdpPercap_1987',
       'gdpPercap_1992', 'gdpPercap_1997', 'gdpPercap_2002', 'gdpPercap_2007'],
      dtype='object')
~~~
{: .output}

## Utiliza `DataFrame.T` para transponer el dataframe.

*   A veces se quiere tratar las columnas como filas y viceversa.
*   La transposición (escrita como `.T`) no copia los datos, solo cambia la vista del programa.
*   Al igual que `columns`, es una variable miembro.

~~~
print(data.T)
~~~
{: .language-python}
~~~
country           Australia  New Zealand
gdpPercap_1952  10039.59564  10556.57566
gdpPercap_1957  10949.64959  12247.39532
gdpPercap_1962  12217.22686  13175.67800
gdpPercap_1967  14526.12465  14463.91893
gdpPercap_1972  16788.62948  16046.03728
gdpPercap_1977  18334.19751  16233.71770
gdpPercap_1982  19477.00928  17632.41040
gdpPercap_1987  21888.88903  19007.19129
gdpPercap_1992  23424.76683  18363.32494
gdpPercap_1997  26997.93657  21050.41377
gdpPercap_2002  30687.75473  23189.80135
gdpPercap_2007  34435.36744  25185.00911
~~~
{: .output}

## Utiliza `DataFrame.describe` para obtener estadísticas resumidas sobre los datos.

DataFrame.describe() obtiene las estadísticas de resumen de solo las columnas que tienen datos numéricos.
Todas las demás columnas se ignoran, a menos que use el argumento `include = 'all'`.
~~~
print(data.describe())
~~~
{: .language-python}
~~~
       gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \ncount        2.000000        2.000000        2.000000        2.000000
mean     10298.085650    11598.522455    12696.452430    14495.021790
std        365.560078      917.644806      677.727301       43.986086
min      10039.595640    10949.649590    12217.226860    14463.918930
25%      10168.840645    11274.086022    12456.839645    14479.470360
50%      10298.085650    11598.522455    12696.452430    14495.021790
75%      10427.330655    11922.958888    12936.065215    14510.573220
max      10556.575660    12247.395320    13175.678000    14526.124650


       gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \ncount         2.00000        2.000000        2.000000        2.000000
mean      16417.33338    17283.957605    18554.709840    20448.040160
std         525.09198     1485.263517     1304.328377     2037.668013
min       16046.03728    16233.717700    17632.410400    19007.191290
25%       16231.68533    16758.837652    18093.560120    19727.615725
50%       16417.33338    17283.957605    18554.709840    20448.040160
75%       16602.98143    17809.077557    19015.859560    21168.464595
max       16788.62948    18334.197510    19477.009280    21888.889030


       gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007
count        2.000000        2.000000        2.000000        2.000000
mean     20894.045885    24024.175170    26938.778040    29810.188275
std       3578.979883     4205.533703     5301.853680     6540.991104
min      18363.324940    21050.413770    23189.801350    25185.009110
25%      19628.685413    22537.294470    25064.289695    27497.598692
50%      20894.045885    24024.175170    26938.778040    29810.188275
75%      22159.406358    25511.055870    28813.266385    32122.777857
max      23424.766830    26997.936570    30687.754730    34435.367440
~~~
{: .output}

*   No es particularmente útil con solo dos registros,
    pero muy útil cuando hay miles.

> ## Lectura de otros datos
>
> Lea los datos en `gapminder_gdp_americas.csv`
> (que debe estar en el mismo directorio que `gapminder_gdp_oceania.csv`)
> en una variable llamada `americas`
> y muestra sus estadísticas de resumen.
>
> > ## Solución
> > Para leer en un CSV, usamos `pd.read_csv` y le pasamos el nombre de archivo 'data/gapminder_gdp_americas.csv'. También una vez más pasamos el
> > nombre de columna 'country' al parámetro `index_col` para indexar por país:
> > ~~~
> > americas = pd.read_csv('data/gapminder_gdp_americas.csv', index_col='country')
> > ~~~
> >{: .language-python}
> {: .solution}
{: .challenge}



> ## Inspección de datos.
>
> Después de leer los datos para las Américas,
> use `help(americas.head)` y `help(americas.tail)`
> para averiguar qué hacen `Data Frame.head` y `DataFrame.tail`.
>
> 1. ¿Qué llamado de método mostrará las primeras tres filas de estos datos?
> 2. ¿Qué llamado de método mostrará las últimas tres columnas de estos datos?
>    (Sugerencia: es posible que deba cambiar su vista de los datos).
>
> > ## Solución
> > 1. Podemos ver las primeras cinco filas de `americas` ejecutando` americas.head() `(lo que nos permite ver las primeras filas
> > del DataFrame). Podemos especificar el número de filas que deseamos ver especificando el parámetro `n` en nuestra llamada
> > a `americas.head()`. Para ver las primeras tres filas, ejecute:
> >
> > ~~~
> > americas.head(n=3)
> > ~~~
> >{: .language-python}
> > 
> > La salida es entonces
> > ~~~
> >          continent  gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  \n> >country                                                               
> >Argentina  Americas     5911.315053     6856.856212     7133.166023   
> >Bolivia    Americas     2677.326347     2127.686326     2180.972546   
> >Brazil     Americas     2108.944355     2487.365989     3336.585802   
> >
> >           gdpPercap_1967  gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  \n> >country                                                                     
> >Argentina     8052.953021     9443.038526    10079.026740     8997.897412   
> >Bolivia       2586.886053     2980.331339     3548.097832     3156.510452   
> >Brazil        3429.864357     4985.711467     6660.118654     7030.835878   
> >
> >           gdpPercap_1987  gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  \n> >country                                                                     
> >Argentina     9139.671389     9308.418710    10967.281950     8797.640716   
> >Bolivia       2753.691490     2961.699694     3326.143191     3413.262690   
> >Brazil        7807.095818     6950.283021     7957.980824     8131.212843   
> >
> >           gdpPercap_2007  
> >country                    
> >Argentina    12779.379640  
> >Bolivia       3822.137084  
> >Brazil        9065.800825 
> > ~~~ 
> >{: .output}
> > 2. Para ver las últimas tres filas de `americas`, usaríamos el comando` americas.tail (n = 3) `,
> > análogo a `head ()` usado anteriormente. Sin embargo, aquí queremos ver las últimas tres columnas, que necesitamos
> > para cambiar nuestra vista y luego usar `tail()`. Para hacerlo, creamos un nuevo DataFrame en el que las filas y
> > las columnas se cambian
> > 
> > ~~~
> > americas_flipped = americas.T
> > ~~~
> >{: .language-python}
> >
> > Podemos ver las últimas tres columnas de `americas` al ver las últimas tres filas de` americas_flipped`:
> > ~~~
> > americas_flipped.tail(n=3)
> > ~~~
> >{: .language-python}
> > La salida es entonces
> > ~~~
> > country        Argentina  Bolivia   Brazil   Canada    Chile Colombia  \n> > gdpPercap_1997   10967.3  3326.14  7957.98  28954.9  10118.1  6117.36   
> > gdpPercap_2002   8797.64  3413.26  8131.21    33329  10778.8  5755.26   
> > gdpPercap_2007   12779.4  3822.14   9065.8  36319.2  13171.6  7006.58   
> > 
> > country        Costa Rica     Cuba Dominican Republic  Ecuador    ...     \n> > gdpPercap_1997    6677.05  5431.99             3614.1  7429.46    ...      
> > gdpPercap_2002    7723.45  6340.65            4563.81  5773.04    ...      
> > gdpPercap_2007    9645.06   8948.1            6025.37  6873.26    ...      
> > 
> > country          Mexico Nicaragua   Panama Paraguay     Peru Puerto Rico  \n> > gdpPercap_1997   9767.3   2253.02  7113.69   4247.4  5838.35     16999.4   
> > gdpPercap_2002  10742.4   2474.55  7356.03  3783.67  5909.02     18855.6   
> > gdpPercap_2007  11977.6   2749.32  9809.19  4172.84  7408.91     19328.7   
> > 
> > country        Trinidad and Tobago United States  Uruguay Venezuela  
> > gdpPercap_1997             8792.57       35767.4  9230.24   10165.5  
> > gdpPercap_2002             11460.6       39097.1     7727   8605.05  
> > gdpPercap_2007             18008.5       42951.7  10611.5   11415.8  
> > ~~~ 
> >{: .output}
> > Nota: podríamos haber hecho lo anterior en una sola línea de código con 'chaining' encadenando los comandos:
> > ~~~
> > americas.T.tail(n=3)
> > ~~~
> >{: .language-python}






> {: .solution}
{: .challenge}

> ## Lectura de archivos en otros directorios
>
> Los datos de su proyecto actual se almacenan en un archivo llamado `microbes.csv`,
> que se encuentra en una carpeta llamada `field_data`.
> Estás haciendo un análisis en un cuaderno llamado `analysis.ipynb`
> en una carpeta llamada `tesis`:
>
> ~~~
> your_home_directory
> +-- field_data/
> |   +-- microbes.csv
> +-- thesis/
>     +-- analysis.ipynb
> ~~~
> {: .output}
>
> ¿Qué valor(es) debe pasar a `read_csv` para leer `microbes.csv` en `analysis.ipynb`?
> 
> > ## Solución
> > Necesitamos especificar la ruta al archivo de interés en la llamada a `pd.read_csv`. Primero necesitamos 'saltar' de
> > la carpeta `tesis` usando '../' y luego en la carpeta` field_data` usando 'field_data /'. Luego podemos especificar el nombre de archivo `microbes.csv.
> > El resultado es el siguiente:
> > ~~~
> > data_microbes = pd.read_csv('../field_data/microbes.csv')
> > ~~~
> >{: .language-python}
> {: .solution}
{: .challenge}

> ## Escritura de datos
> 
> Además de la función `read_csv` para leer datos de un archivo,
> Pandas proporciona una función `to_csv` para escribir dataframes en archivos.
> Aplicando lo que has aprendido sobre la lectura de archivos,
> escriba su dataframe en un archivo llamado `procesado.csv`.
> Puedes usar `help` para obtener información sobre cómo usar` to_csv`.
> > ## Solución
> > Para escribir el DataFrame `americas` en un archivo llamado `processed.csv`, ejecute el siguiente comando:
> > ~~~
> > americas.to_csv('processed.csv')
> > ~~~
> >{: .language-python}
> > Para obtener ayuda sobre `to_csv`, puedes ejecutar, por ejemplo,
> > ~~~
> > help(americas.to_csv)
> > ~~~
> >{: .language-python}
> > Tenga en cuenta que `help (to_csv)` produce un error! Esto es sutil y se debe al hecho de que `to_csv` NO es una función
> > de sí misma sino `americas.to_csv`.
> {: .solution}
{: .challenge}

