---
title: " Funciones integradas y ayuda"
teaching: 15
exercises: 10
questions:
- "¿Cómo puedo usar las funciones integradas?"
- " ¿Cómo puedo saber qué hacen?"
- "¿Qué tipo de errores pueden ocurrir en los programas?"
objectives:
- "Explicar el propósito de las funciones."
- "Llamar correctamente a las funciones integradas de Python."
- "Anidar correctamente las llamadas a las funciones integradas."
- "Usar la ayuda para mostrar la documentación de las funciones integradas."
- "Describir correctamente las situaciones en las que se producen SyntaxError y NameError."
keypoints:
- "Usar comentarios para agregar documentación a los programas."
- "Una función puede tomar cero o más argumentos."
- "Las funciones incorporadas de uso común incluyen `max`,` min` y `round`."
- " Las funciones solo pueden funcionar para ciertos (combinaciones de) argumentos."
- " Las funciones pueden tener valores predeterminados para algunos argumentos."
- " Usa la función incorporada `help` para obtener ayuda para una función."
- "La Libreta Jupyter tiene dos formas de obtener ayuda."
- "Cada función regresa algo."
- " Python reporta un error de sintáxis cuando no puede entender el código fuente de un programa."
- "Python reporta un error de tiempo de ejecución cuando algo sale mal mientras se ejecuta un programa."
- "Soluciona errores de sintaxis leyendo el código fuente y errores de tiempo de ejecución rastreando la ejecución del programa."
---
##  Usa comentarios para agregar documentación a los programas.

~~~
# Esta oración no es ejecutada por Python.
adjustment = 0.5   #Tampoco esto - cualquier cosa despues de '#' es ignorado.
~~~
{: .language-python}

## Una función puede tener cero o más argumentos.

*   Ya hemos visto algunas funciones --- ahora echemos un vistazo más de cerca.
*   Un *argumento* es un valor pasado a una función.
*   `len` toma exactamente uno.
*   `int`, `str`, y `float` crean un nuevo valor a partir de uno existente.
*   `print` toma cero o más.
*   `print` sin argumentos imprime una línea en blanco.
    *   Siempre debe usar paréntesis, incluso si están vacíos,
        para que Python sepa que se está llamando a una función.

~~~
print('before')
print()
print('after')
~~~
{: .language-python}
~~~
before

after
~~~
{: .output}

## Las funciones incorporadas de uso común incluyen `max`,` min` y `round`.

*   Usa `max` para encontrar el valor más grande de uno o más valores.
*   Usa `min` para encontrar el más pequeño.
*   Ambos funcionan tanto en cadenas de caracteres como en números.
    *   "Más grande" y "más pequeño" usan (0-9, A-Z, a-z) para comparar letras.

~~~
print(max(1, 2, 3))
print(min('a', 'A', '0'))
~~~
{: .language-python}
~~~
3
0
~~~
{: .output}

## Las funciones pueden funcionar solo para (combinaciones de) ciertos argumentos.

*   `max` y `min` deben recibir al menos un argumento.
    *   "El más grande del conjunto vacío" es una pregunta sin sentido.
*   Y deben recibir cosas que puedan compararse con sentido.

~~~
print(max(1, 'a'))
~~~
{: .language-python}
~~~
TypeError                                 Traceback (most recent call last)
<ipython-input-52-3f049acf3762> in <module>
----> 1 print(max(1, 'a'))

TypeError: '>' not supported between instances of 'str' and 'int'
~~~
{: .error}

## Las funciones pueden tener valores por defecto para algunos argumentos.

*   `round` redondeará un número de punto flotante.
*   Por defecto, redondea a cero cifras decimales.

~~~
round(3.712)
~~~
{: .language-python}
~~~
4
~~~
{: .output}

*   Podemos especificar el número de cifras decimales que queremos.

~~~
round(3.712, 1)
~~~
{: .language-python}
~~~
3.7
~~~
{: .output}

## Usa la función incorporada `help` para obtener ayuda sobre una función.

*   Cada función incorporada tiene documentación en línea.

~~~
help(round)
~~~
{: .language-python}
~~~
Help on built-in function round in module builtins:

round(number, ndigits=None)
    Round a number to a given precision in decimal digits.

    The return value is an integer if ndigits is omitted or None.  Otherwise
    the return value has the same type as the number.  ndigits may be negative.
~~~
{: .output}

## Python reporta un error de sintaxis cuando no puede entender la fuente de un programa.

*   Ni siquiera intentará ejecutar el programa si no puede interpretarlo.

~~~
# Olvidar cerrar las comillas alrededor de la cadena de caracteres.
name = 'Feng
~~~
{: .language-python}
~~~
  File "<ipython-input-56-f42768451d55>", line 2
    name = 'Feng
                ^
SyntaxError: EOL while scanning string literal
~~~
{: .error}

~~~
# Un '=' adicional en la asignación.
age = = 52
~~~
{: .language-python}
~~~
  File "<ipython-input-57-ccc3df3cf902>", line 2
    age = = 52
          ^
SyntaxError: invalid syntax
~~~
{: .error}

*   Mira de cerca el mensaje de error:

~~~
print("hola mundo"
~~~
{: .language-python}
~~~
  File "<ipython-input-6-d1cc229bf815>", line 1
    print ("hola mundo"
                        ^
SyntaxError: unexpected EOF while parsing
~~~
{: .error}

*   El mensaje indica un problema en la primera línea de la entrada ("line 1").
    *   En este caso la sección "ipython-input" del nombre de archivo nos dice que
        estamos trabajando con entrada en IPython,
        el intérprete de Python usado por la Libreta Jupyter.
*   La parte `-6-` del nombre de archivo indica que
    el error ocurrió en la celda 6 de nuestra Libreta.
*   A continuación está la línea de código problemática,
    indicando el problema con el puntero `^`.

## <a name='runtime-error'></a> Python reporta un error de tiempo de ejecución cuando algo anda mal mientras un programa se está ejecutando.

~~~
age = 53
remaining = 100 - aege # mal escrito 'age'
~~~
{: .language-python}
~~~
NameError                                 Traceback (most recent call last)
<ipython-input-59-1214fb6c55fc> in <module>
      1 age = 53
----> 2 remaining = 100 - aege # mal escrito 'age'

NameError: name 'aege' is not defined
~~~
{: .error}

*   Arregle errores de sintaxis leyendo el código fuente y errores de tiempo de ejecución rastreando la ejecución.

## La Libreta Jupyter ofrece dos formas de obtener ayuda.

*   Ubica el cursor en cualquier lugar en la invocación a la función 
    (es decir, el nombre de la función o sus parámetros),
    mantén apretado `shift`,
    y presiona `tab`.
*   O escribe un nombre de función seguido de un signo de pregunta.

## Cada función devuelve algo.

*   Cada llamada a una función produce algún resultado.
*   Si la función no tiene un resultado útil que devolver,
    usualmente devuelve el valor especial `None`.

~~~
result = print('ejemplo')
print('el resultado de print es', result)
~~~
{: .language-python}
~~~
ejemplo
el resultado de print es None
~~~
{: .output}

> ## Qué ocurre cuándo
>
> 1. Explica en términos simples el orden de operaciones en el siguiente programa:
>    cuándo ocurre la adición y cuándo la sustracción,
>    cuándo es llamada cada función, etc.
> 2. ¿Cuál es el valor final de `radiance`?
>
> ~~~
> radiance = 1.0
> radiance = max(2.1, 2.0 + min(radiance, 1.1 * radiance - 0.5))
> ~~~
> {: .language-python}
> > ## Solución
> > 1.
> >    1. `1.1 * radiance = 1.1`
> >    2. `1.1 - 0.5 = 0.6`
> >    3. `min(radiance, 0.6) = 0.6`
> >    4. `2.0 + 0.6 = 2.6`
> >    5. `max(2.1, 2.6) = 2.6`
> > 2. Al final, `radiance = 2.6`
> {: .solution}
{: .challenge}

> ## Encuentra la diferencia
>
> 1. Predice qué imprimirá cada una de las declaraciones `print` en el programa a continuación.
> 2. ¿Corre `max(len(rich), poor)` o genera un mensaje de error?
>    Si corre, ¿tiene sentido su resultado?
>
> ~~~
> easy_string = "abc"
> print(max(easy_string))
> rich = "gold"
> poor = "tin"
> print(max(rich, poor))
> print(max(len(rich), len(poor)))
> ~~~
> {: .language-python}
> > ## Solucion
> > ~~~
> > print(max(easy_string))
> > ~~~
> > {: .language-python}
> > ~~~
> > c
> > ~~~
> > {: .output}
> > ~~~
> > print(max(rich, poor))
> > ~~~
> > {: .language-python}
> > ~~~
> > tin
> > ~~~
> > {: .output}
> > ~~~
> > print(max(len(rich), len(poor)))
> > ~~~
> > {: .language-python}
> > ~~~
> > 4
> > ~~~
> > {: .output}
> > `max(len(rich), poor)` causa un TypeError. Esto se vuelve `max(4, 'tin')` y 
> > como discutimos antes un **string** y un **integer** no se pueden comparar significativamente.
> > ~~~
> > TypeError                                 Traceback (most recent call last)
> > <ipython-input-65-bc82ad05177a> in <module>
> > ----> 1 max(len(rich), poor)
> > 
> > TypeError: '>' not supported between instances of 'str' and 'int'
> > ~~~
> > {: .error }
> {: .solution}
{: .challenge}

> ## Por qué no?
>
> Por qué `max` y `min` no devuelven `None` cuando no se les pasan argumentos?
>
> > ## Solución
> > `max` y `min` devuelven TypeErrors en este caso porque no se ha proporcionado el número correcto
> > de parámetros. Si sólo devolvieran `None`, el error sería mucho más difícil de rastrear ya
> > que probablemente estaría almacenado en una variable y usado luego en el programa, would likely be stored into a variable and used later in the program, sólo para causar
> > un error de tiempo de ejecución.
> {: .solution}
{: .challenge}

> ## Último Carácter de una Cadena
>
> Si Python comienza a contar desde cero,
> y `len` devuelve el número de caracteres en una cadena,
> qué expresión de índice te devuelve el último carácter de la cadena `name`?
> (Nota: veremos una forma más simple de hacer esto en un episodio posterior.)
>
> > ## Solución
> >
> > `name[len(name) - 1]`
> {: .solution}
{: .challenge}

