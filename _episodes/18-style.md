---
title: "Estilo de Programación"
teaching: 15
exercises: 15
questions:
- "¿Cómo puedo hacer para que mis programas sean fáciles de leer?"
- "¿Qué formato le dan la mayoría de los programadores a su código?"
- "¿De qué forma los programas pueden verificar su propio funcionamiento?"
objectives:
- "Dar argumentos para las reglas básicas de estilo de programación."
- "Re-formatear programas de una página para hacerlos más fáciles de leer y justificar los cambios."
- "Seguir los estándares comunitarios de estilo de Python (PEP-8)."
keypoints:
- "Sigue el formato estándar de Python en tu código."
- "Utiliza docstrings para proveer ayuda integrada."
---

## Estilo de programación

El estilo del código nos ayuda a entender mejor el código. También ayuda a darle mantenimiento y hacer modificaciones en el código.
Python se apoya mucho en el estilo del código como se puede ver en el sangrado que aplicamos en las líneas para definir los distintos bloques de código.
Python propone un estilo estándar en una de las primeras Propuestas de Mejora de Python (PEP, por sus siglas en inglés), [PEP8](https://www.python.org/dev/peps/pep-0008), y resalta la importancia de la lectura de código en [Zen de Python](https://www.python.org/dev/peps/pep-0020). 

Podemos subrayar algunos puntos:
* documenta tu código
* usa nombres de variables claros y significativos
* usa espacios en blanco, *no* tabuladores, para sangrar lineas


## Sigue el estilo estándar de Python en tu código.

*   [PEP8](https://www.python.org/dev/peps/pep-0008):
    una guía de estilo para Python que discute cómo se deben nombrar las variables,
    cómo se debe usar la el sangrado en tu código,
    cómo se deben estructural las declaraciones `import`,
    etc.
    Seguir las recomendaciones de PEP8 hace más fácil para otros desarrolladores de Python leer y entender tu código,
    y entender como deberán de ser sus contribuciones.
    La [aplicación y biblioteca de Python PEP8](https://pypi.python.org/pypi/pep8)
    puede revisar si tu código cumple con las recomendaciones de PEP8.
*   [La guía de estilo de código de Python de Google](https://google.github.io/styleguide/pyguide.html) 
    da soporte al uso de PEP8 y extiende el estilo de código a una estructura más específica de 
    código en Python, que puede ser también interesante de seguir.
    ["yapf" es el nombre de la herramienta de formato de código](https://github.com/google/yapf/)  de Google.

## Usa aserciones para verificar errores internos.

Las aserciones son un método simple pero poderoso para asegurarnos de que el contexto en el que tu código se ejecuta coincida con lo que esperas.

~~~
def calc_densidad(masa, volumen):
    '''Regresa la densidad media = masa / volumen.'''
    assert volumen > 0
    return masa / volumen
~~~
{: .language-python}

Si la aserción es 'False', el interprete de Python llamará una excepción `AssertionError`. El código de la expresión que falló sera mostrada como parte del mensaje de error. Para ignorar todas las aserciones en tu código debes de ejecutar el interprete con la bandera '-O' (optimize). Las aserciones sólo deben contener pruebas simples y nunca cambiar el estado del programa. Por ejemplo, una aserción nunca debe contener una asignación.

## Utiliza docstrings para proporcionar ayuda.

*   Si la primera cosa en una función es una sequencia de caracteres
 que no está asignada directamente a una variable,
 Python la agrega a la función como una variable de ayuda integrada.
* Se le conoce como *docstring* (abreviatura de "cadena de documentación")

~~~
def average(valores):
    "Regresa el promedio de valores, o None si no se proporcionan valores."

    if len(valores) == 0:
        return None
    return sum(valores) / len(valores)

help(average)
~~~
{: .language-python}
~~~
Ayuda de la función `average` en el módulo __main__:

average(valores)
    Regresa el promedio de valores, o None si no se proporcionan valores.
~~~
{: .output}

## Cadenas con múltiples líneas
>
> Utiliza *sequencias multilínea* para documentar tu código.
> Estas inician y terminan con tres comillas (ya sean sencillas o dobles).
>
>~~~
> """Esta cadena se extiende
> varias líneas.
>
> Son permitidas líneas en blanco."""
> ~~~
> {: .language-python}
{: .callout}

> ## ¿Qué será mostrado?
>
> Subraya las líneas del código de abajo que estarán disponibles como ayuda en línea.
> ¿Hay alguna línea que debería estar disponible pero no está?
> ¿Alguna línea producirá un error de sintaxis o un runtime error?
>
> ~~~
> "Encuentra la máxima distancia entre varias secuencias"
> # Este código encuentra la máxima distancia entre todas las secuencias.
>
> def maximo_general(sequencias):
>     '''Determina la distancia máxima.'''
> 
>     mas_alta = 0
>     for izquierda in sequencias:
>         for derecha in sequencias:
>             '''Evita revisar una secuencia con ella misma.'''
>             if izquierda != derecha:
>                 actual = edit_distance(izquierda, derecha)
>                 mas_alta = max(mas_alta, actual)
> 
>     # Reporta.
>     return mas_alta
> ~~~
> {: .language-python}
{: .challenge}

> ## Documenta Este Código
>
> Convierte el comentario de la siguiente función a un docstring
> y verifica que `help` lo muestre correctamente.
>
> ~~~
> def medio(a, b, c):
>     # Regresa el valor que se encuentre en medio de los tres.
>     # Asume que los valores pueden ser comparados.
>     valores = [a, b, c]
>     valores.sort()
>     return valores[1]
> ~~~
> {: .language-python}
> > ## Solución
> >
> > ~~~
> > def medio(a, b, c):
> >     '''Regresa el valor que se encuentre en medio de los tres.
> >     Asume que los valores pueden ser comparados.'''
> >     valores = [a, b, c]
> >     valores.sort()
> >     return valores[1]
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Limpia Este Código
>
> 1. Lee este programa e intenta predecir lo que hace.
> 2. Ejecútalo: ¿qué tan acertada fué tu predicción?
> 3. Modifica el programa para hacerlo más legible.
>    Recuerda de ejecutarlo después de cada cambio para asegurarte que su comportamiento no cambie.
> 4. Compara tu nueva versión con la de tu vecino.
>    ¿Qué hicieron igual?
>    ¿Qué hicieron diferente? y ¿porqué?
>
> ~~~
> n = 10
> s = 'etcetera'
> print(s)
> i = 0
> while i < n:
>     # print('en', j)
>     nuevo = ''
>     for j in range(len(s)):
>         left = j-1
>         right = (j+1)%len(s)
>         if s[left]==s[right]: nuevo += '-'
>         else: nuevo += '*'
>     s=''.join(nuevo)
>     print(s)
>     i += 1
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > Aquí hay una posible solución.
> >
> > ~~~
> > def procesa_cadena(cadena_entrada, iteraciones):
> >     """
> >     Toma una cadena_entrada y genera una nueva cadena con - y *
> >     que corresponde a caracteres que tienen caracteres idénticos
> >     adyacentes o no, respectivamente. Itera sobre este procedimiento
> >     con la cadena resultante el número indicado de iteraciones
> >     """
> >     print(cadena_entrada)
> >     longitud_cadena_entrada = len(cadena_entrada)
> >     anterior = cadena_entrada
> >     for i in range(iteraciones):
> >         nueva = ''
> >         # itera sobre los caracteres de la cadena anterior
> >         for j in range(longitud_cadena_entrada):
> >             izquireda = j-1
> >             derecha = (j+1) % longitud_cadena_entrada  # la última deberá tomar el primer elemento
> >             if anterior[izquierda] == anterior[derecha]:
> >                 nueva += '-'
> >             else:
> >                 nueva += '*'
> >         print(nueva)
> >         # guarda la nueva cadena como la anterior
> >         anterior = nueva   
> >
> > procesa_cadena('et cetera', 10)
> > ~~~
> > {: .language-python}
> > 
> > ~~~
> > etcetera
> > *****-***
> > ----*-*--
> > ---*---*-
> > --*-*-*-*
> > **-------
> > ***-----*
> > --**---**
> > *****-***
> > ----*-*--
> > ---*---*-
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

