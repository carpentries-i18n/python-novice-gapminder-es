---
title: "Alcance de una Variable"
teaching: 10
exercises: 10
questions:
- "¿Cómo trabajan realmente las llamadas a funciones?"
- "Cómo puedo determinar donde ocurrieron los errores?"
objectives:
- "Identificar variables locales y globales."
- "Identificar parámetros como variables locales."
- "Lea un registro de rastreo y determine el archivo, la función y el número de línea en que ocurrió el error, el tipo de error y el mensaje de error."
keypoints:
- "El alcance de una variable es la parte de un programa que puede 'ver' esa variable."
---
## El alcance de una variable es la parte de un programa que puede "ver" esa variable.

*   Hay contados nombres sensibles para las variables.
*   Las personas que usan funciones no se deberían preocupar
    qué variable nombra al autor de la función utilizada.
*   Las personas que escriben funciones no deberian tener que preocuparse sobre
    los nombres de las variables que usa el llamador de la función.
*   La parte de un programa en el que una variable es visible se llama *scope*/alcanse.

~~~
pressure = 103.9

def adjust(t):
    temperature = t * 1.43 / pressure
    return temperature
~~~
{: .language-python}

*   `pressure` es una *variable global*.
    *   Definida fuera de cualquier función particular.
    *   Visible en todas partes.
*   `t` y `temperature` son *variables locales* en `adjust`.
    *   Definida en la función.
    *   No visible en el programa principal.
    *   Recuerda: un parámetro de función es una variable
     que se le asigna automáticamente un valor cuando se llama a la función.

~~~
print('adjusted:', adjust(0.9))
print('temperature after call:', temperature)
~~~
{: .language-python}
~~~
adjusted: 0.01238691049085659
~~~
{: .output}
~~~
Traceback (most recent call last):
  File "/Users/swcarpentry/foo.py", line 8, in <module>
    print('temperature after call:', temperature)
NameError: name 'temperature' is not defined
~~~
{: .error}

> ## Uso de Variable Local y Global
>
> Rastree los valores de todas las variables en este programa a medida que se ejecuta.
> (Usa '---' como el valor de las variables antes y después de que existan.)
>
> ~~~
> limit = 100
>
> def clip(value):
>     return min(max(0.0, value), limit)
>
> value = -22.5
> print(clip(value))
> ~~~
> {: .language-python}
{: .challenge}

> ## Leyendo mensajes de error
>
> Lea el registro de rastreo abajo, e identifique lo siguiente:
>
> 1. ¿Cuántos niveles tiene el registro de rastreo?
> 2. ¿Cuál es el nombre del archivo donde ocurrió el error?
> 3. ¿Cuál es el nombre de la función donde ocurrió el error?
> 4. ¿En qué número de línea en esta función se produjo el error?
> 5. ¿Cuál es el tipo de error?
> 6. ¿Cuál es el mensaje de error?
>
> ~~~
> ---------------------------------------------------------------------------
> KeyError                                  Traceback (most recent call last)
> <ipython-input-2-e4c4cbafeeb5> in <module>()
>       1 import errors_02
> ----> 2 errors_02.print_friday_message()
>
> /Users/ghopper/thesis/code/errors_02.py in print_friday_message()
>      13
>      14 def print_friday_message():
> ---> 15     print_message("Friday")
>
> /Users/ghopper/thesis/code/errors_02.py in print_message(day)
>       9         "sunday": "Aw, the weekend is almost over."
>      10     }
> ---> 11     print(messages[day])
>      12
>      13
>
> KeyError: 'Friday'
> ~~~
> {: .error}
{: .challenge}

