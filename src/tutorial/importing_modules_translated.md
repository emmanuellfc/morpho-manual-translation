<!-- TRANSLATED by md-translate -->
## Módulos de importación

_Morpho_ es un sistema modular y, por lo tanto, normalmente comenzamos nuestro programa por
decir _morpho_ los módulos que necesitamos para que estén disponibles para que nosotros
usar.
Para hacerlo, utilizamos la palabra clave 'import' seguida del nombre del
módulo:

```javascript
import meshtools
    import optimize
    import plot
```

También podemos usar la palabra clave `import` para importar archivos de programa adicionales
para ayudar en modularizar grandes programas.
Estos son los módulos que
Use para este ejemplo:

| Módulo | Propósito
| ------------- | -----------------------------------
-------
| `MeshTools` | Código de utilidad para crear y refinar mallas
| `Optimize` | realizar optimización
| `Plot` | Visualizar los resultados