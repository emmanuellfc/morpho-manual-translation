<!-- TRANSLATED by md-translate -->
# Descripción general

_Morpho_ tiene como objetivo resolver la siguiente clase de problemas.
Considerar un
funcional,
$$ f = \ int_ {c} f (q, \ nabla q, \ nabla^{2} q, ...) d^{n} x+\ int _ {\ parcial c} g (q, \ nabla q,
\ nabla^{2} q, ...) d^{n-1} x, $$
donde \ (q \) representa un conjunto de campos definidos en un colector \ (c \) que
podría incluir escalar, vector, tensor u otras cantidades y sus
derivados \ (\ nabla^{n} q \).
Lo funcional incluye términos a granel y
en el límite \ (\ parcial c \) y también puede incluir propiedades geométricas
del colector, como las curvaturas locales.
Este funcional debe ser
minimizado desde una suposición inicial \ (\ {c_ {0}, q_ {0} \} \) con
respeto a los campos \ (q \) y la forma del colector \ (c \).
Global y
Las restricciones locales se pueden imponer tanto en \ (c \) como en \ (q \).

_Morpho_ es un entorno orientado a objetos: todos los componentes del
Problema, incluido el dominio computacional, los campos, los funcionales, etc.
todos están representados como objetos que interactúan entre sí.
Gran parte de
El esfuerzo por escribir un programa _morpho_ implica la creación y
manipulando estos objetos.
El entorno es flexible, modular y
Los usuarios pueden crear fácilmente nuevos tipos de objetos, o cambiar completamente cómo
_morpho_ funciona.

Este manual tiene como objetivo ayudar a los usuarios a aprender a usar _morpho_.
Proporciona
Instrucciones de instalación en [Capítulo 2] (installing_morpho.md), información sobre cómo ejecutar el
Programa en [Capítulo 3] (usando_morpho.md).
Se proporciona un tutorial detallado en
[Capítulo 4] (tutorial.md), que muestra cómo configurar y resolver un ejemplo
problema.
[Capítulo 5] (Working_with_meshes.md) proporciona información sobre el trabajo
con mallas y [Capítulo 6] (Visualization.MD) describe cómo visualizar los resultados
de su cálculo con _morpho_.
Los ejemplos proporcionados con morfo son
descrito en [Capítulo 7] (ejemplos.md).
Los capítulos restantes, que comprenden el
Segunda parte del manual, proporcione una guía de referencia para todas las áreas de
_morpho_ funcionality.