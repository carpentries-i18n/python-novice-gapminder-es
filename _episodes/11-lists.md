---
title: "Listas"
teaching: 10
exercises: 10
questions:
- "¿Cómo puedo almacenar múltipes valores?"
objectives:
- "Explicar por qué los programas necesitan colecciones de valores."
- "Escribir programa para crear listas, ordenarlas, dividirlas y modificarlas a través de asignaciones y métodos."
keypoints:
- "Una lista almacena muchos valores en una única estructura."
- "Usa el índice de un elemento para buscarlo en una lista."
- "Los valores de las listas se pueden reemplazar asignando nuevos valores."
- "Agregar elementos a una lista la alarga."
- "Usa `del` para eliminar elementos de una lista."
- "La lista vacía no contiene valores."
- "Las listas pueden contener valores de diferentes tipos."
- "Las cadenas de caracteres se pueden indexar como listas."
- "Las cadenas de caracteres son inmutables."
- "La indexación más allá del final de la colección es un error."
---
## Una lista almacena muchos valores en una única estructura.

*  Hacer cálculos con 100 variables llamadas `pressure_001`, `pressure_002`, etc.,
   sería al menos tan lento como hacerlo a mano.
*  Usa una *lista* para almacenar muchos valores juntos.
    *  Contenidos entre corchetes `[...]`.
    *  Valores separados por comas `,`.
*  Usa `len` para averiguar cuántos valores hay en una lista.

~~~
pressures = [0.273, 0.275, 0.277, 0.275, 0.276]
print('pressures:', pressures)
print('length:', len(pressures))
~~~
{: .language-python}
~~~
pressures: [0.273, 0.275, 0.277, 0.275, 0.276]
length: 5
~~~
{: .output}

## Usa el índice de un elemento para buscarlo en una lista.

*   Como en las secuencias de caracteres.

~~~
print('elemento cero de pressures:', pressures[0])
print('cuarto elemento de pressures:', pressures[4])
~~~
{: .language-python}
~~~
elemento cero de pressures: 0.273
cuarto elemento de pressures: 0.276
~~~
{: .output}

## Los valores de las listas se pueden reemplazar asignándole un nuevo valor.

*   Usa un índice a la izquierda de la asignación para reemplazar un valor.

~~~
pressures[0] = 0.265
print('pressures es ahora:', pressures)
~~~
{: .language-python}
~~~
pressures es ahora: [0.265, 0.275, 0.277, 0.275, 0.276]
~~~
{: .output}

## Agregar elementos a una lista la alarga.

*   Usa `list_name.append` para agregar elementos al final de una lista.

~~~
primes = [2, 3, 5]
print('primes inicialmente es:', primes)
primes.append(7)
primes.append(9)
print('primes ahora es :', primes)
~~~
{: .language-python}
~~~
primes inicialmente es: [2, 3, 5]
primes ahora es : [2, 3, 5, 7, 9]
~~~
{: .output}

*   `append` es un *método* de las listas.
    *   Como una función, pero vinculada a un objeto particular.
*   Usa `object_name.method_name` para llamar métodos.
    *   Deliberadamente se asemeja a la forma en que nos referimos a las cosas en una biblioteca.
*   Encontraremos otros métodos de las listas a medida que avancemos.
    *   Usa `help(list)` para ver un avance.
*   `extend` es similar a `append`, pero permite combinar dos listas. Por ejemplo:

~~~
teen_primes = [11, 13, 17, 19]
middle_aged_primes = [37, 41, 43, 47]
print('primes es:', primes)
primes.extend(teen_primes)
print('ahora primes es:', primes)
primes.append(middle_aged_primes)
print('finalmente primes es:', primes)
~~~
{: .language-python}
~~~
primes es: [2, 3, 5, 7, 9]
primes ahora primes es: [2, 3, 5, 7, 9, 11, 13, 17, 19]
finalmente primes es: [2, 3, 5, 7, 9, 11, 13, 17, 19, [37, 41, 43, 47]]
~~~
{: .output}

Ten en cuenta que si bien `extend` mantiene la estructura "plana" de la lista, agregar una lista a una lista produce el resultado bidimensional: el último elemento en 'primes' es una lista, no un entero.

## Usa `del` para remover elementos de una lista.

*   `del list_name[index]` remueve un elemento de una lista y la acorta.
*  No es una función o un método, es una sentencia del lenguaje.

~~~
primes = [2, 3, 5, 7, 9]
print('primes antes de remover el último elemento:', primes)
del primes[4]
print('primes después de remover el último elemento:', primes)
~~~
{: .language-python}
~~~
primes antes de remover el último elemento: [2, 3, 5, 7, 9]
primes después de remover el último elemento: [2, 3, 5, 7]
~~~
{: .output}

## La lista vacía no contiene valores.

*   Usa `[ ]` para representar una lista que no contiene ningún valor.
    *   "El cero de las listas."
*   Útil como punto de partida para recolectar valores.
        (que veremos en el [próximo episodio]({% link _episodes/12-for-loops.md %}).

## Las listas pueden contener valores de diferentes tipos.

*   Una única lista puede contener números, cadenas y cualquier otra cosa.

~~~
goals = [1, 'Create lists.', 2, 'Extract items from lists.', 3, 'Modify lists.']
~~~
{: .language-python}

## Las secuencias de caracteres pueden indexarse de la misma manera que las listas.

*   Obtén caracteres individuales de una secuencia de caracteres utilizando índices entre corchetes.

~~~
element = 'carbon'
print('carácter cero:', element[0])
print('tercer carácter:', element[3])
~~~
{: .language-python}
~~~
carácter cero: c
tercer carácter: b
~~~
{: .output}

## Las secuencias de caracteres son inmutables.

*   No se pueden cambiar los caracteres de una secuencia de caracteres después de que se haya creado.
    *   *Inmutable*: no se puede cambiar luego de su creación.
    *   Por el contrario, las listas son *mutables*: se pueden modificar.
*   Python considera la secuencia de caracteres como un único valor con partes,
no una colección de valores.

~~~
element[0] = 'C'
~~~
{: .language-python}
~~~
TypeError: 'str' object does not support item assignment
~~~
{: .error}

*   Las listas y las secuencias de caracteres son *colecciones*.

## Indexar más allá del final de una colección es un error.

*   Python reporta un `IndexError` si intentamos acceder a un valor que no existe.
    *   Este es un tipo de [error de ejecución]({{ page.root }}/04-built-in/#runtime-error).
    *   No se puede detectar mientras se analiza el código
        porque el índice podría calcularse en función de los datos.

~~~
print('El elemento número 99 es:', element[99])
~~~
{: .language-python}
~~~
IndexError: string index out of range
~~~
{: .output}

> ## Rellena los espacios en blanco
>
> Rellena los espacios en blanco para que el programa produzca el resultado mostrado.
>
> ~~~
> values = ____
> values.____(1)
> values.____(3)
> values.____(5)
> print('primera vez:', values)
> values = values[____]
> print('segunda vez:', values)
> ~~~
> {: .language-python}
>
> ~~~
> primera vez: [1, 3, 5]
> segunda vez: [3, 5]
> ~~~
> {: .output}
>
> > ## Solución
> > ~~~
> > values = []
> > values.append(1)
> > values.append(3)
> > values.append(5)
> > print('primera vez:', values)
> > values = values[1:]
> > print('segunda vez:', values)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## ¿Qué tan grande es un corte?
>
> Si 'low' y 'high' son dos enteros no-negativos,
> ¿qué tan grande es la lista `values[low:high]`?
>
> > ## Solución
> > La lista `values[low:high]` tiene `high - low` elementos.  Por ejemplo,
> > `values[1:4]` tiene 3 elementos `values[1]`, `values[2]`, y `values[3]`.
> > Nota que la expresión sólo funciona si `high` es menor que la longitud
> > total de `valores` de la lista.
> {: .solution}
{: .challenge}

> ## De Secuencias de caracteres a Listas y Viceversa
>
> Dado esto:
>
> ~~~
> print('cadena a lista:', list('tin'))
> print('lista a cadena:', ''.join(['g', 'o', 'l', 'd']))
> ~~~
> {: .language-python}
> ~~~
> ['t', 'i', 'n']
> 'gold'
> ~~~
> {: .output}
>
> 1.  ¿Qué hace `list('cadena')`?
> 2.  ¿Qué genera `'-'.join(['x', 'y', 'z'])`?
>
> > ## Solución
> > 1. [`list('cadena')`](https://docs.python.org/3/library/stdtypes.html#list) convierte una secuencia de caracteres en una lista que contiene todos los caracteres.
> > 2. [`join`](https://docs.python.org/3/library/stdtypes.html#str.join) devuelve una secuencia de caracteres que es una _concatenación_
> >    de cada elemento de la secuencia en la lista y añade un separador entre elementos en la lista. Esto resulta
> >    `x-y-z`. El separador entre los elementos es el que provee el método.
> {: .solution}
{: .challenge}

> ## Trabajando con el Final
>
> ¿Qué muestra el siguiente programa?
>
> ~~~
> element = 'helium'
> print(element[-1])
> ~~~
> {: .language-python}
>
> 1.  ¿Cómo interpreta Python un índice negativo?
> 2.  Si una lista o secuencia de caracteres de N elementos,
>     ¿cuál es el índice más negativo que se puede usar,
>     y qué posición representa este índice?
> 3.  Si `values` es una lista, ¿qué hace `del values[-1]`?
> 4.  ¿Cómo se puede mostrar todos los elementos sin cambiar `values`?
>     (Consejo: necesitas combinar cortes e índices negativos.)
>
> > ## Solución
> > El programa muestra `m`.
> > 1. Python interpreta un índice negativo como empezar desde el final (en lugar de
> >    empezar desde el inicio).  El último elemento es `-1`.
> > 2. El último índice que se puede usar con seguridad en una lista de N elementos es el elemento
> >    `-N`, que representa el primer elemento.
> > 3. `del values[-1]` remueve el último elemento de la lista.
> > 4. `values[:-1]`
> {: .solution}
{: .challenge}

> ## Recorriendo una Lista
>
> ¿Qué muestra el siguiente programa?
>
> ~~~
> element = 'fluorine'
> print(element[::2])
> print(element[::-1])
> ~~~
> {: .language-python}
>
> 1.  Si escribimos un corte como `low:high:stride`, ¿qué hace `stride`?
> 2.  ¿Qué expresión seleccionaría todos los elementos pares de una colección?
>
> > ## Solución
> > El programa muestra
> > ~~~
> > furn
> > eniroulf
> > ~~~
> > {: .language-python}
> > 1. `stride` es el tamaño del paso del corte
> > 2. El corte `1::2` selecciona todos los elementos pares de una colección: empieza
> >    con el elemento `1` (que es el segundo elemento, ya que la indexación empieza en `0`),
> >    va hasta el final (ya que no se usó `end`), y usa un paso de `2`
> >    (es decir, selecciona cada dos elementos).
> {: .solution}
{: .challenge}

> ## Límites de los Cortes
>
> ¿Qué muestra el siguiente programa?
>
> ~~~
> element = 'lithium'
> print(element[0:20])
> print(element[-1:3])
> ~~~
> {: .language-python}
>
> > ## Solución
> > ~~~
> > lithium
> > 
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Sort y Sorted
>
> ¿Qué muestran estos dos programas?
> Explica la diferencia entre `sorted(letters)` y `letters.sort()` en términos simples.
>
> ~~~
> # Programa A
> letters = list('gold')
> result = sorted(letters)
> print('letters es', letters, 'y result es', result)
> ~~~
> {: .language-python}
>
> ~~~
> # Programa B
> letters = list('gold')
> result = letters.sort()
> print('letters es', letters, 'y result es', result)
> ~~~
> {: .language-python}
>
> > ## Solución
> > El programa A muestra
> > ~~~
> > letters es ['g', 'o', 'l', 'd'] y result es ['d', 'g', 'l', 'o']
> > ~~~
> > {: .language-python}
> > El program B muestra
> > ~~~
> > letters es ['d', 'g', 'l', 'o'] y result es None
> > ~~~
> > {: .language-python}
> > `sorted(letters)` devuelve una copia ordenada de  la lista `letters` (la lista
> > original `letters` permanece sin cambios), mientras que `letters.sort()` ordena la lista
> > `letters` en si misma y no devuelve nada.
> {: .solution}
{: .challenge}

> ## Copiar (o no copiar)
>
> ¿Qué muestran estos dos programas?
> Explica la diferencia entre `new = old` y `new = old[:]` en términos simples.
>
> ~~~
> # Programa A
> old = list('gold')
> new = old      # asignación simple
> new[0] = 'D'
> print('new es', new, 'y old es', old)
> ~~~
> {: .language-python}
>
> ~~~
> # Programa B
> old = list('gold')
> new = old[:]   # asignación de un corte
> new[0] = 'D'
> print('new es', new, 'y old es', old)
> ~~~
> {: .language-python}
>
> > ## Solución
> > El programa A muestra
> > ~~~
> > new es ['D', 'o', 'l', 'd'] y old es ['D', 'o', 'l', 'd']
> > ~~~
> > El programa B muestra
> > ~~~
> > new es ['D', 'o', 'l', 'd'] y old es ['g', 'o', 'l', 'd']
> > ~~~
> > {: .language-python}
> > `new = old` crea una referencia a la lista `old`; `new` y `old` apuntan
> > al mismo objeto.
> > 
> > `new = old[:]`, sin embargo, crea una nueva lista `new` con todos los elementos
> > de la lista `old`; `new` y `old` son dos objetos diferentes.
> {: .solution}
{: .challenge}

