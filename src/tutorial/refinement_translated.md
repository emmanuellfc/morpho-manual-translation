<!-- TRANSLATED by md-translate -->
# Refinamiento

Ahora hemos resuelto nuestro primer problema de optimización de forma, y el
Se proporciona un guión de problema completo en la carpeta `Ejemplos/Tutorial`
Dentro del repositorio de git como `tutorial.morpho`.
El resultado que tenemos
obtenido en la Fig. [4.5] (#Fig: FinalResult) es, sin embargo, una resolución muy gruesa y muy gruesa
Solución que comprende solo un número relativamente pequeño de elementos.
Ganar
Una solución mejorada, necesitamos _refine_ nuestra malla.
Porque modificando
La malla también requiere que actualicemos otras estructuras de datos como campos
y selecciones, se utiliza un objeto especial `meshrefiner` para realizar el
refinamiento.

Para realizar el refinamiento nosotros:

1. Cree un objeto `meshrefiner`, proporcionándole una lista de todos los
`Mesh`,` Field` y `Selection` objetos (es decir, la malla y los objetos
que dependen directamente de él) que deben actualizarse:
`` `JavaScript
var mr = meshrefiner ([m, nn, bnd]);
// Establecer el refinador
`` `` ``
2. Llame al método `refine` en el objeto 'Meshrefiner` a realmente
realizar el refinamiento.
Este método devuelve un objeto `Diccionario`
Eso mapea los objetos viejos a los potencialmente recién creados.
`` `JavaScript
var refMap = Mr.Refine ();
// realizar el refinamiento
`` `` ``
3. Dígale a cualquier otro objeto que se refiera a la malla, campos o selecciones
para actualizar sus referencias usando `refmap`.
Por ejemplo,
Los objetos `OptimizationProblem` y` Optimizer` se actualizan típicamente
en este paso.
`` `JavaScript
para (el en [problema, sopt, fopt]) el.update (refmap);
// Actualizar el problema
`` `` ``
4. Actualice nuestras propias referencias
`` `JavaScript
m = refmap [m];
nn = refmap [nn];
bnd = refmap [bnd];
// actualizar variables
`` `` ``

<figure id="fig:Refinement">
<p><img src="../Figures/Tutorial/3Refine/out1.png" style="width:2in"
alt="image" /><img src="../Figures/Tutorial/3Refine/out2.png" style="width:2in"
alt="image" /><img src="../Figures/Tutorial/3Refine/out3.png" style="width:2in"
alt="image" /></p>
<figcaption><span id="fig:Refinement"
label="fig:Refinement"></span>Optimized mesh and director field at three
successive levels of refinement.</figcaption>
</figure>

Insertamos este código después de nuestra sección de optimización, que causa
_morpho_ para optimizar y refinar sucesivamente.

> El código completo que incluye el refinamiento está en la carpeta `ejemplos/tutoriales` dentro del repositorio de git como` tutorial2.morpho`

La resultante
Las formas optimizadas se muestran en la Fig. [4.6] (#Fig: refinamiento).

```
// Optimization loop
var refmax = 3
for (refiter in 1..refmax) {
  print "===Refinement level ${refiter}==="
  for (i in 1..100) {
    fopt.linesearch(20)
    sopt.linesearch(20)
  }

  if (refiter==refmax) break

  // Refinement
  var mr=MeshRefiner([m, nn, bnd]) // Set the refiner up
  var refmap=mr.refine() // Perform the refinement
  for (el in [problem, sopt, fopt]) el.update(refmap) // Update the problem
  m=refmap[m]; nn=refmap[nn]; bnd=refmap[bnd] // Update variables
}
```