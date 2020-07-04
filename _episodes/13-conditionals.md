---
title: "Condicionales"
teaching: 10
exercises: 15
questions:
- "¿Cómo pueden los programas hacer cosas diferentes para datos diferentes?"
objectives:
- "Escribir correctamente los programas que usan declaraciones `if` y `else` y expresiones booleanas simples (sin operadores lógicos)."
- "Rastrear la ejecución de sentencias condicionales no anidados y sentencias condicionales dentro de bucles."
keypoints:
- "Utiliza las declaraciones `if` para controlar si se ejecuta o no un bloque de código."
- "Las sentencias condicionales a menudo se usan dentro de bucles."
- "Usa `else` para ejecutar un bloque de código cuando una condición` if` *no* es verdadera."
- "Usa `elif` para especificar verificaciones adicionales."
- "Las condiciones se verifican una vez, en orden."
- "Crea una tabla que muestre los valores de las variables para rastrear la ejecución de un programa."
---
## Utiliza las declaraciones `if` para controlar si se ejecuta o no un bloque de código.

Una declaración `if` (más propiamente llamada declaración *condicional*)
    controla si algún bloque de código se ejecuta o no.
*   La estructura es similar a una declaración `for`:
    *   La primera línea se abre con `if` y termina con dos puntos
    *   El cuerpo que contiene una o más declaraciones es indentado (generalmente por 4 espacios)

~~~
mass = 3.54
if mass > 3.0:
    print(mass, 'is large')

mass = 2.07
if mass > 3.0:
    print (mass, 'is large')
~~~
{: .language-python}
~~~
3.54 is large
~~~
{: .output}

## Las sentencias condicionales a menudo se usan dentro de bucles.

*   No tiene mucho sentido usar una sentencia condicional cuando conocemos el valor (como arriba).
*   Pero es útil cuando tenemos una colección de datos para procesar.

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 3.0:
        print(m, 'is large')
~~~
{: .language-python}
~~~
3.54 is large
9.22 is large
~~~
{: .output}

## Utiliza `else` para ejecutar un bloque de código cuando una condición` if`  *no* es verdadera.

*  `else` se puede usar después de un` if`.
*   Nos permite especificar una alternativa para ejecutar cuando no se entra en la *rama* `if`.

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 3.0:
        print(m, 'is large')
    else:
        print(m, 'is small')
~~~
{: .language-python}
~~~
3.54 is large
2.07 is small
9.22 is large
1.86 is small
1.71 is small
~~~
{: .output}

## Usa `elif` para especificar verificaciones adicionales.

*   Tal vez desees proporcionar varias opciones alternativas, cada una con su propia verificación.
*   Usa `elif` (abreviatura de" else if ") y una condición para especificarlos.
*   Siempre asociado con un `if`.
*   Debe venir antes de `else` (que "trata todo lo demás").

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 9.0:
        print(m, 'is HUGE')
    elif m > 3.0:
        print(m, 'is large')
    else:
        print(m, 'is small')
~~~
{: .language-python}
~~~
3.54 is large
2.07 is small
9.22 is HUGE
1.86 is small
1.71 is small
~~~
{: .output}

## Las condiciones se verifican una vez, en orden.

*   Python recorre las ramas de las sentencias condicionales en orden, verificando cada una por turno.
*   Por lo que el orden es importante.

~~~
grade = 85
if grade >= 70:
    print('grade is C')
elif grade >= 80:
    print('grade is B')
elif grade >= 90:
    print('grade is A')
~~~
{: .language-python}
~~~
grade is C
~~~
{: .output}

*  *No* retrocede automáticamente y vuelve a evaluar si los valores cambian.

~~~
velocity = 10.0
if velocity > 20.0:
    print('moving too fast')
else:
    print('adjusting velocity')
    velocity = 50.0
~~~
{: .language-python}
~~~
adjusting velocity
~~~
{: .output}

*   A menudo se usa condicionales en un bucle para "evolucionar" los valores de las variables.

~~~
velocity = 10.0
for i in range(5): # execute the loop 5 times
    print(i, ':', velocity)
    if velocity > 20.0:
        print('moving too fast')
        velocity = velocity - 5.0
    else:
        print('moving too slow')
        velocity = velocity + 10.0
print('final velocity:', velocity)
~~~
{: .language-python}
~~~
0 : 10.0
moving too slow
1 : 20.0
moving too slow
2 : 30.0
moving too fast
3 : 25.0
moving too fast
4 : 20.0
moving too slow
final velocity: 30.0
~~~
{: .output}

## Crea una tabla que muestre los valores de las variables para rastrear la ejecución de un programa.

<table>
  <tr>
    <td><strong>i</strong></td>
    <td>0</td>
    <td>.</td>
    <td>1</td>
    <td>.</td>
    <td>2</td>
    <td>.</td>
    <td>3</td>
    <td>.</td>
    <td>4</td>
    <td>.</td>
  </tr>
  <tr>
    <td><strong>velocity</strong></td>
    <td>10.0</td>
    <td>20.0</td>
    <td>.</td>
    <td>30.0</td>
    <td>.</td>
    <td>25.0</td>
    <td>.</td>
    <td>20.0</td>
    <td>.</td>
    <td>30.0</td>
  </tr>
</table>

El programa debe tener una declaración `print` *fuera* del cuerpo del bucle.
para mostrar el valor final de 'velocity',
ya que su valor se actualiza hasta la última iteración del bucle

> ## Relaciones Compuestas Usando `and`,` or`, y Paréntesis
>
> A menudo, quieres alguna combinación de cosas para que la condición sea verdadera. Puedes combinar
> relaciones dentro de un condicional usando `and` y `or`. Continuando con el ejemplo
> arriba, suponga que tienes
>
> ~~~
> mass     = [ 3.54,  2.07,  9.22,  1.86,  1.71]
> velocity = [10.00, 20.00, 30.00, 25.00, 20.00]
>
> i = 0
> for i in range(5):
>     if mass[i] > 5 and velocity[i] > 20:
>         print("Fast heavy object.  Duck!")
>     elif mass[i] > 2 and mass[i] <= 5 and velocity[i] <= 20:
>         print("Normal traffic")
>     elif mass[i] <= 2 and velocity[i] <= 20:
>         print("Slow light object.  Ignore it")
>     else:
>         print("Whoa!  Something is up with the data.  Check it")
> ~~~
> {: .language-python}
>
> Al igual que con la aritmética, debes usar paréntesis siempre que
> se presente una posible ambigüedad. Una buena regla general es *siempre* usar paréntesis
> al mezclar `and` y` or` en la misma condición. Es decir, en lugar de:
>
> ~~~
> if mass[i] <= 2 or mass[i] >= 5 and velocity[i] > 20:
> ~~~
> {: .language-python}
>
> escribe uno de estos:
>
> ~~~
> if (mass[i] <= 2 or mass[i] >= 5) and velocity[i] > 20:
> if mass[i] <= 2 or (mass[i] >= 5 and velocity[i] > 20):
> ~~~
> {: .language-python}
>
> así que es perfectamente claro para un lector (y para Python) lo que realmente quieres decir.
{: .callout}

> ## Rastreo de Ejecución
>
> ¿Qué imprime este programa?
>
> ~~~
> pressure = 71.9
> if pressure > 50.0:
>     pressure = 25.0
> elif pressure <= 50.0:
>     pressure = 0.0
> print(pressure)
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > ~~~
> > 25.0
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Recorte de valores
>
> Complete los espacios en blanco para que este programa cree una nueva lista
> que contenga ceros (0) donde los valores de la lista original eran negativos
> y unos (1) donde los valores de la lista original eran positivos

> ~~~
> original = [-1.5, 0.2, 0.4, 0.0, -1.3, 0.4]
> result = ____
> for value in original:
>     if ____:
>         result.append(0)
>     else:
>         ____
> print(result)
> ~~~
> {: .language-python}
>
> ~~~
> [0, 1, 1, 1, 0, 1]
> ~~~
> {: .output}
> > ## Solución
> >
> > ~~~
> > original = [-1.5, 0.2, 0.4, 0.0, -1.3, 0.4]
> > result = []
> > for value in original:
> >     if value<0.0:
> >         result.append(0)
> >     else:
> >         result.append(1)
> > print(result)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Procesando archivos pequeños
>
> Modifica este programa de manera que solo procese archivos con menos de 50 registros.
>
> ~~~
> import glob
> import pandas as pd
> for filename in glob.glob('data/*.csv'):
>     contents = pd.read_csv(filename)
>     ____:
>         print(filename, len(contents))
> ~~~
> {: .language-python}
> > ## Solución
> >
> > ~~~
> > import glob
> > import pandas as pd
> > for filename in glob.glob('data/*.csv'):
> >     contents = pd.read_csv(filename)
> >     if len(contents)<50:
> >         print(filename, len(contents))
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Iniciando
>
Modifique este programa para que encuentre los valores más altos y más bajos en la lista 
> sin importar cuál sea el rango de valores originalmente.
>
> ~~~
> values = [...some test data...]
> smallest, largest = None, None
> for v in values:
>     if ____:
>         smallest, largest = v, v
>     ____:
>         smallest = min(____, v)
>         largest = max(____, v)
> print(smallest, largest)
> ~~~
> {: .language-python}
>
> ¿Cuáles son las ventajas y desventajas de usar este método
> para encontrar el rango de los datos?
> > ## Solución
> >
> > ~~~
> > values = [-2,1,65,78,-54,-24,100]
> > smallest, largest = None, None
> > for v in values:
> >     if smallest==None and largest==None:
> >         smallest, largest = v, v
> >     else:
> >         smallest = min(smallest, v)
> >         largest = max(largest, v)
> > print(smallest, largest)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Uso de Funciones con Condicionales en Pandas
>
> Las funciones a menudo contienen condicionales. Aquí hay un breve ejemplo que
> indicará en qué cuartil se encuentra el argumento basado en valores codificados a mano
> para los puntos de corte del cuartil.
>
> ~~~
> def calculate_life_quartile(exp):
>     if exp < 58.41:
>         # This observation is in the first quartile
>         return 1
>     elif exp >= 58.41 and exp < 67.05:
>         # This observation is in the second quartile
>        return 2
>     elif exp >= 67.05 and exp < 71.70:
>         # This observation is in the third quartile
>        return 3
>     elif exp >= 71.70:
>         # This observation is in the fourth quartile
>        return 4
>     else:
>         # This observation has bad data
>        return None
>
> calculate_life_quartile(62.5)
> ~~~
> {: .language-python}
>
> ~~~
> 2
> ~~~
> {: .output}
>
> Esa función normalmente se usaría dentro de un bucle `for`, pero Pandas tiene
> una forma diferente y más eficiente de hacer lo mismo, y eso es mediante
> *aplicando* una función a un **dataframe** o una parte de ello. El siguiente
> ejemplo, usa la definición anterior.
> ~~~
> data = pd.read_csv('Americas-data.csv')
> data['life_qrtl'] = data['lifeExp'].apply(calculate_life_quartile)
> ~~~
> {: .language-python}
>
> Hay mucho en esa segunda línea, así que vamos a tomarlo pieza por pieza.
> En el lado derecho de `=` comenzamos con `data ['lifeExp']`, que es la
> columna en el **dataframe** llamado `data` con la etiqueta` lifExp`. Usamos el
> `apply()` para hacer lo que dice, aplique el 'calculate_life_quartile` al
> valor de esta columna para cada fila en el **dataframe**.
{: .callout}

