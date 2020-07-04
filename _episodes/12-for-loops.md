---
title: "Bucles For"
teaching: 10
exercises: 15
questions:
- "¿Cómo puedo hacer que un programa haga muchas cosas?"
objectives:
- "Explicar para qué se usan normalmente los bucles for."
- "Rastrear la ejecución de un bucle simple (no anidado) e indicar correctamente los valores de las variables en cada iteración."
- "Escribir bucles for que usan el patrón del Acumulador para agregar valores."
keypoints:
- "Un *bucle for* ejecuta comandos una vez para cada valor en una colección."
- "Un bucle `for` se compone de una colección, una variable de bucle y un cuerpo."
- "La primera línea del bucle `for` debe terminar con dos puntos, y el cuerpo debe ser indentado."
- "La indentación siempre es significativa en Python."
- "Las variables de bucle se pueden llamar de cualquier forma (pero se recomienda encarecidamente tener un nombre significativo para la variable de bucle)."
- "El cuerpo de un bucle puede contener muchas instrucciones."
- "Usa `range` para iterar sobre una secuencia de números."
- "El patrón Acumulador convierte muchos valores en uno."
---
##  Un *bucle for* ejecuta comandos una vez para cada valor en una colección.

* Hacer cálculos sobre los valores en una lista uno por uno
es tan incómodo como trabajar con `pressure_001`, `pressure_002`, etc.
* Un *bucle for* le dice a Python que ejecute algunas instrucciones una vez por cada valor de una lista,
una secuencia de caracteres,
 o alguna otra colección.
* "para cada cosa en este grupo, realiza estas operaciones"

~~~
for number in [2, 3, 5]:
    print(number)
~~~
{: .language-python}

* Este bucle `for` es equivalente a:

~~~
print(2)
print(3)
print(5)
~~~
{: .language-python}

* Y la salida del bucle `for` es:

~~~
2
3
5
~~~
{: .output}

## Un bucle `for` se compone de una colección, una variable de control y un cuerpo.

~~~
for number in [2, 3, 5]:
    print(number)
~~~
{: .language-python}

* La colección, `[2, 3, 5]`, es sobre lo que se está ejecutando el bucle.
* El cuerpo, `print (number)`, especifica qué hacer para cada valor en la colección.
* La variable de control, `number`, es lo que cambia para cada *iteración* del bucle.
* El "valor actual de la variable".

## La primera línea del bucle `for` debe terminar con dos puntos, y el cuerpo debe estar indentado.

* Los dos puntos al final de la primera línea indican el inicio de un *bloque* de instrucciones.
* Python usa indentación en lugar de `{}` o `begin` /` end` para mostrar *anidamiento *.
 * Cualquier indentación consistente es legal, pero casi todos usan cuatro espacios.

~~~
for number in [2, 3, 5]:
print(number)
~~~
{: .language-python}
~~~
IndentationError: expected an indented block
~~~
{: .error}

* La indentación es siempre significativa en Python.

~~~
firstName = "Jon"
  lastName = "Smith"
~~~
{: .language-python}
~~~
File "<ipython-input-7-f65f2962bf9c>", line 2
lastName = "Smith"
^
IndentationError: unexpected indent
~~~
{: .error}

* Este error se puede solucionar eliminando los espacios adicionales 
al comienzo de la segunda línea.

## Las variables de control pueden tener cualquier nombre.

* Como todas las variables, las variables de control son:
 * Creadas a petición.
 * Sin significado: pueden usar cualquier nombre.

~~~
for kitten in [2, 3, 5]:
    print(kitten)
~~~
{: .language-python}

## El cuerpo de un bucle puede contener muchas instrucciones.

* Pero ningún bucle debería tener más de unas pocas líneas de longitud.
* Es difícil para los seres humanos tener en mente grandes fragmentos de código.

~~~
primes = [2, 3, 5]
for p in primes:
    squared = p ** 2
    cubed = p ** 3
    print(p, squared, cubed)
~~~
{: .language-python}
~~~
2 4 8
3 9 27
5 25 125
~~~
{: .output}

## Usa `range` para iterar sobre una secuencia de números.

* La función incorporada [`range`](https://docs.python.org/3/library/stdtypes.html#range) produce una secuencia de números.
 * *No es* una lista: los números se producen a pedido.
 para hacer que el bucle en grandes rangos sea más eficiente
* `range(N)` son los números 0..N-1
* Exactamente los índices legales de una lista o secuencia de caracteres de longitud N

~~~
print('un range no es una lista: range(0, 3)')
for number in range(0, 3):
    print(number)
~~~
{: .language-python}
~~~
un range no es una lista: range(0, 3)
0
1
2
~~~
{: .output}

## El patrón Acumulador convierte muchos valores en uno.

*  Un patrón común en los programas es:
 1. Inicializar una variable *acumulador* a cero, la secuencia de caracteres vacía o la lista vacía.
2. Actualizar la variable con valores de una colección. 

~~~
# Suma los primeros 10 números enteros.
total = 0
for number in range(10):
    total = total + (number + 1)
print(total)
~~~
{: .language-python}
~~~
55
~~~
{: .output}

* Lee `total = total + (number + 1)` como:
 * Suma 1 al valor actual de la variable de control `number`.
* Añade esto al valor actual de la variable acumuladora `total`.
* Asigna esto a `total`, reemplazando el valor actual.
* Tenemos que añadir `number + 1` porque `range` produce 0..9, no 1..10.

> ## Clasificación de errores 
>
> ¿Es un error de indentación un error de sintaxis o un error de tiempo de ejecución?
> > ## Solución
> > Un IndentationError es un error de sintaxis. Los programas con errores de sintaxis no se pueden iniciar
> > Un programa con un error de ejecución se iniciará pero se lanzará un error bajo ciertas condiciones.
> {: .solution}
{: .challenge}

> ## Rastreo de Ejecución
>
> Crea una tabla que muestre los números de las líneas que se ejecutan cuando se corre este programa,  
> y los valores de las variables después de ejecutar cada línea.
>
> ~~~
> total = 0
> for char in "tin":
> total = total + 1
> ~~~
> {: .language-python}
> > ## Solución
> >
> > | no. de linea | Variables |
> > |---------|----------------------|
> > | 1 | total = 0 |
> > | 2 | total = 0 char = 't' |
> > | 3 | total = 1 char = 't' |
> > | 2 | total = 1 char = 'i' |
> > | 3 | total = 2 char = 'i' |
> > | 2 | total = 2 char = 'n' |
> > | 3 | total = 3 char = 'n' |
> {: .solution}
{: .challenge}

> ## Invertir a una secuencia de caracteres
>
> Completa los espacios en blanco en el programa a continuación para que imprima "nit"
> (el reverso de la secuencia de caracteres original "tin").
>
> ~~~
> original = "tin"
> result = ____
> for char in original:
> result = ____
> print(result)
> ~~~
> {: .language-python}
> > ## Solución
> > ~~~
> > original = "tin"
> > result = ""
> > for char in original:
> > result = char + result
> > print(result)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Practica con el Acumulador
>
> Complete los espacios en blanco en cada uno de los programas de abajo
> para producir el resultado indicado.
>
> ~~~
> # Longitud total de las cadenas de texto en la lista: ["red", "green", "blue"] => 12
> total = 0
> for word in ["red", "green", "blue"]:
> ____ = ____ + len(word)
> print(total)
> ~~~
> {: .language-python}
> > ## Solución
> > ~~~
> > total = 0
> > for word in ["red", "green", "blue"]:
> > total = total + len(word)
> > print(total)
> > ~~~
> > {: .language-python}
> {: .solution}
>
> ~~~
> # Lista de longitudes de las palabras: ["red", "green", "blue"] => [3, 5, 4]
> lengths = ____
> for word in ["red", "green", "blue"]:
> lengths.____(____)
> print(lengths)
> ~~~
> {: .language-python}
> > ## Solución
> > ~~~
> > lengths = []
> > for word in ["red", "green", "blue"]:
> > lengths.append(len(word))
> > print(lengths)
> > ~~~
> > {: .language-python}
> {: .solution}
>
> ~~~
> # Concatena todas las palabras: ["red", "green", "blue"] => "redgreenblue"
> words = ["red", "green", "blue"]
> result = ____
> for ____ in ____:
> ____
> print(result)
> ~~~
> {: .language-python}
> > ## Solución
> > ~~~
> > words = ["red", "green", "blue"]
> > result = ""
> > for word in words:
> > result = result + word
> > print(result)
> > ~~~
> > {: .language-python}
 
> {: .solution}
>
> ~~~
> # Crea un acrónimo: ["red", "green", "blue"] => "RGB"
> # escribe toda la solución.
> ~~~
> {: .language-python}
> > ## Solución
> > ~~~
> > acronym = ""
> > for word in ["red", "green", "blue"]:
> > acronym = acronym + word[0].upper()
> > print(acronym)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Suma acumulativa
>
> Reordena e indenta correctamente las líneas de código a continuación
> para que se imprima una lista con la suma acumulativa de datos.
> El resultado debería ser `[1, 3, 5, 10]`.
>
> ~~~
> cumulative.append(sum)
> for number in data:
> cumulative = []
> sum += number
> sum = 0
> print(cumulative)
> data = [1,2,2,5]
> ~~~
> {: .language-python}
> > ## Solución
> > ~~~
> > sum = 0
> > data = [1,2,2,5]
> > cumulative = []
> > for number in data:
> > sum += number
> > cumulative.append(sum)
> > print(cumulative)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Identificación de errores en el nombre de la variable
>
> 1. Lee el siguiente código e intenta identificar cuáles son los errores
> *sin* ejecutarlos.
> 2. Ejecuta el código y lee el mensaje de error.
> ¿Qué tipo de `NameError` crees que es?
> ¿Es una secuencia de caracteres sin comillas, una variable mal escrita o una
> variable que debería haber sido definida pero no lo fue?
> 3. Corrige el error.
> 4. Repite los pasos 2 y 3, hasta que haya solucionado todos los errores.
>
> ~~~
> for number in range(10):
>     # usa a si el número es un múltiplo de 3, usa b en los otros casos
>     if (Number % 3) == 0:
>         message = message + a
>     else:
>         message = message + "b"
> print(message)
> ~~~
> {: .language-python}
> > ## Solución
> > la variable `message` necesita ser inicializada y los nombres de las variables en Python son sensibles a las mayúsculas y minúsculas: `number` y `Number`
> > se refieren a diferentes variables.
> > ~~~
> > message = ""
> > for number in range(10):
> >     # usa a si el número es un múltiplo de 3, usa b en los otros casos
> >     if (number % 3) == 0:
> >         message = message + "a"
> >     else:
> >         message = message + "b"
> >     print(message)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Identificación de errores en los elementos
>
> 1. Lee el código que aparece a continuación e intenta identificar cuáles son los errores
> *sin* ejecutarlo.
> 2. Ejecuta el código y lee el mensaje de error. ¿Qué tipo de error es?
> 3. Arregla el error.
>
> ~~~
> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
> print('Mi temporada favorita es  ', seasons[4])
> ~~~
> {: .language-python}
> > ## Solución
> > Esta lista tiene 4 elementos y el índice para acceder al último elemento de la lista es `3`.
> > ~~~
> > seasons = ['Spring', 'Summer', 'Fall', 'Winter']
> > print('Mi temporada favorita es ', seasons[3])
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

