---
title: "Escribiendo Funciones"
teaching: 10
exercises: 15
questions:
- "¿Cómo puedo crear mis funciones?"
objectives:
- "Explicar e identificar la diferencia entre definir una función y el llamado de una función."
- "Escribe una función que toma un número de argumentos fijo y pequeño, y produce un sólo resultado."
keypoints:
- "Divide los programas en funciones para hacerlos mas entendibles o mas fácil de interpretar."
- "Define una función usando `def` con nombre, parámetros, y código en bloque."
- "Defining a function does not run it."
- "Los argumentos en una llamada corresponden a los parametros en la definición."
- "Las funciones pueden devolver un resultado, a quienes las invocan (llaman) usando `return`."
---
## Dividir los programas en funciones para que sean mas fácil de entender.

*    Las personas pueden mantener unos pocos elementos en la memoria de trabajo, cada vez que lo hacen.
*   Comprender ideas más grandes / más complicadas y saber combinar o relacionar las partes.
    *   Componentes en una computadora.
    *   Ideas al probar teoremas.
*   Las funciones tienen el mismo propósito en los programas.
    *   *Encapsular* reducir la complejidad para que podamos tratarlo como una sola "cosa". 
*   También facilita el *re-uso*.
    *   Se escribe una vez, se usa muchas veces.

## Definir una función usando `def` con nombre, parámetros y bloque de código.

*   Empieza o inicia la definición de una nueva función con`def`.
*   Seguido por el nombre de la función.
    *   Debe respetar las normas de los nombres de las variables.
    *     Entonces los parámetros / argumentos van entre paréntesis.
    *    Paréntesis vacíos, si la función no toma ningún argumento.
    *    Discutiremos en detalle en un momento
    *    Después un punto y coma.
    *    Después un bloque de código identado.

~~~ 
def mostrar_saludos(): 
    print ('¡Hola!') 
~~~
{: .language-python}

## Definir una función, no significa que esta se ejecuta.

* La definición de una función no la ejecuta.
* Como asignar un valor en una variable.
* Debes llamar a la función para ejecutar el código que contiene.

~~~
mostrar_saludo()
~~~
{: .language-python}
~~~
¡Hola!
~~~
{: .output}

## Los argumentos en la llamada corresponden a los parámetros de la definición.

*  Las funciones son más efectivas cuando pueden operar sobre datos diferentes.
*  Especificar *parámetros* al definir una función.
*  Estos se convierten en variables cuando se ejecuta la función.
* Se asignan los argumentos en la llamada (es decir, los valores se pasan ​​a la función).
* Si no invoca los argumentos cuando los usa en la llamada, los argumentos se compararán con los
parámetros en el orden definido en la función.

~~~ 
def mostrar_fecha (year, mes, día): 
    unido = str (year) + '/' + str (mes) + '/' + str (dia) 
    print (unido) 

mostrar_fecha (1871, 3, 19) 
~~~
{: .language-python}
~~~
1871/3/19
~~~
{: .output}

O bien, podemos nombrar los argumentos cuando llamamos a la función, lo que nos permite
especificarlos en cualquier orden:
~~~
print_date(mes=3, dia=19, year=1871)
~~~
{: .language-python}
~~~
1871/3/19
~~~
{: .output}

*   Via [Twitter](https://twitter.com/minisciencegirl/status/693486088963272705):
    `()` contiene las componentes de la función
    mientras el cuerpo contiene la fórmula.

## Las funciones pueden devolver un resultado a quien la llama usando `return`.

*   Usa `return` para devolver el valor.
*  Puede ocurrir en cualquier parte de la función.
*   Pero las funciones son más fácil de entender si tienen un `return`:
* Al principio para manejar casos especiales.
 * Al final, con un resultado final.

~~~
def average(valores):
    if len(valores) == 0:
        return None
    return sum(valores) / len(valores)
~~~
{: .language-python}

~~~
a = average([1, 3, 4])
print('promedio de valores:', a)
~~~
{: .language-python}
~~~
promedio de valores: 2.6666666666666665
~~~
{: .output}

~~~
print('promedio de la lista vacía:', average([]))
~~~
{: .language-python}
~~~
promedio de la lista vacía: None
~~~
{: .output}

*   Recuerda: [toda función devuelve algo]({{ page.root }}/04-built-in/).
*   Una función que no devuelve un valor explícitamente `devuelve` automáticamente `None`.

~~~
resultado = print_date(1871, 3, 19)
print('resultado de la llamada es:', resultado)
~~~
{: .language-python}
~~~
1871/3/19
resultado de la llamada es: None
~~~
{: .output}

> ## Identificación de errores de sintaxis
>
> 1. Lee el código a continuación e intente identificar cuáles son los errores
>     *sin* ejecutarlo.
> 2. Corre el código y lee el mensaje de error.
>    Es un `SyntaxError` o un `IndentationError`?
> 3. Corrige el error.
> 4. Repite los pasos 2 y 3 hasta que hasta que haya solucionado todos los errores.
>
> ~~~
> def another_function
>   print("Los errores de sintaxis son molestos.")
>    print("¡Pero al menos Python nos cuenta sobre ellos!")
>   print("Generalmente no son demasiado difíciles de arreglar.")
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > ~~~
> > def another_function():
> >   print("Los errores de sintaxis son molestos.")
> >   print("¡Pero al menos Python nos cuenta sobre ellos!")
> >   print("Generalmente no son demasiado difíciles de arreglar.")
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Definición y Uso
>
> ¿Qué muestra el siguiente programa?
>
> ~~~
> def report(presion):
>     print('presion es', presion)
>
> print('llamado', report, 22.5)
> ~~~
> {: .language-python}
> > ## Solución
> >
> > ~~~
> > calling <function report at 0x7fd128ff1bf8> 22.5
> > ~~~ 
> > {: .output}
> >
> > La llamada a una función siempre necesita paréntesis, de lo contrario, obtiene la dirección de memoria del objeto función. Entonces, si queremos llamar a la función de nombre report, y le damos el valor 22.5, podríamos tener la llamada a la función de la siguiente manera
> > ~~~
> > print("llamada")
> > report(22.5)
> > ~~~
> {: .solution}
{: .challenge}


> ## Orden de Operaciones
>
> El ejemplo anterior:
>
> ~~~
> resultado = print_date(1871, 3, 19)
> print('resultado de la llamada es:', resultado)
> ~~~
> {: .language-python}
>
> muestra:
> ~~~
> 1871/3/19
> resultado de la llamada es: None
> ~~~
> {: .output}
>
> Explica por qué las dos líneas de salida aparecieron en el orden en que lo hicieron.
>
> ¿Qué hay de malo en este ejemplo?
> ~~~
> resultado = print_date(1871,3,19)
>
> def print_date(year, mes, dia):
>    joined = str(year) + '/' + str(mes) + '/' + str(dia)
>    print(joined)
> ~~~
> {: .language-python}
> 
> > ## Solution
> > 
> > 1. La primer línea de salida (`1871/3/19`) es lo que muestra la función dentro de `print_date()`, mientras que la segunda línea
> > lo que muestra está debajo de la llamadaa la función. Todo el código dentro de `print_date ()` se ejecuta primero, y
> > el programa luego "deja" la función y ejecuta el resto del código. 
> > 2. El problema con el ejemplo es que la función se define * después de * que se realiza la llamada a la función. Python
> > por lo tanto no entiende la llamada a la función.
> {: .solution}
{: .challenge}

> ## Encapsulamiento
>
> Completa los espacios en blanco para crear una función que tome un nombre de archivo como argumento,
> cargue los datos de ese archivo pasado como argumento,
> y devuelva el mínimo valor de esos datos.
>
> ~~~
> import pandas as pd
>
> def min_in_data(____):
>     data = ____
>     return ____
> ~~~
> {: .language-python}
> > ## Solución
> >
> > ~~~
> > import pandas as pd
> > 
> > def min_in_data(filename):
> >     data = pd.read_csv(filename)
> >     return data.min()
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Encuentra el primero
>
> Completa los espacios en blanco para crear una función que tome una lista de números como argumento
> y devuelva el primer valor negativo en la lista.
> ¿Qué hace su función si la lista está vacía?
>
> ~~~
> def first_negative(valores):
>     for v in ____:
>         if ____:
>             return ____
> ~~~
> {: .language-python}
> > ## Solution
> >
> > ~~~
> > def first_negative(valores):
> >     for v in valores:
> >         if v<0:
> >             return v
> > ~~~
> > {: .language-python}
> > Si se pasa una lista vacía a esta función, devuelve `None`:
> > ~~~
> > my_list = []
> > print(first_negative(my_list))
> > ~~~
> > {: .language-python}
> > ~~~
> > None
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Llamando por nombre
>
> Anteriormente vimos esta función:
>
> ~~~
> def print_date(year, mes, dia):
>     joined = str(year) + '/' + str(mes) + '/' + str(dia)
>     print(joined)
> ~~~
> Vimos que podemos llamar a la función usando *argumentos con nombres*, así:
> ~~~
> print_date(dia=1, mes=2, year=2003)
> ~~~
> {: .language-python}
>
> 1.  ¿Qué muestra`print_date (dia = 1, mes = 2, year = 2003)`?
> 2.  ¿Cuándo has visto una llamada a una función como esta antes?
> 3.  ¿Cuándo y por qué es útil llamar a las funciones de esta manera?
> {: .language-python}
> > ## Solution
> > 
> > 1. `2003/2/1`
> > 2. Vimos ejemplos de uso de *argumentos con nombre* al trabajar con la biblioteca de Pandas. Por ejemplo, al leer en un conjunto de datos 
> > using `data = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')`, el último argumento `index_col` es un 
> > nombre de argumento.  
> > 3. El uso de argumentos con nombre puede hacer que el código sea más legible ya que uno puede ver desde la llamada de función qué nombre tienen los diferentes argumentos  
> > dentro de la función. También puede reducir las posibilidades de pasar argumentos en el orden incorrecto, ya que al usar argumentos con nombre 
> > el orden no importa.
> {: .solution}
{: .challenge}

> ## Encapsular un bloque de If/Print
>
> El siguiente código se ejecutará en una impresora de etiquetas para huevos de gallina. Una balanza digital informará una masa de huevo de gallina (en gramos) a la computadora y luego la computadora imprimirá una etiqueta.
>
> Vuelve a escribir el código para que el bloque if se despliegue en una función.
>
> ~~~
>  import random
>  for i in range(10):
>
>     # simulando la masa de un huevo de gallina
>     # la masa (random) será 70 +/- 20 gramos
>     masa=70+20.0*(2.0*random.random()-1.0)
>
>     print(masa)
>    
>     #la maquinaria de dimensionamiento de huevos imprime una etiqueta
>     if(masa>=85):
>        print("super")
>     elif(masa>=70):
>        print("grande")
>     elif(masa<70 and mass>=55):
>        print("medio")
>     else:
>        print("pequeño")
> ~~~
> {: .language-python}
>
>
> El programa sigue. ¿Qué definición de función lo hará funcional?
>
> ~~~
>  # versión revisada
>  import random
>  for i in range(10):
>
>     # simulando la masa de un huevo de gallina
>     # la masa (random) será 70 +/- 20 gramos
>     masa=70+20.0*(2.0*random.random()-1.0)
>
>     print(masa,print_egg_label(masa))    
>
> ~~~
> {: .language-python}
>
>
> 1. Crea una definición de función para `print_egg_label ()` que funcionará con el programa anterior. Ten en cuenta que el valor de retorno de la función sea significativo. La salida puede ser '71.23 grande'.
> 2.  Un huevo sucio puede tener una masa de más de 90 gramos, y un huevo estropeado o roto probablemente tendrá una masa de menos de 50 gramos. Modifica tu función `print_egg_label ()` para tener en cuenta estas condiciones de error. La salida podría ser '25 demasiado ligera, probablemente estropeada'.
>
> > ## Solución
> >
> > ~~~
> > def print_egg_label(masa):
> >     #la maquinaria de dimensionamiento de huevos imprime una etiqueta
> >     if(masa>=90):
> >         return("cuidado: el huevo debe estar sucio")
> >     elif(masa>=85):
> >         return("super")
> >     elif(masa>=70):
> >         return("grande")
> >     elif(masa<70 and mass>=55):
> >         return("mediano")
> >     elif(masa<50):
> >         return("Demasiado ligero, probablemente roto")
> >     else:
> >         return("pequenio")
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Encapsulando Análisis de Datos
>
> Suponga que se ha ejecutado el siguiente código:
>
> ~~~
> import pandas as pd
>
> df = pd.read_csv('data/gapminder_gdp_asia.csv', index_col=0)
> japan = df.loc['Japan']
> ~~~
> {: .language-python}
>
> 1. Complete las siguientes declaraciones para obtener el PIB promedio de Japón
> a través de los años reportados para la década de 1980.
>
> ~~~
> year= 1983
> gdp_decada = 'gdpPercap_' + str(year // ____)
> prom = (japan.loc[gdp_decada + ___] + japan.loc[gdp_decada + ___]) / 2
> ~~~
> {: .language-python}
>
> 2.Resuma el código anterior en una sola función.
>
> ~~~
> def prom_gdp_in_decada(pais, continente, year):
>     df = pd.read_csv('data/gapminder_gdp_'+___+'.csv',delimiter=',',index_col=0)
>     ____
>     ____
>     ____
>     return prom
> ~~~
> {: .language-python}
>
> 3.¿Cómo generalizarías esta función
>   si no sabes de antemano qué años específicos ocurrieron como columnas de datos?
>    Por ejemplo, ¿qué pasaría si también tuviéramos datos de años que terminan en 1 y 9 para cada década?
>   (Sugerencia: use las columnas para filtrar las que corresponden a la década,
>    en lugar de enumerarlos en el código).
>
> > ## Solución
> >
> > 1.
> >
> > ~~~
> > year= 1983
> > gdp_decada = 'gdpPercap_' + str(year// 10)
> > prom = (japan.loc[gdp_decada + '2'] + japan.loc[gdp_decada + '7']) / 2
> > ~~~
> > {: .language-python}
> >
> > 2.
> >
> > ~~~
> > def prom_gdp_in_decada(pais, continente, year):
> >     df = pd.read_csv('data/gapminder_gdp_' + continente + '.csv', index_col=0)
> >     c = df.loc[pais]
> >     gdp_decada = 'gdpPercap_' + str(year// 10)
> >     prom = (c.loc[gdp_decada + '2'] + c.loc[gdp_decada + '7'])/2
> >     return prom
> > ~~~
> > {: .language-python}
> >
> > 3.
> > 
> > Necesitamos recorrer los años reportados
> >    para obtener el promedio de los relevantes en los datos.
> >
> > ~~~
> > def prom_gdp_in_decada(pais, continente, year):
> >     df = pd.read_csv('data/gapminder_gdp_' + continente+ '.csv', index_col=0)
> >     c = df.loc[pais]
> >     gdp_decada = 'gdpPercap_' + str(year// 10)
> >     total = 0.0
> >     num_anios = 0
> >     for yr_header in c.index: # el índice de c contiene años reportados
> >         if yr_header.startswith(gdp_decada):
> >             total = total + c.loc[yr_header]
> >             num_anios = num_year + 1
> >     return total/num_year
> > ~~~
> > {: .language-python}
> > La función puede ahora llamarse asi:
> > ~~~
> > prom_gdp_in_decada('Japan','Asia',1983)
> > ~~~
> > {: .language-python}
> > 
> > ~~~
> > 20880.023800000003
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Simulando un sistema dinámico
>
> En Matemática, un [sistema dinámico](https://en.wikipedia.org/wiki/Dynamical_system) es el sistema en el que una función describe la dependencia del tiempo de un punto en un espacio geométrico.  Un ejemplo canónico de un sistema dinámico es un sistema llamado [mapa logístico](https://en.wikipedia.org/wiki/Logistic_map).
>
>
> 1. Define una función llamada `logistic_map` que tome dos entradas:` x`, que representa el estado del sistema en el tiempo _t_, y un parámetro `r`. Esta función deberá devolver un valor que represente el estado del sistema en el momento _t + 1_.
>
> 2. Usa un bucle `for`, itera la función `logistic_map` definida en la parte 1 a partir de una condición inicial de 0.5 para los períodos `t_final = 10`,` 100` y `1000`. Almacena los resultados intermedios en una lista para que, después de que finalice el ciclo `for`, haya acumulado una secuencia de valores que representan el estado del mapa logístico en el tiempo _t = 0,1, ..., t_final_.
>
> 3. Encapsula la lógica de tu bucle `for` en una función llamada `iterar` que toma la condición inicial como su primera entrada, el parámetro `t_final` como su segunda entrada y el parámetro` r` como su tercera entrada. La función debe devolver la lista de valores que representan el estado del mapa logístico en el tiempo _t = 0,1, ..., t_final_.
>
>
> > ## Solución
> >
> > 1.
> >
> > ~~~
> > def logistic_map(x, r):
> >     return r * x * (1 - x)
> > ~~~
> > {: .language-python}
> >
> > 2.
> >
> > ~~~
> > initial_condition = 0.5
> > t_final = 10
> > r = 1.0
> > trayectoria= [initial_condition]
> > for t in range(1, t_final):
> >     trayectoria.append( logistic_map(trayectoria[t-1], r) )
> > ~~~
> > {: .language-python}
> >
> > 3.
> > ~~~
> > def iterar(initial_condition, t_final, r):
> >     trayectoria = [initial_condition]
> >     for t in range(1, t_final):
> >         trayectoria.append( logistic_map(trajectory[t-1], r) )
> >     return trayectoria
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

