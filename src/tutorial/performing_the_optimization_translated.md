<!-- TRANSLATED by md-translate -->
## Realizar la optimización

Ahora estamos listos para realizar la optimización, para lo cual necesitamos un
Objeto `Optimizer`.
Estos vienen en dos sabores: un `sapeOptimizer` y un
`FieldOptimizer` que actúa respectivamente sobre la forma y un campo.
Nosotros
Crearlos con el problema y la cantidad en las que se supone que deben actuar:

```javascript
// Create shape and field optimizers
var sopt = ShapeOptimizer(problem, m)
var fopt = FieldOptimizer(problem, nn)
```

Habiendo creado estos, podemos realizar la optimización llamando al
Método `LineSearch` con un número especificado de iteraciones para cada uno:

```javascript
// Optimization loop
for (i in 1..100) {  
    fopt.linesearch(20)
    sopt.linesearch(20)
}
```

Cada iteración de un `linearch` evoluciona el campo (o forma) hacia abajo en el
gradiente del objetivo funcional, sujeto a restricciones y encuentra un
pasos de tamaño óptimo para reducir el valor de lo funcional.
Aquí nosotros
Alternar entre optimizar el campo y optimizar la forma,
realizar veinte iteraciones de cada uno, y en general haz esto cien
veces.
Estos números han sido elegidos bastante arbitrariamente, y si
Mire la salida, notará que _morpho_ no siempre se ejecuta
Veinte iteraciones de cada uno.
Más bien, en cada iteración verifica si
El cambio de energía satisface, $$ | e | <\ epsilon, $$ o,
$$ \ izquierda | \ frac {\ delta e} {e} \ right | <\ epsilon $$ donde el valor de
\ (\ epsilon \), la tolerancia de convergencia se puede cambiar configurando el
Propiedad `Etol` del objeto optimizador:

```javascript
sopt.etol = 1e-7 // default value is 1e-8
```

Algunas otras propiedades de un 'optimizador' que pueden ser útiles para que el usuario
ajustar son los siguientes:

|
Propiedad |
Valor predeterminado | Propósito
| ---------------------- | ------------------------ |-
--------------------------------------------------
-----------------------
|
`Etol` |
\ (1 \ Times10^{-8} \) |
Tolerancia energética (error relativo)
|
`ctol` |
\ (1 \ Times10^{-10} \) |
Tolerancia a la restricción (qué tan bien se satisfacen las restricciones)
|
`Stepsize` |
`0.1` | Stepsize para` relax` (cambiado por líneas en línea)
|
`StepLimit` |
`0.5` | Las medidas más grandes que puede tomar un` linearch` "
|
`maxConstraintsteps` |
`20` | Número de pasos que el optimizador puede tomar para garantizar que se cumplan las restricciones
|
`CALIENTE '|
`falso` | si imprimir la salida como ocurre la optimización