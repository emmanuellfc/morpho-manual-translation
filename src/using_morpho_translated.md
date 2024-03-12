<!-- TRANSLATED by md-translate -->
# Usando _morpho_

_Morpho_ es una aplicación de línea de comandos, como `python` o` lua`.
Puede
ser utilizado para ejecutar scripts o programas, que generalmente se les da el
_.morpho_ Extensión del archivo, o ejecutar interactivamente respondiendo al usuario
comandos.

## Ejecutar un programa

Para ejecutar un programa, simplemente ejecute Morpho con el nombre del archivo,

```
morpho5 script.morpho
```

_Morpho_ admite una serie de interruptores:

-Wor

: Ejecutar _morpho_ con más de un hilo de trabajador, p.
`-W 4` corre
Morpho con 4 hilos.

-D

: Mostrar el desmontaje del programa sin ejecutarlo.
_[Ver
Guía del desarrollador] _

-d

:   Modo de depuración.
Morpho se detendrá e ingresará al depurador cada vez que un
`@` se encuentra en la fuente.
_ [Ver guía del desarrollador] _

-pag

: Perfil La ejecución del programa.
Útil para identificar el rendimiento
cuellos de botella.
_ [Ver guía del desarrollador] _

## Modo interactivo

Para usar _morpho_ de manera interactiva, simplemente cargue la aplicación _erminal_
(o equivalente a su sistema) y escriba

```
morpho5
```

#### Interfaz de línea de comandos para morfo

! [Interfaz de línea de comandos para morfo] (./ figures/commandline.jpg)

Como se muestra en la figura anterior, (Fig. [Fig: CLI] (#-línea de comandos-interfaz-para-morfo)), será recibido por una breve bienvenida y un
Solicitud> Invitarlo a ingresar los comandos _morpho_.
Por ahora, prueba un
clásico:

```
print "Hello World"
```

que mostrará `Hello World` como salida.
Más información sobre el
El lenguaje _morpho_ se proporciona en la sección de referencia, especialmente
Capítulo [idioma] (./ reference/idioma.md) Si está familiarizado con los idiomas de C
como C, C ++, Java, JavaScript, etc. Las cosas deben ser bastante familiares.

Para ayudar al usuario, el contenido del manual de referencia está disponible
al usuario en modo interactivo como ayuda en línea.
Para obtener ayuda, simplemente
tipo:

```
help
```

o incluso más brevemente,

```
?
```

Para ver la lista de temas principales.
Para encontrar ayuda sobre un tema en particular, para
Ejemplo `for` bucles, simplemente escriba el nombre del tema después:

```
? for
```

Una vez que haya terminado de usar _morpho_, simplemente escriba

```
quit
```

para salir del programa y volver al shell.

El entorno interactivo tiene algunas otras características útiles para ayudar
el usuario:

*** Autocompletar. ** Como escribe, _morpho_ le mostrará cualquier sugerido
Comandos que cree que estás tratando de ingresar.
Por ejemplo, si tu
Tipo `V` La línea de comando mostrará la palabra clave` var`.
Para aceptar el
Sugerencia, presione la tecla Tab.
Múltiples sugerencias pueden ser
disponible;
Use las teclas de flecha hacia arriba y hacia abajo para rotar a través de ellas.
*** Historial de comando. ** Use las teclas de flecha para recuperar anteriormente
comandos ingresados.
Luego puede editarlos antes de ejecutarlos.
*** Edición de línea. ** Mientras escribe un comando, usa la izquierda y la derecha
flechas para mover el cursor;
Puedes insertar nuevos caracteres en
el cursor simplemente escribiéndolos o eliminando caracteres con el
Clave de `eliminar '.
Mantenga presionada la tecla `Shift 'mientras usa la izquierda y
teclas de flecha derecha para seleccionar texto;
Entonces puede usar`ctrl-c` para copiar
y `Ctrl-V` para pegar.
`CTRL-A` se mueve al comienzo de la línea y
`Ctrl-e` el final.