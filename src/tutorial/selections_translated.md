<!-- TRANSLATED by md-translate -->
## Selecciones

A veces, queremos referirnos a partes específicas de un objeto `Mesh`:
elementos que coinciden con algún criterio, por ejemplo.
Objetos `selección '
permitirnos hacer esto.
Porque seleccionar el límite es muy común
Actividad, la función del constructor `selección` toma una opcional
argumento para hacer esto:

```
var bnd=Selection(m, boundary=true)
```

Por defecto, solo los elementos límite se incluyen en la 'selección'.
Para una malla con la mayoría de los elementos de grado 2 (facetas), los límites son
elementos de grado 1 (líneas);
para una malla con elementos de grado 3 (volúmenes),
Los límites son elementos de grado 2 (facetas).
Muy a menudo queremos el
Vértices mismos también, por lo que podemos llamar a un método para lograrlo:

```
bnd.addgrade(0)
```

Una vez que se ha creado una 'selección', puede ser útil visualizarlo
Para asegurarse de que se seleccionen los elementos correctos.
Hablaremos más de
Visualización en la sección
[Visualizando resultados] (./ Visualizing_The_Results.md), pero por ahora la línea

```
Show(plotselection(m, bnd, grade=1))
```

muestra una visualización de la malla con los elementos de grado 1 seleccionados
Rojo sombreado como se muestra en la fig.
[4.4] (#Fig: Boundary) {reference-type = "ref" reference = "fig: límite"}.

! [Selección] (../ figuras/tutoriales/2Visualize/Selection.png)
_ Seleccionar el límite de la malla_