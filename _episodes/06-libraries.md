---
title: "Bibliotecas"
teaching: 10
exercises: 10
questions:
- "¿Cómo puedo usar el software que otras personas han escrito?"
- "¿Cómo puedo saber qué hace dicho software?"
objectives:
- "Explicar qué son las bibliotecas de software, y por qué los programadores las crean y usan."
- "Escribir programas que importen y usen bibliotecas de la biblioteca estándar de Python."
- "Encontrar y leer la documentación de las bibliotecas estándar de forma interactiva (en el intérprete) y en  línea."
keypoints:
- "Gran parte del poder que puede tener un lenguaje de programación está en sus bibliotecas."
- "Un programa debe importar los módulos de una biblioteca para poder usarlos."
- "Usa `help` para aprender sobre los contenidos de un módulo de la biblioteca."
- "Importa elementos específicos de una biblioteca para acortar programas."
- "Crea un alias para una biblioteca al importarla para acortar programas."
---
## Gran parte del poder de un lenguaje de programación está en sus bibliotecas.

* Una *biblioteca* es una colección de archivos (llamados *módulos*) que contienen
funciones para ser usadas por otros programas.
* Pueden también contener datos (e.g. constantes numéricas) y otras cosas.
* Los contenidos de una biblioteca deberían estar relacionados, pero no hay una forma establecida para imponer esto.
* La [biblioteca estándar][stdlib] de Python es una colección extensa de módulos que vienen
con Python mismo.
* Muchas bibliotecas adicionales están disponibles en [PyPI][pypi] (el índice de paquetes de Python).
* Más tarde veremos cómo escribir nuevas bibliotecas.

## Bibliotecas y módulos
>
> Una biblioteca es una colección de módulos, pero los términos a menudo se usan
> indistintamente, especialmente porque muchas bibliotecas consisten de un solo
> módulo, entonces no te preocupes si las mezclas. 
{: .callout}


## Un programa debe importar un módulo de biblioteca antes de usarlo.

* Usa `import` para cargar un módulo de una biblioteca en la memoria del programa.
* Después refiérete a las cosas del módulo como `nombre_del_modulo.nombre_de_la_cosa`.
*  Python usa `.`  para referirse a "parte de".
* Usando `math`, uno de los módulos de la biblioteca estándar:

~~~
import math

print('pi es', math.pi)
print('cos(pi) es', math.cos(math.pi))
~~~
{: .language-python}
~~~
pi es 3.141592653589793
cos(pi) es -1.0
~~~
{: .output}

* Debemos referirnos a cada elemento con el nombre del módulo.
    *   `math.cos(pi)` no funcionará: la referencia a `pi`
no "hereda" de alguna forma la referencia que está haciendo la función a `math`

## Usa `help` para aprender sobre los contenidos del módulo de una biblioteca.

* Funciona tal y como la ayuda para una función.

~~~
help(math)
~~~
{: .language-python}
~~~
Help on module math:

NAME
    math

MODULE REFERENCE
    http://docs.python.org/3/library/math

La documentación que sigue fue automáticamente generada desde los archivos fuente
de Python (los cuales están escritos en inglés). Puede estar incompleta, ser incorrecta o incluir características que son
consideradas detalles de la implementación y que pueden variar entre implementaciones
de Python. Cuando tengas dudas, consulta la referencia al módulo en la
dirección que encuentras arriba.

DESCRIPTION
    Este módulo siempre está disponible. Proporciona acceso a las
    funciones matemáticas definidas por el estándar C.

FUNCTIONS
    acos(x, /)
        Devuelve el arco coseno (medido en radianes) de x
⋮ ⋮ ⋮
~~~
{: .output}

## Importa elementos específicos del módulo de una biblioteca para acortar programas

* Usa `from ... import ...` para cargar solamente elementos específicos del módulo de una biblioteca.
* Después refiérete a ellos directamente sin escribir el nombre de la biblioteca como prefijo.

~~~
from math import cos, pi

print('cos(pi) es', cos(pi))
~~~
{: .language-python}
~~~
cos(pi) es -1.0
~~~
{: .output}

## Crea un alias para el módulo de una biblioteca al importarlo para acortar programas.

* Usa `import ... as ...` para asignarle a una biblioteca un *alias* más corto al importarla.
* Después refiérete a los elementos de la biblioteca usando el nombre corto.

~~~
import math as m

print('cos(pi) es', m.cos(m.pi))
~~~
{: .language-python}
~~~
cos(pi) es -1.0
~~~
{: .output}

*   Esto se suele hacer con las librerías que se usan frecuentemente o que tienen nombres largos.
* Por ejemplo, para la biblioteca de graficación `matplotlib` se suele usar el alias `mpl`.
* Pero esto puede hacer que los programas sean más difíciles de entender,
porque los lectores deberán aprender los alias de tu programa.

> ## Explorando el módulo Math
>
> 1. ¿Qué función del módulo `math` se puede usar para calcular la raíz cuadrada
> *sin usar* `sqrt`?
> 2. Si la biblioteca contiene esta otra función, ¿por qué existe `sqrt`?
>
> > ## Solución
> > 1. Usando `help(math)` podemos ver que tenemos `pow(x,y)` además de `sqrt(x)`,
> > entonces podemos usar `pow(x, 0.5)` para hallar una raíz cuadrada.
> > 2. Podríamos argumentar que la función `sqrt(x)` es más legible que `pow(x, 0.5)` cuando
> > implementamos ecuaciones. La legibilidad es la piedra angular de la buena programación, entonces
> > tiene sentido proveer una función especial para este caso específico y común.
> > 
> > También, el diseño de la biblioteca `math` de Python tiene sus raíces en el estándar de C,
> > el cual incluye ambos `sqrt(x)` y `pow(x,y)`, entonces un poco de la historia de 
> > la programación está mostrándose en los nombres de las funciones de Python. 
> {: .solution}
{: .challenge}

> ## Localizando el módulo correcto
>
> Tú quieres seleccionar un caracter de una secuencia de caracteres al azar:
>
> ~~~
> bases = 'ACTTGCTTGAC'
> ~~~
> {: .language-python}
>
> 1. ¿Cuál módulo de la [biblioteca estándar][stdlib] podría ayudarte?
> 2. ¿Qué función seleccionarías de ese módulo?, ¿tienes otras alternativas?
> 3. Intenta escribir un programa que use esa función.
>
> > ## Solución
> >
> > El [módulo aleatorio][randommod] parece que podría ayudarte.
> >
> > La cadena tiene 11 caracteres, cada uno con un índice posicional de 0 a 10.
> > Podrías usar la función `random.randrange` (o el alias `random.randint`
> > si te parece más fácil de recordar) para obtener un número entero al azar entre 0 y 
> > 10, y después seleccionar el caracter en esa posición:
> >
> > ~~~
> > from random import randrange
> >
> > random_index = randrange(len(bases))
> > print(bases[random_index])
> > ~~~
> > {: .language-python}
> >
> > o, más compacto:
> >
> > ~~~
> > from random import randrange
> >
> > print(bases[randrange(len(bases))])
> > ~~~
> > {: .language-python}
> >
> > ¿Tal vez encontraste la función `random.sample`? Ésta te permite escribir
> > un poco menos:
> >
> > ~~~
> > from random import sample
> >
> > print(sample(bases, 1)[0])
> > ~~~
> > {: .language-python}
> >
> > Nota que esta función regresa una lista de valores. Aprenderemos sobre
> > listas en el [episodio 11]({% link _episodes/11-lists.md %}).
> >
> > Hay también otras funciones que podrías usar, pero resultarías con un
> > código más complejo.
> {: .solution}
{: .challenge}


> ## Ejemplo de programación con el rompecabezas (problema de Parson)
>
> Reorganiza las siguientes declaraciones para imprimir una
> base de ADN al azar junto con su índice en la cadena. Puede que no todas las declaraciones sean necesarias. Puedes usar/añadir variables intermedias. 
>
> ~~~
> bases="ACTTGCTTGAC"
> import math
> import random
> ___ = random.randrange(n_bases)
> ___ = len(bases)
> print("base aleatoria", bases[___], "índice de la base", ___)
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > ~~~
> > import math 
> > import random
> > bases = "ACTTGCTTGAC" 
> > n_bases = len(bases)
> > idx = random.randrange(n_bases)
> > print("base aleatoria", bases[idx], "índice de la base", idx)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## ¿Cuándo está disponible la ayuda?
>
> Cuando un colega tuyo escribe `help(math)`,
> Python reporta un error:
>
> ~~~
> NameError: name 'math' is not defined
> ~~~
> {: .error}
>
> ¿Qué se le olvidó hacer a tu colega?
>
> > ## Solución
> >
> > importar el módulo `math` (`import math`)
> {: .solution}
{: .challenge}

> ## Importando con los alias.
>
> 1. Rellena los espacios en blanco para que el programa que está abajo imprima `90.0`
> 2. Reescribe el programar para que use `import` *sin* el `as`.
> 3. ¿Cuál de las dos formas te parece más fácil de leer?
>
> ~~~
> import math as m
> angle = ____.degrees(____.pi / 2)
> print(____)
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > ~~~
> > import math as m
> > angle = m.degrees(m.pi / 2)
> > print(angle)
> > ~~~
> > {: .language-python}
> >
> > el cual puede ser escrito como
> >
> > ~~~
> > import math
> > angle = math.degrees(math.pi / 2)
> > print(angle)
> > ~~~
> > {: .language-python}
> >
> > Como acabas de escribir el código y estás familiarizado con él, podría 
> > parecerte más legible la primera versión. Pero cuando estés intentando leer un código enorme
> > escrito por alguien más, o cuando estés regresando a un código enorme tuyo
> > después de meses de no verlo, los nombres no-abreviados suelen ser más legibles, excepto
> > cuando las convenciones de abreviación son claras.
> {: .solution}
{: .challenge}

> ## Hay muchas formas de importar bibliotecas!
>
> Haz coincidir las siguientes declaraciones de impresión con las llamadas adecuadas a la biblioteca.
>
> Comandos de print:
>
> 1. `print("sin(pi/2) =", sin(pi/2))`
> 2. `print("sin(pi/2) =", m.sin(m.pi/2))`
> 3. `print("sin(pi/2) =", math.sin(math.pi/2))`
>
> Llamadas a la biblioteca:
>
> 1. `from math import sin, pi`
> 2. `import math`
> 3. `import math as m`
> 4. `from math import *`
>
> > ## Solución
> >
> > 1. Las llamadas 1 y 4 a la biblioteca. Para podernos referir directamente a `sin` y `pi` sin usar el
> > nombre de la biblioteca como prefijo, tienes que usar la declaración
> >  `from ... import ...`. Mientras la llamada 1 a la biblioteca importa específicamente las dos funciones
> > `sin` y `pi`, la llamada 4 a la biblioteca importa todas las funciones del módulo `math`.
> > 2. La llamada 3 a la biblioteca. Aquí se hace referencia a `sin` y `pi` usando
> >      el nombre corto `m` en vez de `math`. La llamada 3 a la biblioteca hace
> >      exactamente eso usando la sintaxis `import ... as ...` - crea un alias para `math` en forma de
> >      el nombre abreviado `m`.
> > 3. La llamada 2 a la biblioteca. Aquí nos referimos a `sin` y `pi` con el nombre
> >     regular de la biblioteca `math`, entonces la llamada regular `import ...` basta.
> {: .solution}
{: .challenge}

> ## Importando elementos específicos
>
> 1. Rellena los espacios en blanco para que el programa de abajo imprima `90.0`
> 2. ¿Te parece que esta versión es más fácil de leer que las anteriores?
> 3. Why *wouldn't* programmers always use this form of `import`?
> 3. ¿Por qué los programadores *no suelen* usar siempre esta forma del `import`?
>
> ~~~
> ____ math import ____, ____
> angle = degrees(pi / 2)
> print(angle)
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > ~~~
> > from math import degrees, pi
> > angle = degrees(pi / 2)
> > print(angle)
> > ~~~
> > {: .language-python}
> >
> > Seguramente te parece más legible esta versión puesto que es menos densa.
> > La razón principal para no usar esta forma de importar es para evitar conflictos de nombres. 
> > Por ejemplo, no importarías `degrees` de tal forma si también quisieras usar
> > el nombre `degrees` para una variable o función propia. O si también
> > fueras a importar una función llamada `degrees` de otra biblioteca.
> {: .solution}
{: .challenge}

> # # Leyendo mensajes de error
>
> 1. Lee el código acá abajo e intenta identificar cuáles son los errores que tiene sin correrlo.
> 2. Corre el código y lee el mensaje de error. ¿Qué tipo de error es?
>
> ~~~
> from math import log
> log(0)
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > 1. El logaritmo de `x` solo está definido para `x > 0`, entonces 0 está fuera del
> >    dominio de la función.
> > 2. Obtienes un error de tipo "ValueError", indicando que la función
> >     recibió un valor inadecuado en el argumento. El mensaje adicional
> >     "math domain error" (error matemático en el dominio) hace más claro qué tipo de problema es.
> {: .solution}
{: .challenge}

[pypi]: https://pypi.python.org/pypi/
[stdlib]: https://docs.python.org/3/library/
[randommod]: https://docs.python.org/3/library/random.html

