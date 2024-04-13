# Demostración Matemática
La proposición universal:
$$\forall x:P(x) \to Q(x)$$
- Puede resultar verdadera -> Demostración: Métodos
- Puede resultar falsa -> Refutación: Contraejemplo
## Métodos de Demostración
Una demostración de una proposición universal verdadera es un argumento sistemático que establece la veracidad de la misma.
Si $\forall x:P(x) \to Q(x)$ es una proposición **verdadera**, los métodos de demostración son:
#### Directo
Se parte de la verdad de $\forall x:P(x)$ y usando definiciones, leyes y propiedades ya demsotradas se debe llegar a la verdad de $\forall x:Q(x)$.
#### Por Contrarrecíproco
Se prueba el método directo que $\forall x:(-Q(x)\to-P(x))$ es verdadera.
#### Por Contradicción (Absurdo)
Se parte de la verdad de $\forall x:(P(x) \wedge -Q(x))$ y usando definiciones, leyes y propiedades ya demostradas se debe llegar a una contradicción o absurdo $(R \wedge -R)$. 
#### De Existencia
Se utiliza para demostrar la verdad de $\exists x: P(x)$.
Basta con encontrar un elemento $a$ del universo tal que $P(a)$ sea verdadero (constructiva).
O bien se puede demostrar que $-[\exists x: P(x)]$ conduce a una contradicción (no constructiva).
#### Por Casos
Se utiliza para demostrar la verdad de proposiciones de la forma:
$$(p_{1} \vee p_{2} \vee \dots \vee p_{n}) \to q$$
para ello se utiliza su equivalencia lógica con la proposición:
$$(p_{1}\to q)\wedge(p_{2}\to q)\wedge\dots\wedge(p_{n}\to q)$$
## Refutación
Si $\forall x:P(x) \to Q(x)$ es una proposición **falsa**:
- Basta encontrar un elemento $a$ del universo del discurso, para el cual $P(a)$ es verdadera y $Q(a)$ falsa, lo cual permite demostrar que la proposición $\exists x:(P(x) \wedge -Q(x))$ es verdadera.
- Se está refutando una proposición universal mostrando un *contraejemplo*.
# Inducción Matemática
Dada la proposición $\forall n: P(n)$ en el dominio de los números naturales, la demostración por inducción de que $P(n)$ es verdadera para todo $n$, consiste en:
1. ***PASO BASE***: se muestra que $P(1)$ es verdadera.
2. ***PASO INDUCTIVO***: se muestra que el condicional $P(k) \to P(k+1)$ es verdadero para todo natural k (k fijo pero arbitrario).
Luego de completar estos pasos se habrá demostrado que $\forall n: P(n)$ es **verdadera** en el dominio de los números naturales.
> [!caution] Observaciones
> - En el paso inductivo, para demostrar que $P(k) \to P(k+1)$ es verdadera para todo natural k, se supone la verdad de $P(k)$ (***HIPÓTESIS INDUCTIVA***) y se demuestra la verdad de $P(k+1)$.
> - Recordemos que si el antecedente es verdadero y el consecuente también, entonces la proposición condicional será verdadera.
> - En el paso base, no necesariamente el primero elemento que hace verdad a la proposición es 1, $n \geq n_{0}$.
# Recurrencia
Una **sucesión** de números reales es una función $f: N_{0} \to R$ tal que $f(n) = a_{n}$ y se escribe $\{a_{n}\}_{n\in N}$ o bien $(a_{n})$.
También podemos representar una sucesión como un conjunto de elementos escritos en un renglón. $𝑎_{0},𝑎_{1},…,𝑎_{n}.$
Una sucesión de números reales $𝑎_{0},𝑎_{1},…$ se dice **recurrente** si existe una ecuación que relacione cada término $a_{k}$ con algunos de sus predecesores $𝑎_{k-1},𝑎{k-2},…, 𝑎{k-p}$ donde $𝑝$ es un número entero con $𝑘−𝑝 ≥0$. A esta ecuación se la denomina **relación de recurrencia de orden p**. Si los términos de una sucesión satisface una relación de recurrencia, entonces la sucesión se denomina recurrencia.
Una relación de **recurrencia con coeficientes lineal de orden p constantes** es una ecuación de la forma: