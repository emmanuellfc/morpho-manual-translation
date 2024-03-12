<!-- TRANSLATED by md-translate -->
## Crear la malla inicial

<figure id="fig:Mesh">
<div class="centering">
<p><img src="../Figures/Tutorial/0ExampleMesh/meshgrade0.png" style="width:2in"
alt="image" /><img src="../Figures/Tutorial/0ExampleMesh/meshgrade1.png"
style="width:2in" alt="image" /><img
src="../Figures/Tutorial/0ExampleMesh/meshgrade2.png" style="width:2in"
alt="image" /></p>
</div>
<figcaption><span id="fig:Mesh" label="fig:Mesh"></span>A <em>Mesh</em>
object contains different kinds of element. In this example, the mesh
contains points, lines and area elements referred to by their
<em>grade</em>.</figcaption>
</figure>

Las mallas son regiones discretizadas del espacio.
La región más simple que podemos
Imagine es un _point_ o _vertex_ descrito por un conjunto de coordenadas
\ (((x_ {1}, x_ {2}, ...., x_ {d}) \) donde el número de coordenadas \ (d \) define
la dimensionalidad del espacio que se dice que el colector es
_embedded_ in. Desde más de un punto, podemos comenzar a construir más
regiones complejas.
Primero, entre dos puntos podemos imaginar arreglar un
Regla imaginaria y dibujar una línea recta o _edge_ entre ellos.
Tres puntos definen un avión y también un triángulo;
por lo tanto podemos
Identificar el área bidimensional del plano limitado por el triángulo
como un _face_, como frente a un poliedro.
Usando cuatro puntos, podemos
Defina el volumen limitado por un tetraedro.
Cada uno de estos ** elementos **
tiene una dimensionalidad diferente que se ha presentado a _grade_ y un `mesh` puede completo
contienen elementos de muchos grados diferentes como se muestra en la Fig.
[4.2] (#fig: malla).

_Morpho_ proporciona varias formas de crear una malla.
Uno puede cargar un
malla a partir de un archivo, construya uno manualmente a partir de un conjunto de puntos, cree uno
de un poliedro, o del conjunto de niveles (contornos) de una función.

Para este ejemplo, utilizaremos un archivo de malla predefinido `disk.mesh`.
A
Crear un objeto de malla desde este archivo, llamamos a la función _mesh_ con
el nombre del archivo:

```javascript
var m = Mesh("disk.mesh")
```

Aquí, la palabra clave ** var ** le dice a Morpho que cree una nueva variable _m_,
que ahora se refiere al objeto _mesh_ recién creado.

<figure id="fig:InitialMesh">
<div class="centering">
<img src="../Figures/Tutorial/1Mesh/mesh.png" style="width:3.5in" />
</div>
<figcaption><span id="fig:InitialMesh"
label="fig:InitialMesh"></span>The initial mesh, loaded from
<code>disk.mesh</code>.</figcaption>
</figure>

La malla inicial es
representado en la Fig. [4.3] (#Fig: InitialMesh);
Proporcionaremos el código para realizar el
Visualización en la sección
[Visualizando los resultados] (./ Visualizing_The_Results.md).

Si abre el archivo `disk.mesh`, que puede encontrar en la misma carpeta
Como `tactoide.morpho`, encontrarás que tiene un formato legible humano simple:

```
vertices

1 -1. 0. 0 
2 -0.951057 -0.309017 0
...

edges
1 8 2 
2 2 4
...

faces
1 8 2 4 
2 8 4 6
...
```

El archivo se divide en secciones, cada uno describiendo elementos de un
Grado diferente.
Cada línea comienza con un delimitador de sección como
como _Evertices_, _Edges_ o _faces_, o con una ID.
Los vértices son entonces
definido por un conjunto de coordenadas;
Los bordes y las caras se definen por
proporcionando las respectivas ID de vértice.