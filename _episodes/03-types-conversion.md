---
title: "Tipos de Datos y Conversión de Tipos"
teaching: 10
exercises: 10
questions:
- "¿Qué tipo de datos almacenan los programas?"
- "¿Cómo puedo convertir un tipo a otro?"
objectives:
- "Explicar las diferencias clave entre números enteros y números de punto flotante."
- "Use las funciones de la biblioteca de Python para convertir entre enteros, números de punto flotante, y secuencia de caracteres."
keypoints:
- "Cada valor tiene un tipo."
- "Use la función  `type` para encontrar el tipo de un valor."
- "Los tipos controlan qué operaciones se pueden hacer con los valores."
- "A las secuencias de caracteres se les pueden agregar y multiplicar."
- "Las secuencias de caracteres tienen una longitud (pero los números no)."
- "Se deben convertir números a secuencias de caracteres o viceversa cuando se opera con ellas."
- "Se pueden mezclar  enteros y puntos flotantes libremente en operaciones."
- "Las variables solo cambian de valor cuando se les asigna algo."
---
## Cada valor tiene un tipo.

* Cada valor en un programa tiene un tipo específico.
* Entero (`int`): representa números enteros positivos o negativos como 3 o -512.
* Número de punto flotante (`float`): representa números reales como 3.14159 o -2.5.
* secuencia de caracteres  (usualmente llamado "string", `str`): texto.
* Escrito entre comillas simples o comillas dobles (siempre y cuando se usen las mismas).
* El entrecomillado no se imprimen cuando una secuencia de caracteres / cadena de texto es desplegada.

## Use la función integrada `type` para encontrar el tipo de un valor.

* Use la función integrada `type` para averiguar de que tipo es un valor.
* Funciona también en variables.
 * Pero recuerda: el *valor* tiene el tipo --- la *variable* es solo una etiqueta.

~~~
print(type(52))
~~~
{: .language-python}
~~~
<class 'int'>
~~~
{: .output}

~~~
fitness = 'average'
print(type(fitness))
~~~
{: .language-python}
~~~
<class 'str'>
~~~
{: .output}

## Los tipos controlan qué operaciones (o métodos) se pueden realizar en un valor dado.

 * El tipo de un valor determina lo que el programa puede hacerle.

~~~
print(5 - 3)
~~~
{: .language-python}
~~~
2
~~~
{: .output}

~~~
print('hello' - 'h')
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError Traceback (most recent call last)
<ipython-input-2-67f5626a1e07> in <module>()
----> 1 print('hello' - 'h')

TypeError: unsupported operand type(s) for -: 'str' and 'str'
~~~
{: .error}

## Puede usar los operadores "+" y "*" en secuencia de caracteres

*   "Sumar" secuencia de caracteres les concatena.

~~~
full_name = 'Ahmed' + ' ' + 'Walsh'
print(full_name)
~~~
{: .language-python}
~~~
Ahmed Walsh
~~~
{: .output}

*   Multiplicar una secuencia de caracteres por un entero _N_ crea una nueva cadena que consiste en esa cadena de caracteres repetida _N_ veces.
    *   Ya que la multiplicación es suma repetida.

~~~
separator = '=' * 10
print(separator)
~~~
{: .language-python}
~~~
==========
~~~
{: .output}

## Las secuencias de caracteres tienen una longitud (pero los números no).

*  La función incorporada `len` cuenta el número de caracteres en una secuencia de caracteres / cadena de texto.

~~~
print(len(full_name))
~~~
{: .language-python}
~~~
11
~~~
{: .output}

*   Pero los números no tienen una longitud (ni siquiera cero).

~~~
print(len(52))
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-3-f769e8e8097d> in <module>()
----> 1 print(len(52))

TypeError: object of type 'int' has no len()
~~~
{: .error}

## <a name='convert-numbers-and-strings'></a> Debe convertir los números en secuencia de caracteres o viceversa cuando realizando operaciones sobre ellos.

*   No se puede sumar números y secuencias de caracteres.

~~~
print(1 + '2')
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-4-fe4f54a023c6> in <module>()
----> 1 print(1 + '2')

TypeError: unsupported operand type(s) for +: 'int' and 'str'
~~~
{: .error}

*   No está permitido porque es ambiguo: ¿debería `1 + '2'` ser `3` o `'12`'?
*   Algunos tipos se pueden convertir a otros tipos utilizando el nombre del tipo como una función.

~~~
print(1 + int('2'))
print(str(1) + '2')
~~~
{: .language-python}
~~~
3
12
~~~
{: .output}

## Puede mezclar enteros y números de punto flotantes libremente en las operaciones.

*   Enteros y números de punto flotante se pueden mezclar en aritmética.
    *   Python 3 convierte automáticamente los enteros en números de puntos flotantes según sea necesario. (La división de enteros en Python 2 devolverá un entero, el entero más bajo del valor de la división).

~~~
print('half is', 1 / 2.0)
print('three squared is', 3.0 ** 2)
~~~
{: .language-python}
~~~
half is 0.5
three squared is 9.0
~~~
{: .output}

## Las variables solo cambian de valor cuando se les asigna algo.

*   Si hacemos que una celda de una hoja de cálculo dependa de otra,
    y actualizamos esta última,
    la anterior se actualiza automáticamente.
*   Esto **no** ocurre en lenguajes de programación.

~~~
first = 1
second = 5 * first
first = 2
print('first is', first, 'and second is', second)
~~~
{: .language-python}
~~~
first is 2 and second is 5
~~~
{: .output}

*   La computadora lee el valor de `first` cuando hace la multiplicación,
    el resultado de la multiplicación lo asigna a `second`.
*   Después de eso, `second`  solo guarda el valor y no recuerda de dónde vino.

> ## Fracciones
>
> ¿Qué tipo de valor es 3.4?
> ¿Cómo puedes averiguarlo?
>
> > ## Solución
> >
> >Es un número de punto flotante (a menudo abreviado "float").
> >
> > ~~~
> > print(type(3.4))
> > ~~~
> > {: .language-python}
> > ~~~
> > <class 'float'>
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Conversión Automática de Tipos
>
> ¿Qué tipo de valor resulta de 3.25 + 4?
>
> > ## Solución
> >
> > Es **float**:
> > Enteros son convertidos automáticamente en números de puntos flotantes según sea necesario.
> >
> > ~~~
> > result = 3.25 + 4
> > print(result, 'is', type(result))
> > ~~~
> > {: .language-python}
> > ~~~
> > 7.25 is <class 'float'>
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Elige un Tipo
>
> ¿Qué tipo de valor (**integer**, **float**, o **string**)
> usarías para representar cada uno de los siguientes? Intenta encontrar más de una buena respuesta para cada problema. Por ejemplo, en el n. ° 1, ¿cuándo tendría más sentido contar días con una variable de punto flotante que usar un entero?
>
> 1. Número de días desde el comienzo del año.
> 2. Tiempo transcurrido desde el inicio del año hasta ahora en días.
> 3. Número de serie de un equipo de laboratorio.
> 4. Edad de un espécimen de laboratorio
> 5. Población actual de una ciudad.
> 6. Población media de una ciudad a lo largo del tiempo.
>
>> ## Solución
> >
>> Las respuestas a las preguntas son:
>> 1. Entero, ya que el número de días estaría entre 1 y 365.
>> 2. Punto flotante, ya que se requieren días fraccionados
>> 3. Secuencia de caracteres si el número de serie contiene letras y números; de lo contrario, entero si el número de serie consta solo de números
>> 4. ¡Esto variará! ¿Cómo define la edad de un espécimen? días completos desde la colección (**entero**)? fecha y hora (**secuencia de caracteres**)?
>> 5. Elija punto flotante para representar la población como grandes agregados (por ejemplo, millones), o entero para representar la población en unidades de individuos.
>> 6. Punto flotante, ya que es probable que un promedio tenga una parte fraccionaria.
> > {: .output}
> {: .solution}
{: .challenge}

> ## Tipos de División
>
> En Python 3, el operador `//` realiza una división de piso de número entero  ( devuelve la parte entera de la división), el operador `/` realiza una división
> de número de punto flotante, y el operador '%' (o *módulo*) calcula y devuelve el resto de la división entera:
>
> ~~~
> print('5 // 3:', 5//3)
> print('5 / 3:', 5/3)
> print('5 % 3:', 5%3)
> ~~~
> {: .language-python}
>
> ~~~
> 5 // 3: 1
> 5 / 3: 1.6666666666666667
> 5 % 3: 2
> ~~~
> {: .output}
>
> Sin embargo, en Python 2 (y otros lenguajes), el operador `/` entre dos enteros realiza una división de piso (`//`). Para realizar una división de punto flotante, tenemos que convertir uno de los enteros a punto flotante.
>
> ~~~
> print('5 // 3:', 1)
> print('5 / 3:', 1 )
> print('5 / float(3):', 1.6666667 )
> print('float(5) / 3:', 1.6666667 )
> print('float(5 / 3):', 1.0 )
> print('5 % 3:', 2)
> ~~~
>
> Si `num_subjects` es el número de sujetos que participan en un estudio,
> y `num_per_survey` es el número sujetos que pueden participar en una sola encuesta,
> escriba una expresión que calcule la cantidad de encuestas necesarias
> para alcanzar a todos los participantes de una sola vez.
>
>> ## Solución
>> Queremos la cantidad mínima de encuestas que alcance a todos los participantes de una sola vez, que es
>> el valor redondeado de `num_subjects / num_per_survey`. Esto es
>> equivalente a realizar una división entera con `//` y sumar 1.
> > ~~~
> > num_subjects = 600
> > num_per_survey = 42
> > num_surveys = num_subjects // num_per_survey + 1
> >
> > print(num_subjects, 'subjects,', num_per_survey, 'per survey:', num_surveys)
> > ~~~
> > {: .language-python}
> > ~~~
> > 600 subjects, 42 per survey: 15
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Secuencia de caracteres a Números
>
> Donde sea razonable, `float()` convertirá una secuencia de caracteres a un número de punto flotante,
> y `int()` convertirá un número de punto flotante a un entero:
>
> ~~~
> print("string to float:", float("3.4"))
> print("float to int:", int(3.4))
> ~~~
> {: .language-python}
>
> ~~~
> string to float: 3.4
> float to int: 3
> ~~~
> {: .output}
>
> Sin embargo, si la conversión no tiene sentido, aparecerá un mensaje de error
>
> ~~~
> print("string to float:", float("Hello world!"))
> ~~~
> {: .language-python}
>
> ~~~
> ---------------------------------------------------------------------------
> ValueError                                Traceback (most recent call last)
> <ipython-input-5-df3b790bf0a2> in <module>()
> ----> 1 print("string to float:", float("Hello world!"))
>
> ValueError: could not convert string to float: 'Hello world!'
> ~~~
> {: .error}
>
> Dada esta información, ¿qué espera que haga el siguiente programa?
>
> ¿Qué hace realmente?
>
> ¿Por qué crees que hace eso?
>
> ~~~
> print("fractional string to int:", int("3.4"))
> ~~~
> {: .language-python}
> 
>> ## Solución
>> ¿Qué esperas que haga este programa? No sería tan irracional esperar que el comando `int` de Python 3
>> convierta la **string** "3.4" a 3.4 y una conversión de tipo adicional a 3. Después de todo, Python 3 realiza muchas otras
>> magia - ¿no es esa parte de su encanto?
>>
>> Sin embargo, Python 3 arroja un error. ¿Por qué? Para ser consistente, posiblemente. Si le pide a Python que realice dos
>> typecasts, debe indicar la conversión explícitamente en el código.
> >
> > ~~~
> > int("3.4")
> > int(float("3.4"))
> > ~~~
> > {: .language-python}
> > ~~~
> > In [2]: int("3.4")
> > ---------------------------------------------------------------------------
> > ValueError                                Traceback (most recent call last)
> > <ipython-input-2-ec6729dfccdc> in <module>()
> > ----> 1 int("3.4")
> > ValueError: invalid literal for int() with base 10: '3.4'
> > 3
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Aritmética con Diferentes Tipos
>
> ¿Cuál de los siguientes devolverá el **float** `2.0`?
> Nota: puede haber más de una respuesta correcta.
>
> ~~~
> first = 1.0
> second = "1"
> third = "1.1"
> ~~~
> {: .language-python}
>
> 1. `first + float(second)`
> 2. `float(second) + float(third)`
> 3. `first + int(third)`
> 4. `first + int(float(third))`
> 5. `int(first) + int(float(third))`
> 6. `2.0 * second`
>
> > ## Solución
> >
> > Respuesta: 1 y 4
> {: .solution}
{: .challenge}

> ## Números Complejos
>
> Python proporciona números complejos,
> que son escritos como `1.0+2.0j`.
> Si `val` es un número imaginario,
> Se puede acceder a sus partes reales e imaginarias usando *notación de punto*
> como `val.real` y` val.imag`.
>
> ~~~
> complex = 6 + 2j
> print(complex.real)
> print(complex.imag)
> ~~~
> {: .language-python}
>
> ~~~
> 6.0
> 2.0
> ~~~
> {: .output}
>
>
> 1. ¿Por qué crees que Python usa `j` en lugar de` i` para la parte imaginaria?
> 2. ¿Qué esperas que produzca `1+2j + 3` ?
> 3. ¿Qué esperas que sea `4j` ? ¿Y qué esperas de `4 j` o` 4 + j` ?
>
>> ## Solución
>>
>> 1. Los tratamientos matemáticos estándar suelen usar `i` para denotar un número imaginario. Sin embargo, según informan los medios
>> fue una convención temprana establecida a partir de la ingeniería eléctrica que ahora presenta un área técnicamente costosa para
>> cambiar. [Stack Overflow proporciona una explicación adicional y
>> discusión.] (http://stackoverflow.com/questions/24812444/why-are-complex-numbers-in-python-denoted-with-j-instead-of-i)
>> 2. `(4 + 2j)`
>> 3. `4j`, `Syntax Error: invalid syntax`, en este caso _j_ se considera una variable y esto depende de si _j_ está definido y, de ser así, su valor asignado
> {: .solution}
{: .challenge}

