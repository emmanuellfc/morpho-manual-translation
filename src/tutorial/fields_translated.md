<!-- TRANSLATED by md-translate -->
## Campos

Habiendo creado nuestro dominio computacional inicial, ahora crearemos un
Objeto `Field` que representa el campo Director \ (\ Mathbf {n} \)::

```
var nn = Field(m, Matrix([1,0,0]))
```

Al igual que con el objeto `mesh` anterior, declaramos una variable, _nn_, referir
al objeto 'campo'.
Tenemos que proporcionar dos argumentos a 'Field': el
Objeto `mesh` en el que se define el 'campo' y algo para
inicializarlo.
Aquí, queremos que el director inicial tenga un
valor uniforme, por lo que podemos proporcionar `campo 'una` Matrix` constante
objeto.
Por defecto, _morpho_ almacena una copia de esta matriz en cada vértice
en la malla;
Sin embargo, los campos pueden almacenar información sobre elementos de cualquier
Grado (y almacene tanto más de una cantidad por grado e información
en varios grados al mismo tiempo).

Es posible inicializar un 'campo' con valores espacialmente variables por
Proporcionar una función _anónima_ a `campo 'así:

```
var phi = Field(m, fn (x,y,z) x^2+y^2)
```

Aquí, _phi_ es un campo escalar que toma el valor \ (x^{2}+y^{2} \).
El
** FN ** Se usa la palabra clave para definir funciones.