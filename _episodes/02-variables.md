---
title: "Variables y Asignación"
teaching: 10
exercises: 10
questions:
- "¿Cómo puede guardar datos en los programas?"
objectives:
- "Escribir programas que asignen valores escalares a variables y realicen cálculos con esos valores."
- "Rastrear correctamente cambios de valores en programas que usan asignación de escalares."
keypoints:
- "Usa variables para guardar valores."
- "Usa `print` para mostrar los valores."
- "Las variables persisten entre celdas."
- "Las variables deben ser creadas antes de ser utilizadas."
- "Las variables pueden ser usadas en cálculos."
- "Usa un índice para obtener un solo carácter de una secuencia de caracteres."
- "Usa un corte para obtener una parte de una secuencia de caracteres."
- "Usa la función incorporada `len` para encontrar la longitud de una secuencia de caracteres."
- "Python distingue mayúsculas de minúsculas."
- "Usa nombres de variables significativos."
---
## Usa variables para guardar valores.

*   **Variables** son nombres de valores.
*   En Python el símbolo `=` asigna el valor que se encuentra a la derecha al nombre que se encuentra a la izquierda.
*   La variable es creada en el momento que se le asigna un valor.
*   Aquí, Python asigna una edad a la variable `age`
    y un nombre entre comillas a la variable `first_name`.

~~~
age = 42
first_name = 'Ahmed'
~~~
{: .language-python}

*   Nombres de variables
    * puede contener **sólo** letras, dígitos y guión bajo  `_` (habitualmente usado para separar palabras en nombres largos de variable)
    * no se puede comenzar con un dígito
    * se **distingue mayúsculas de minúsculas** (age, Age and AGE son tres variables diferentes)
*   Los nombres de variables que comiencen con un guión bajo `__alistairs_real_age`  tienen un significado especial 
    , por lo cual no lo usaremos hasta que comprendamos la convención.

## Usa `print` para mostrar los valores.

*   Python tiene una función incorporada llamada `print` que muestra cosas como texto.
*   Llama a una función usando su nombre (por ejemplo, decirle a Python que la ejecute).
*   Proporciona valores a la función (es decir, algo que quieres mostrar) entre paréntesis.
*   Para agregar una secuencia de caracteres a la salida, se debe escribir el mismo entre comillas simples o dobles.
*   Los valores pasados a la función se denominan **argumentos**

~~~
print(first_name, 'is', age, 'years old')
~~~
{: .language-python}
~~~
Ahmed is 42 years old
~~~
{: .output}

*   `print` pone automáticamente un espacio simple entre los ítems para separarlos.
*   Y se hace a una nueva línea al final.

## Las variables deben ser creadas antes de ser utilizadas.

*   Si una variable aún no existe, o si el nombre ha sido mal escrito,
    Python informa un error. (A diferencia de otros lenguajes, que "suponen" un valor predeterminado).

~~~
print(last_name)
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-1-c1fbb4e96102> in <module>()
----> 1 print(last_name)

NameError: name 'last_name' is not defined
~~~
{: .error}

*   La última línea de un mensaje de error suele ser la más informativa.
*  Examinaremos los mensajes de error en detalle [later]({{ page.root }}/15-scope/#reading-error-messages).

> ## Las variables persisten entre celdas
>
> Tenga en cuenta que el orden de ejecución en las celdas es importante en un cuaderno (**notebook**) de Jupyter, no el orden 
> en que aparecen. Python recordará *todo* el código que se ejecutó anteriormente, incluidas las variables que hayas
>  definido, independientemente del orden en el cuaderno. Por lo tanto, si defines variables más abajo en el cuaderno y luego
> (re) ejecutas las celdas más arriba, estas definidas más abajo aún estarán presentes. Como ejemplo, crea dos celdas con el
>  siguiente contenido, en este orden:
>
> ~~~
> print(myval)
> ~~~
> {: .language-python}
>
> ~~~
> myval = 1
> ~~~
> {: .language-python}
>
> Si lo ejecutas en este orden, la primera celda dará un error. Sin embargo, si ejecutas la primera celda *después* de la segunda celda, 
> se mostrará `1`. Para evitar confusiones, puede ser de ayuda usar la opción del  `Kernel` -> `Restart & Run All` que
> borra el intérprete y ejecuta todo desde una pantalla limpia, yendo de arriba a abajo.
{: .callout}

## Las variables pueden ser usadas en cálculos.

*   Podemos usar variables en los cálculos así como si fueran valores.
    *   Recuerda, hemos asignado el valor `42`  a la variable `age` unas líneas arriba.

~~~
age = age + 3
print('Age in three years:', age)
~~~
{: .language-python}
~~~
Age in three years: 45
~~~
{: .output}

## Usa un índice para obtener un solo carácter de una secuencia de caracteres.

*   Los caracteres (letras individuales, números, etc.) en una secuencia de caracteres están  
    ordenados. Por ejemplo, la secuencia de caracteres `'AB'` no es lo mismo que `'BA'`. Porque en este orden, podemos tratar la secuencia de caracteres como una lista de caracteres.
*   Cada posición en la secuencia de caracteres (primero, segundo, etc.) recibe un número. A este número se le llama **índice** o, a veces, subíndice.
*   Los índices están numerados a partir del 0.
*   Usa el índice de la posición entre corchetes para obtener el carácter en esa posición.

![representación gráfica de como funciona el indexado]({{ site.baseurl }}/fig/2_indexing.svg)

~~~
atom_name = 'helium'
print(atom_name[0])
~~~
{: .language-python}
~~~
h
~~~
{: .output}

## Usa un corte para obtener una parte de una secuencia de caracteres.

*   Una parte de una secuencia de caracteres también es llamada **fragmento de secuencia de caracteres**. Un fragmento de secuencia de caracteres puede ser tan corto como
    un único carácter.
*   Un ítem en una lista es llamado elemento. Cada vez que tratamos una secuencia de caracteres como si
    fuese una lista, los elementos de una secuencia de caracteres son sus caracteres individuales.
*   Un corte es una parte de una secuencia de caracteres (o, de manera general, cualquier objecto similar a una lista). 
*   Tomamos un corte usando `[inicio:fin]`, donde `inicio` es reemplazado por el
    índice del primer elemento que queremos y `fin` es reemplazado por el índice del
    elemento justo después del último elemento que queremos.
*   Matemáticamente, podría decirse que se selecciona el corte `[inicio:fin)`.
*   La diferencia entre `fin` e `inicio` es la longitud del corte.
*   Tomar un corte no cambia el contenido de la secuencia de caracteres original. En cambio,
    el corte es una copia de una parte de la secuencia de caracteres original.

~~~
atom_name = 'sodium'
print(atom_name[0:3])
~~~
{: .language-python}
~~~
sod
~~~
{: .output}

## Usa la función incorporada `len` para encontrar la longitud de una secuencia de caracteres.

~~~
print(len('helium'))
~~~
{: .language-python}
~~~
6
~~~
{: .output}

*   Las funciones anidadas se evalúan de adentro hacia afuera,
     como en matemática.

## Python distingue mayúsculas de minúsculas

*   Python piensa que las letras mayúsculas y minúsculas son diferentes,
    así que `Nombre` y `nombre` son variables diferentes.
*   Existen convenciones para usar letras mayúsculas al comienzo de los nombres de las variables, por ahora nosotros usaremos letras minúsculas.

## Usa nombres de variables significativos.

*   A Python no le importa cómo nombras las variables siempre que obedezcan las reglas
   (caracteres alfanuméricos y guiones bajos).

~~~
flabadab = 42
ewr_422_yY = 'Ahmed'
print(ewr_422_yY, 'tiene', flabadab, 'años')
~~~
{: .language-python}

*   Usa nombres de variables significativas para ayudar a otras personas a comprender lo que hace el programa.
*   La "otra persona" más importante es tu futuro yo.

> ## Intercambiar valores
>
> Rellene la tabla que muestra los valores de las variables en este programa
> *después* de ejecutar cada instrucción.
>
> ~~~
> # Command # Value of x   # Value of y   # Value of swap #
> x = 1.0    #              #              #               #
> y = 3.0    #              #              #               #
> swap = x   #              #              #               #
> x = y      #              #              #               #
> y = swap   #              #              #               #
> ~~~
> {: .language-python}
> > ## Solución
> >
> > ~~~
> > # Command # Value of x # Value of y # Value of swap #
> > x = 1.0    # 1.0          # not defined  # not defined   #
> > y = 3.0    # 1.0          # 3.0          # not defined   #
> > swap = x   # 1.0          # 3.0          # 1.0           #
> > x = y      # 3.0          # 3.0          # 1.0           #
> > y = swap   # 3.0          # 1.0          # 1.0           #
> > ~~~
> > {: .output}
> > 
> > Estas tres líneas intercambian los valores en `x` e` y` usando la variable `swap`
> > como almacenamiento temporario. Esto es bastante común en lenguajes de programación.
>{: .solution}
{: .challenge}

> ## Predicción de Valores
>
> ¿Cuál es el valor final de 'position' en el programa a continuación?
> (Intenta predecir el valor sin ejecutar el programa,
> luego comprueba tu predicción)
>
> ~~~
> initial = 'left'
> position = initial
> initial = 'right'
> ~~~
> {: .language-python}
> > ## Solución
> >
> > ~~~
> > 'left'
> > ~~~
> > {: .output}
> >
>> A la variable `initial` se le asigna el valor `'left'`.
> > en la segunda línea, la variable `position` también recibe
>> como valor la secuencia de caracteres `'left'`. En la tercera línea, la variable `initial` toma el valor
>>  `'right'`, y la variable `position` conserva su valor de secuencia de caracteres
>>  `'left'`.
>{: .solution}
{: .challenge}

> ## Desafío
>
> Si asignas  `a = 123`,
> ¿Qué sucede si intenta obtener el segundo dígito de 'a' a través de 'a [1] `?
>
> > ## Solución
> > Los números no son secuencia de caracteres, por lo cual Python generará un error si intenta realizar una operación de índice en un
> > número. En la  [próxima lección de tipos de datos y conversión de tipos]({{ page.root }}/03-types-conversion/#convert-numbers-and-strings)
> > aprenderemos más sobre los tipos de datos y cómo convertir entre los diferentes tipos. Si quieres  el enésimo dígito de un número
> > puedes convertirlo en una secuencia de caracteres usando la función incorporada `str` y luego realizar una operación de índice en esa secuencia de caracteres.
> >
> > ~~~
> > a = 123
> > print(a[1])
> > ~~~
> > {: .language-python}
> > ~~~
> > TypeError: 'int' object is not subscriptable
> > ~~~
> > {: .error}
> > 
> > 
> > ~~~
> > a = str(123)
> > print(a[1])
> > ~~~
> > {: .language-python}
> > ~~~
> > 2
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Eligiendo un nombre
>
> ¿Cuál es el mejor nombre de variable `m`,` min` o `minutes`?
> Porqué?
> Sugerencia: piensa qué código preferiría heredar 
> de alguien que abandona el laboratorio:
>
> 1. `ts = m * 60 + s`
> 2. `tot_sec = min * 60 + sec`
> 3. `total_seconds = minutes * 60 + seconds`
>
> > ## Solución
> >
> > `minutes` es mejor que porque `min` podría significar algo como "mínimo"
> > (actualmente min es una función existente en Python que veremos más adelante).
> {: .solution}
{: .challenge}

> ## Práctica de corte
>
> ¿Qué muestra el siguiente programa?
>
> ~~~
> atom_name = 'carbon'
> print('atom_name[1:3] is:', atom_name[1:3])
> ~~~
> {: .language-python}
>
> > ## Solución
> >
> > ~~~
> > atom_name[1:3] is: ar
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Conceptos de corte
>
> 1.  ¿Qué hace `algo[inicio:fin]` ?
> 2.  ¿Qué hace `algo [inicio:]` (sin un valor después de los dos puntos)?
> 3.  ¿Qué hace `algo[:fin]` (sin un valor antes de los dos puntos)?
> 4.  ¿Qué hace `algo[:]` (solo dos puntos)?
> 5.  ¿Qué hace `algo[número:algún-número-negativo]` ?
> 6.  ¿Qué pasa cuando eliges un valor `fin` que está fuera de rango? (es decir, probar con  `atom_name[0:15]`) 
>
> > ## Soluciones
> >
> > 1. `algo[inicio:fin]` devuelve un corte desde `inicio` hasta un valor antes de `fin`
> > 2. `algo[inicio:]` devuelve un corte desde `inicio` hasta el final de ese `algo`
> > 3. `algo[:fin]` devuelve un corte desde el comienzo de ese `algo` hasta el valor anterior a `fin`
> > 4. `algo[:]` devuelve todo de `algo`
> > 5. `algo[número:algún-número-negativo]` devuelve un corte desde ese `número` hasta el `algún-número-negativo` desde el final de `algo`
> > 6. Si una parte del corte está fuera de rango, la operación no falla. `atom_name [0:15]` da el mismo resultado que `atom_name [0:]`.
> {: .solution}
{: .challenge}

