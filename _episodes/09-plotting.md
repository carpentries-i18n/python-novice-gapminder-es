---
title: "Visualizando"
teaching: 15
exercises: 15
questions:
- "¿Cómo puedo graficar mis datos?"
- "¿Cómo puedo guardar mi gráfico para publicarlo?"
objectives:
- "Crear un gráfico de serie temporal que muestre un único conjunto de datos."
- "Crear un gráfico de dispersión que muestre la relación entre dos conjuntos de datos."
keypoints:
- "[`matplotlib`](https://matplotlib.org/) es la biblioteca de generación de gráficos científicos más utilizada en Python."
- "Grafica datos directamente desde un **dataframe** de Pandas."
- "Selecciona y transforma datos, luego grafícalos."
- "Muchos estilos de gráfico están disponibles: ve la [Galería de Gráficos de Python](https://python-graph-gallery.com/matplotlib/) para más opciones."
- "Puedes graficar muchos conjuntos de datos juntos."
---
## [`matplotlib`](https://matplotlib.org/) es la biblioteca de graficado científico más utilizada en Python.

* Comúnmente usa una sub-biblioteca llamada [`matplotlib.pyplot`](https://matplotlib.org/api/pyplot_api.html).
* Jupyter Notebook insertará los gráficos en el cuaderno si lo pedimos usando un comando "mágico".

~~~
%matplotlib inline
import matplotlib.pyplot as plt
~~~
{: .language-python}

* Gráficas simples son entonces (bastante) simples de crear.

~~~
time = [0, 1, 2, 3]
position = [0, 100, 200, 300]

plt.plot(time, position)
plt.xlabel('Time (hr)')
plt.ylabel('Position (km)')
~~~
{: .language-python}

![Gráfica simple de Posición-Tiempo]({{ site.baseurl }}/fig/9_simple_position_time_plot.svg)
## Graficar datos directamente desde un [`dataframe` de Pandas](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html).

* También podemos graficar [marcos de datos de Pandas](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html).
* Esto usa implicitamente [`matplotlib.pyplot`](https://matplotlib.org/api/pyplot_api.html).
* Antes de graficar, convertimos las cabeceras de las columnas de una cadena a un tipo de dato entero, siendo que ellos representan valores numéricos.

~~~
import pandas as pd

data = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')

# Extraer el año de los 4 últimos caracteres de cada nombre de columna
# Los nombres de columna actuales están estructurados como 'gdpPercap_(year)', 
# Entonces queremos mantener la parte del año (year) solo para claridad cuando grafiquemos PIB vs. años
# Para hacer esto, usamos strip(), el cual remueve de la cadena los caracteres declarados en el argumento 
# Este método funciona en cadenas, entonces llamamos str antes de strip()
years = data.columns.str.strip('gdpPercap_')

# Convertir los valores del año a enteros, guardando los resultados nuevamente en el marco de datos. 

data.columns = years.astype(int)

data.loc['Australia'].plot()
~~~
{: .language-python}

![Gráfico del PIB de Australia]({{ site.baseurl }}/fig/9_gdp_australia.svg)
## Selecciona y transforma los datos, luego lo graficas.

*   Por defecto, [`DataFrame.plot`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.plot.html#pandas.DataFrame.plot) grafica con las filas como el eje X .
*   Podemos transponer los datos para graficar multiples series.

~~~
data.T.plot()
plt.ylabel('PIB per capita')
~~~
{: .language-python}

![Gráfico del PIB de Australia y Nueva Zelanda]({{ site.baseurl }}/fig/9_gdp_australia_nz.svg)
## Varios estilos de gráficos están disponibles.

*   Por ejemplo, hacer un diagrama de barras usando un estilo mas elegante.

~~~
plt.style.use('ggplot')
data.T.plot(kind='bar')
plt.ylabel('GDP per capita')
~~~
{: .language-python}

![Diagrama de barras del PIB de Australia]({{ site.baseurl }}/fig/9_gdp_bar.svg)

## Los datos pueden ser también graficados llamando a la función `plot` de `matplotlib`  directamente.
*   El comando es `plt.plot(x, y)`
*   El color / formato de los marcadores también pueden ser especificados como un argumento óptico: ejemplo. 'b-' es una linea azul, 'g--' es una linea verde discontinua. 

## Obtener datos de Australia desde el marco de datos

~~~
years = data.columns
gdp_australia = data.loc['Australia']

plt.plot(years, gdp_australia, 'g--')
~~~
{: .language-python}

![Gráfico formateado del PIB para Australia]({{ site.baseurl }}/fig/9_gdp_australia_formatted.svg)

## Se puede trazar varios conjuntos de datos juntos.

~~~
# Selecciona el valor de los datos de dos países.
gdp_australia = data.loc['Australia']
gdp_nz = data.loc['New Zealand']

# Grafica con marcadores de diferentes colores.
plt.plot(years, gdp_australia, 'b-', label='Australia')
plt.plot(years, gdp_nz, 'g-', label='New Zealand')

# Crea leyenda
plt.legend(loc='upper left')
plt.xlabel('Year')
plt.ylabel('GDP per capita ($)')
~~~
{: .language-python}

> ## Añadiendo una leyenda
> 
> A menudo, al trazar múltiples conjuntos de datos en la misma figura, es deseable tener
> una leyenda describiendo los datos.
>
> Esto se puede hacer en `matplotlib` en dos etapas:
> 
> * Provee una etiqueta por cada set de datos en la figura:
>
> ~~~
> plt.plot(years, gdp_australia, label='Australia')
> plt.plot(years, gdp_nz, label='New Zealand')
> ~~~
>
> * Instruye a `matplotlib` para que crea una leyenda.
>
> ~~~
> plt.legend()
> ~~~
>
> Por defecto matplotlib intentara colocar la leyenda en una posición adecuada. Si
> preferirías especificar una posición se podría hacer con el argumento `loc=`, por ejemplo, para colocar
> la leyenda en la esquina superior izquierda de la gráfica, se puede especificar `loc='upper left'`
> {: .language-python}
{: .callout}


![Gráfica formateada del PIB para Australia y Nueva Zelanda]({{ site.baseurl }}/fig/9_gdp_australia_nz_formatted.svg)
* Grafica un diagrama de dispersión que correlacione el PIB de Australia y Nueva Zelanda
* Utiliza `plt.scatter` o `DataFrame.plot.scatter`

~~~
plt.scatter(gdp_australia, gdp_nz)
~~~
{: .language-python}

![Correlación del PIB utilizando plt.scatter]({{ site.baseurl }}/fig/9_gdp_correlation_plt.svg)
~~~
data.T.plot.scatter(x = 'Australia', y = 'New Zealand')
~~~
{: .language-python}

![Correlación del PIB utilizando data.T.plot.scatter]({{ site.baseurl }}/fig/9_gdp_correlation_data.svg)

> ## Mínimo y Máximo
>
> Completa los espacios en blanco a continuación para graficar el PIB mínimo per cápita a lo largo del tiempo
> para todos los países en Europa.
> Modificalo de nuevo para graficar el PIB máximo per cápita a lo largo del tiempo para Europa.
>
> ~~~
> data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
> data_europe.____.plot(label='min')
> data_europe.____
> plt.legend(loc='best')
> plt.xticks(rotation=90)
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > ~~~
> > data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
> > data_europe.min().plot(label='min')
> > data_europe.max().plot(label='max')
> > plt.legend(loc='best')
> > plt.xticks(rotation=90)
> > ~~~
> > {: .language-python}
> > ![Minima Maxima Solución]({{ site.basurl }}/fig/9_minima_maxima_solution.png)
> {: .solution}
{: .challenge}

> ## Correlaciones
>
> Modifica el ejemplo en las notas para crear un diagrama de dispersión que muestre
> la relación entre el PIB mínimo y máximo per cápita
> entre los países de Asia por cada año en el conjunto de datos.
> ¿Qué relación se ve (si es que existe)?
>
> ~~~
> data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
> data_asia.describe().T.plot(kind='scatter', x='min', y='max')
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > ![Correlaciones Solución 1]({{ site.baseurl }}/fig/9_correlations_solution1.svg)
> >
> > No se pueden ver correlaciones particulares entre los valores mínimos y máximos de PIB
> > año a año. Parece que las fortunas de los países asiáticos no suben ni bajan juntas.
> {: .solution}
>
> Puedes notar que la variabilidad en el máximo es mucho mayor que
> la del mínimo. Dale una mirada a los índices maximos y max:
>
> ~~~
> data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
> data_asia.max().plot()
> print(data_asia.idxmax())
> print(data_asia.idxmin())
> ~~~
> {: .language-python}
> > ## Solución
> > ![Correlaciones Solución 2]({{ site.baseurl }}/fig/9_correlations_solution2.png)
> >
> > Parece que la variabilidad en este valor se debe a una fuerte caída después de 1972.
> > ¿Alguna geopolítica en juego quizás? Dado el dominio de los países productores de petróleo,
> > tal vez el índice de crudo Brent haría una comparación interesante?
> > Mientras que Myanmar tiene consistentemente el pib más bajo, la nación con el pib más alto ha variado
> > más notablemente.
> {: .solution}
{: .challenge}

> ## Más Correlaciones
>set
> Este breve programa crea un grsetáfico que muestra
> la correlación entre el PIB y la esperanza de vida para 2007,
> normalizando el tamaño del marcador por población:
>
> ~~~
> data_all = pd.read_csv('data/gapminder_all.csv', index_col='country')
> data_all.plot(kind='scatter', x='gdpPercap_2007', y='lifeExp_2007',
>               s=data_all['pop_2007']/1e6)
> ~~~
> {: .language-python}
>
> Usando ayuda en línea y otros recursos,
> explica lo que hace cada argumento para `plot`.
>
> > ## Solución
> > ![Solución de Más Correlaciones]({{ site.baseurl }}/fig/9_more_correlations_solution.svg)
> >
> > Un buen lugar para buscar es la documentación para la función plot -
> > help(data_all.plot).
> >
> > kind - Como ya se ha visto, esto determina el tipo de gráfico que se dibujará.
> >
> > "x" e "y" - Un nombre de columna o índice que determina qué datos serán
> > colocado en los ejes x e y del gráfico
> >
> > s - Los detalles para esto se pueden encontrar en la documentación de plt.scatter.
> > Un solo número o un valor para cada punto de datos. Determina el tamaño
> > de los puntos graficados.
> {: .solution}
{: .challenge}

> ## Guardando tu gráfico en un archivo
> 
> Si estás satisfecho con el gráfico que se ve, es posible que desees guardarlo en un archivo,
> quizás para incluirlo en una publicación. Hay una función en el
> módulo matplotlib.pyplot que cumple con esto:
> [savefig](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.savefig.html).
> Llamando a esta función, por ejemplo con
> ~~~
> plt.savefig('my_figure.png')
> ~~~
> {: .language-python}
> 
> guardará la figura actual en el archivo `my_figure.png`. El formato de archivo
> se deducirá automáticamente de la extensión del nombre del archivo (otros formatos
> son pdf, ps, eps y svg).
>
> Ten en cuenta que las funciones en `plt` se refieren a una variable de figura global
> y después de que se haya mostrado una figura en la pantalla (por ejemplo, con `plt.show`)
> matplotlib hará que esta variable se referencie a una nueva figura vacía.
> Por lo tanto, asegúrate de llamar a `plt.savefig` antes de mostrar el grafico por
> pantalla, de lo contrario, puedes encontrar un archivo con un gráfico vacío.
>
> Cuando se usan marcos de datos, los datos a menudo se generan y se grafican en la pantalla en una línea,
> y `plt.savefig` no parece ser una método posible.
> Una posibilidad para guardar la figura en el archivo es entonces
>
> * guardar una referencia a la figura actual en una variable local (con `plt.gcf`) 
> * llamar al método de la clase `savefig` desde esa variable
>
> ~~~
> fig = plt.gcf() # Obten la figura actual
> data.plot(kind='bar')
> fig.savefig('my_figure.png')
> ~~~
> {: .language-python}
{: .callout}

> ## Hacer tus gráficas accesibles
>
> Siempre que estes generando gráficos que van en un documento o una presentación, hay algunas cosas que puedes hacer para asegurarte de que todos puedan entender tus diagramas
> * Siempre asegúrate de que tu texto es lo suficientemente grande para leerlo. Usa el parámetro `fontsize` en `xlabel`, `ylabel`, `title`, y `legend`, y [`tick_params` con `labelsize`](https://matplotlib.org/2.1.1/api/_as_gen/matplotlib.pyplot.tick_params.html) para aumentar el tamaño del texto de los números en sus ejes.
> * Del mismo modo, debes hacer que los elementos de tus gráficos sean fáciles de ver. Usa `s` para aumentar el tamaño de los marcadores de tu diagrama de dispersión y `linewidth` para aumentar el tamaño de las líneas del trazado.
> * Usar colores (y nada más) para distinguir entre diferentes elementos del gráfico hará que los trazados sean ilegibles para cualquier persona daltónica o que tenga una impresora en blanco y negro. Para líneas, el parámetro `linestyle` permite utilizar diferentes tipos de líneas. Para diagramas de dispersión, `marker` permite cambiar la forma de los puntos. Si no estás seguro acerca de tus colores, puede usar [Coblis](https://www.color-blindness.com/coblis-color-blindness-simulator/) o [Color Oracle](https://colororacle.org/) para simular cómo se verían tus gráficos para aquellos con daltonismo.
{: .callout}

