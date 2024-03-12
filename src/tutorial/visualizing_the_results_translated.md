<!-- TRANSLATED by md-translate -->
## Visualización de resultados {#sec: visualización-resulta etiqueta = "Sec: visualizar resultos"}

_Morpho_ proporciona un sistema de gráficos altamente flexible, con un externo
Aplicación del visor _morphoview_, para habilitar visualizaciones ricas de
resultados.
Las visualizaciones generalmente involucran uno o más 'gráficos'
objetos, que actúan como un contenedor para que los elementos gráficos sean
desplegado.
Varios _graphics primitives_, como esferas, cilindros,
Las flechas, tubos, etc. se pueden agregar a un objeto 'gráficos' para hacer un
dibujo.

Ahora estamos listos para visualizar los resultados de la optimización.
Primero,
Dibujaremos la malla.
Porque estamos interesados en ver la malla
Estructura, dibujaremos los bordes (es decir, los elementos de grado 1).
El
La función para hacer esto se proporciona como parte del módulo `tram.
importado en la sección [módulos de importación] (./ importing_modules.md):

```javascript
var g=plotmesh(m, grade=1)
```

A continuación, crearemos un objeto 'Graphics` separado que contenga el
director.
Dado que el director \ (\ mathbf {n} \) es un campo vectorial unitario, y
El signo no es significativo (la energía elástica nemática es en realidad
invariante en \ (\ mathbf {n} \ to- \ mathbf {n} \)), una forma apropiada para
mostrar un solo director está como un cilindro orientado a lo largo de \ (\ mathbf {n} \).
Por lo tanto, haremos una función de ayudante que cree un `gráficos`
objeto y dibuja tal cilindro en cada punto de malla:

```javascript
// Function to visualize a director field
// m - the mesh 
// nn - the director Field to visualize
// dl - scale the director 
fn visualize(m, nn, dl) { 
    var v = m.vertexmatrix()
    var nv = m.count() // Number of vertices
    var g = Graphics() // Create a graphics object
    for (i in 0...nv) {
    var x = v.column(i) // Get the ith vertex
    // Draw a cylinder aligned with nn at this vertex
    g.display(Cylinder(x-nn[i]*dl, x+nn[i]*dl, aspectratio=0.3))
    }
    return g
}
```

Una vez que hayamos definido esta función, podemos usarla:

```javascript
var gnn=visualize(m, nn, 0.2)
```

Las variables \ (g \) y \ (GNN \) ahora se refieren a dos objetos gráficos separados.
Podemos combinarlos usando el operador \ (+\) y mostrarlos así:

```javascript
var gdisp = g+gnn
Show(gdisp)
```

<figure id="fig:FinalResult">
<div class="centering">
<img src="../Figures/Tutorial/2Visualize/out.png" style="width:3.5in" />
</div>
<figcaption><span id="fig:FinalResult"
label="fig:FinalResult"></span>Optimized mesh and director
field.</figcaption>
</figure>

La visualización resultante se muestra en la Fig. [4.5] (#Fig: FinalResult).