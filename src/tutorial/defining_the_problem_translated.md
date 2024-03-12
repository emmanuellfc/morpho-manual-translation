<!-- TRANSLATED by md-translate -->
## Definiendo el problema

Ahora recurrimos a configurar el problema.
Cada término en la energía
funcional [(1)] (../ tutorial.md#eq: free) está representado por un _functional_ correspondiente
objeto, que actúa sobre una `mesh` (y posiblemente un 'campo') para calcular un
cantidad integral como una energía;
Los objetos funcionales también son
responsable de calcular los gradientes de la energía con respecto a
Posiciones de vértice y componentes de los campos.

Tomemos los términos en [(1)] (../ tutorial.md#eq: gratis) uno por uno: para representar la elasticidad nemática nosotros
Crea un objeto 'Nematic`:

```
var lf=Nematic(nn)
```

El término de tensión superficial implica la longitud del límite, por lo que necesitamos
un objeto `longitud`:

```
var lt=Length()
```

El término de anclaje no tiene un tipo de objeto incorporado simple, pero nosotros
puede usar un objeto `LineIngal` general" para lograr el resultado correcto.

```
var la=LineIntegral(fn (x, n) n.inner(tangent())^2, nn)
```

Observe que tenemos que proporcionar una función que la integrandia será
llamado por `LineIngal` cuando evalúa la integral.
Integrar
Las funciones se llaman primero con las coordenadas locales (como una 'matriz'
objeto que representa un vector de columna) y luego el local interpolado
valor de cualquier número de `campos '.
También hacemos uso del especial
función `tangent ()` que localmente devuelve una tangente local a la línea.

También necesitamos imponer restricciones.
Se puede usar cualquier objeto _functional_
igualmente bien como una energía o una restricción, y por lo tanto creamos un
Objeto `Normsq` (Norm cuadrado) que se utilizará para implementar el local
restricción vectorial unitaria en el campo Director:

```
var ln=NormSq(nn)
```

y un objeto de 'área' para la restricción global.
Esto es realmente un
restricción fija el volumen de fluido en la gota, pero como estamos en
2D que se convierte en una restricción en el área de la malla:

```
var laa=Area()
```

Ahora tenemos una colección de objetos funcionales que podemos usar para definir
el problema.
Hasta ahora, no hemos especificado qué funcionales son energías
y que son restricciones;
ni hemos especificado qué partes de la malla
Los funcionales deben ser evaluados.
Toda esa información es
recopilado en un objeto 'OptimizationProblem`, que ahora crearemos:

```
// Set up the optimization problem
var W = 1
var sigma = 1

var problem = OptimizationProblem(m)
problem.addenergy(lf)
problem.addenergy(la, selection=bnd, prefactor=-W/2)
problem.addenergy(lt, selection=bnd, prefactor=sigma)
problem.addconstraint(laa)
problem.addlocalconstraint(ln, field=nn, target=1)
```

Observe que algunos de estos funcionales solo actúan en una selección como
el límite y, por lo tanto, usamos el parámetro `selección 'opcional para
especificar esto.
También podemos especificar el prefactor del funcional.