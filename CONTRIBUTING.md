# Colaborando

[Las Carpentries][c-site] ([Software Carpentry][swc-site], [Data Carpentry][dc-site] y [Library Carpentry][lc-site]) son proyectos de código abierto,
y agradecemos las colaboraciones de todo tipo:
nuevas lecciones,
correcciones del material existente,
informes de errores,
y las revisiones de cambios propuestas, todas son bienvenidas.

## Acuerdo de colaboración

Al colaborar,
aceptas que podemos redistribuir tu trabajo bajo [nuestra licencia](LICENSE.md).
A cambio,
abordaremos tus informes de errores y/o evaluaremos tu propuesta de cambio tan pronto como podamos,
y te ayudaremos a convertirte en miembro de nuestra comunidad.
Todos los involucrados en [Las Carpentries][c-site]
aceptan cumplir con nuestro [código de conducta](CODE_OF_CONDUCT.md).

## Cómo contribuir

La forma más fácil de comenzar es informarnos de un problema
para poder corregirlo, como un error ortográfico,
algunas palabras no claras,
o un error.
Contribuir es una buena forma de presentarte
y conocer a algunos de los miembros de nuestra comunidad.

1. Si no tienes una cuenta de [GitHub][github],
    puedes [enviarnos comentarios por correo electrónico][email].
    Sin embargo,
    podremos responder más rápidamente si usas uno de los otros métodos descritos a continuación.

2. Si tienes una cuenta de[GitHub][github],
  o estás dispuesto a [crear una][github-join],
  pero no sabes como usar Git,
  puedes informar de problemas o sugerir mejoras al [crear un informe de error][issues] (**issue** en inglés).
  Esto nos permite asignar la tarea a alguien
  y seguirla en un hilo de discusión.

3. Si te sientes cómodo con Git,
    y te gustaría añadir o cambiar algo del material,
    puedes enviar una solicitud de inclusión (PR por sus siglas en inglés, **pull request**).
    Las instrucciones para hacerlo [se incluyen a continuación](#usando-github).

## Dónde contribuir

1. Si deseas cambiar esta lección,
    por favor trabaja en <https://github.com/swcarpentry/python-novice-gapminder/>,
    que se puede visualizar en <https://swcarpentry.github.io/python-novice-gapminder>.

2. Si deseas cambiar la lección de ejemplo,
    por favor trabaja en <https://github.com/carpentries/lesson-example>,
    que documenta el formato de nuestras lecciones
    y se puede ver en <https://carpentries.github.io/lesson-example>.

3. Si deseas cambiar la plantilla utilizada para la página web del taller,
    por favor trabaja en <https://github.com/carpentries-es/workshop-template-es>.
    La página de inicio de ese repositorio explica cómo configurar los sitios web de los talleres,
    mientras que las páginas adicionales en <https://carpentries-es.github.io/workshop-template-es>
    proporcionan más información sobre nuestros criterios de diseño.

4. Si deseas cambiar los archivos de estilo CSS, herramientas,
    o texto estándar HTML para lecciones o talleres almacenados en `_includes` o ` _layouts`,
    por favor trabaja en <https://github.com/carpentries/styles-es>.

## Qué aportar

Hay muchas maneras de contribuir,
desde escribir ejercicios nuevos y mejorar los existentes
hasta actualizar o completar la documentación
y enviando [informes de errores][issue]
sobre cosas que no funcionan, no son claras o faltan.
Si estás buscando ideas, por favor revisa la pestaña 'Issues' para
ver la lista de problemas para este repositorio,
o la de los problemas de los proyectos de [Data Carpentry][dc-issues],
[Software Carpentry][swc-issues] y [Library Carpentry][lc-issues].

Los comentarios sobre problemas y revisiones de solicitudes de inclusión son bienvenidos:
somos más inteligentes juntos que solos.
Los comentarios de principiantes y recién llegados son particularmente valiosos.
Es fácil para las personas que usan estas lecciones frecuentemente
olvidar lo impenetrable que pueden ser partes de este material;
por lo tanto, una nueva perspectiva es siempre bienvenida.

## Qué *No* contribuir

Nuestras lecciones ya contienen más material de lo que podemos cubrir en un taller típico,
por lo que normalmente *no* buscamos más conceptos o herramientas para agregarles.
Como regla general,
si quieres presentar una idea nueva,
debes (a) estimar cuánto tiempo tomará enseñarla
y (b) explicar lo que sacarías para darle espacio.
El primero anima a los contribuyentes a ser honestos acerca de los requisitos;
el segundo, pensar bien las prioridades.

Tampoco buscamos ejercicios u otro material que sólo se ejecute en una plataforma.
Nuestros talleres suelen contener una mezcla de usuarios de Windows, macOS y Linux;
para ser utilizable,
nuestras lecciones deben correr igualmente bien en las tres plataformas.

## Usando GitHub

Si eliges contribuir a través de GitHub, es posible que desees echarle un vistazo a
[Cómo contribuir a un proyecto de código abierto en GitHub][how-contribute].
Para gestionar los cambios, seguimos [el flujo de GitHub][github-flow].
Cada lección tiene dos mantenedores que revisan problemas y solicitudes de inclusión o invitan a otros que lo hagan.
Los mantenedores son voluntarios de la comunidad y tienen la última palabra sobre qué se acepta en la lección.
Para usar la interfaz web para contribuir a una lección deberás:

1. Bifurcar el repositorio original a tu perfil de GitHub.
2. En tu versión del repositorio, cámbiate a la rama `gh-pages` y
crea una nueva rama por cada cambio significativo que se vaya a a hacer.
3. Navega al archivo (o archivos) que desees cambiar en la misma rama y realiza los cambios necesarios.
4. Confirma todos los archivos cambiados en las ramas apropiadas.
5. Crea solicitudes de inclusión para cada una de tus distintas ramas
a la rama `gh-pages` dentro del repositorio origen.
6. Si recibes comentarios, realiza los cambios necesarios usando la rama específica de tu repositorio
bifurcado y la solicitud de inclusión se actualizará automáticamente.
7. Repite esos pasos cuanto sea necesario hasta que todos los comentarios se hayan atendido.

Cuando empieces a trabajar, por favor, asegúrate que tu rama `gh-pages` está al día con el repositorio original
antes de crear tu rama de ella.
Además, por favor sólo trabaja en la rama nueva creada y *no*
en el clon de la rama `gh-pages`.
Finalmente, copias públicas de todas las lecciones están disponibles en la rama `gh-pages` del repositorio
origen para referencia mientras se haga la revisión.

Cada lección tiene mantenedores que revisan problemas y solicitudes de inclusión
o invitan a otros que lo hagan.
Los mantenedores son voluntarios de la comunidad
y tienen la última palabra sobre qué se acepta en la lección.

## Otros recursos

Discusiones generales de [Software Carpentry][swc-site] y [Data Carpentry][dc-site]
están en la [lista de distribución de discusiones][discuss-list], 
a la cual todos son bienvenidos.
También puedes [contactarnos por correo electrónico][email].

[email]: mailto:admin@software-carpentry.org
[dc-issues]: https://github.com/issues?q=user%3Adatacarpentry
[dc-lessons]: http://datacarpentry.org/lessons/
[dc-site]: http://datacarpentry.org/
[discuss-list]: http://lists.software-carpentry.org/listinfo/discuss
[github]: https://github.com
[github-flow]: https://guides.github.com/introduction/flow/
[github-join]: https://github.com/join
[how-contribute]: https://egghead.io/series/how-to-contribute-to-an-open-source-project-on-github
[issues]: https://guides.github.com/features/issues/
[swc-issues]: https://github.com/issues?q=user%3Aswcarpentry
[swc-lessons]: https://software-carpentry.org/lessons/
[swc-site]: https://software-carpentry.org/
[c-site]: https://carpentries.org/
[lc-site]: https://librarycarpentry.org/
[lc-issues]: https://github.com/issues?q=user%3Alibrarycarpentry

