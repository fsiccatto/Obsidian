##### Corolarios de Teoremas de Funciones Lógicas
Se obtienen efectuando el producto miembro a miembro de la primera expresión por a o por a', como se indica a continuación:
$$
    af(a, b, c, \dots, n) = a[af(1, b, c, \dots, n) + \overline{a}f(0, b, c, \dots, n)]
$$
Aplicando distributiva al primer miembro:
$$
af(a, b, c, \dots, n) = af(1, b, c, \dots, n) \rightarrow \text{Primer Corolario}
$$
En cambio,
$$
    \overline{a}f(a, b, c, \dots, n) = \overline{a}[af(1, b, c, \dots, n) + \overline{a}f(0, b, c, \dots, n)]
$$
Aplicando propiedad distributiva al segundo miembro
$$
\overline{a}f(a, b, c, \dots, n) = \overline{a}f(0, b, c, \dots, n) \rightarrow \text{Segundo Corolario}
$$
Aplicando dualidad a los corolarios, se obtiene
$$
a+f(a, b, c, \dots, n) = a+ f(0, b, c, \dots, n) \rightarrow \text{Tercer Corolario}
$$
y
$$
\overline{a}+f(a, b, c, \dots, n) = \overline{a}+ f(1, b, c, \dots, n) \rightarrow \text{Cuarto Corolario}
$$
##### Demostación teorema 9
Aplicando el teorema 1 [[remote-repo/Arquitectura de Computadoras/Unidad 2#1- Dualidad]] a `f(a,b)`, se tiene:
$$
f(a, b) = af(1,b) + \overline{a}f(0,b)
$$
Aplicando nuevante el teorema 1 a `f(1, b)` y a `f(0, b)`, se tiene
$$
\begin{split}
f(1, b) &= af(1,b) + \overline{b}f(1,b) \\
f(0, b) &= af(0,b) + \overline{b}f(0,b) \\
\end{split}
$$
Reemplazando en la expresión inicial se obtiene
$$
f(a, b) = abf(1,1) + a\overline{b}f(1,0) + \overline{a}bf(0,1) + \overline{a}\overline{b}f(0,0)
$$
Se observa entonces que toda función puede expresarse como una **sumatoria de todos sus minterms**, afectados cada uno de ellos por un coeficiente que consiste en el valor de la función.

Teniendo en cuenta que f(a, b) es una función cualquiera del álgebra de Boole, su dual también lo será, por lo tanto:
$$
f(a, b) = [a+b+f(0,0)][a+\overline{b}+f(0,1)][\overline{a}+b+f(1,0)][ \overline{a}+\overline{b}+f(1,1)]
$$
Análogamente, toda función puede expresarse como una **productoria de todos sus maxterms**, afectados cada uno de ellos por un coeficiente que consiste en el valor de la función.