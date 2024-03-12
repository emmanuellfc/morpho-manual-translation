<!-- TRANSLATED by md-translate -->
# Tutorial

Para ilustrar cómo usar _morpho_, resolveremos un problema que involucre
Cristales líquidos nemáticos (NLC), fluidos compuestos de moléculas largas y rígidas
que posee una orientación molecular promedio local descrita por una unidad
Vector Field \ (\ Mathbf {n} \).
Gotas de NLC inmersas en un anfitrión
El fluido isotrópico como el agua se llama _tactoids_ y, a diferencia de las gotas
de, digamos, aceite en agua que forma esferas, los tactoides pueden adoptar alargados
formas.

Lo funcional a minimizar, la energía libre del sistema es bastante
complejo,

$$
\ begin {ecuación}
F = \ subbacial {\ frac {1} {2} \ int_ {c} k_ {11} \ izquierdo (\ nabla \ cdot \ mathbf {n} \ right)^{2}+k_ {22} (\ mathbf {
n} \ cdot \ nabla \ times \ mathbf {n})^{2}+k_ {33} \ izquierdo | \ mathbf {n} \ times \ nabla \ times \ mathbf {n} \ right |^{2} da
} _ \ text {Liquid Crystal Elastic Energy} \ Label {Eq: Free}
\ end {ecuación}
$$

$$
\ begin {ecuation_}
\ quad + \ subbacial {\ sigma \ int dl} _ \ text {s.t.}
\ End {Ecation_}
$$

$$
\ begin {ecuation_}
\ quad + \ subbacace {\ frac {w} {2} \ int \ left (\ mathbf {n} \ cdot \ mathbf {t} \ right)^{2} dl} _ \ text {Anchoring}
\ End {Ecation_}
$$

donde los tres términos incluyen ** elasticidad de cristal líquido ** que impulsa el alargamiento de la gota, ** superficie
tensión ** _ (s.t.) _ que se opone al alargamiento del límite y un
** Término de anclaje ** que impone una orientación preferida en el límite.
Necesitamos una restricción local, \ (\ mathbf {n} \ cdot \ mathbf {n} = 1 \), y también lo hará
imponer una restricción en el volumen de la gota.
Por simplicidad,
Resuelve este problema en 2d.
El código completo para este ejemplo de tutorial es
contenido en la carpeta `ejemplos/tactoide` en el repositorio.