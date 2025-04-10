# Autómatas
## Teoría de autómatas
Un autómata es una máquina **abstracta** (es decir un modelo que simula el comportamiento de una máquina real) que se utiliza para procesar información.
- La información se codifica en cadenas de símbolos
- Procesan cadenas de **entrada** y producen cadenas de **salida**
- Reciben símbolos de entrada **secuencialmente**
- El símbolo de salida en un instante dado depende de:
	- el último símbolo de entrada
	- la secuencia o cadena que ha recibido hasta ese instante
	- el **estado** en que se encuentra
- En un instante dado sólo pueden estar en un estado
- Formas de descripción: *gráfica matricial funcional*
> [!info] Estado de un autómata, número de estados, configuración y movimiento
> - El **estado de un autómata** es toda la información necesaria en un momento dado, para poder deducir, dado un símbolo de entrada en ese momento, cual será el símbolo de salida.
> - El autómata tendrá un determinado **número de estados**, que puede ser infinito, y se encontrará en uno u otro según sea la historia de símbolos que le han llegado.
> - La **configuración de un autómata** se define a su situación en un instante.
> - El **movimiento de un autómata** se define como el tránsito entre dos configuraciones.

Un autómata se define como:
$$
A = (E, S, Q, f, g)
$$
$$
\begin{align}
 & E = \{ \text{conjunto de entradas o vocabulario de entrada} \} \\
 & S = \{ \text{conjunto de salidas o vocabulario de salida} \} \\
 & Q = \{ \text{conjunto de estados} \} \\
 & f: E x Q \to Q \\
 & g: E x Q \to S
\end{align}
$$
- ***Tabla de transiciones***
	Supongamos $A=(E,S,Q,f,g)$ donde $E=\{ a,b \}$, $S=\{ 0,1 \}$, $Q=\{ q_{1},q_{2},q_{3} \}$ y las funciones $f$ y $g$ se pueden representar por:
	![[imgs/automatas.png| 200]]
	Así se tiene que $f=(a,q_{1})=q_{1}; g(a,q_{1})=0$
	Ambas funciones se pueden representar en la misma tabla
	![[imgs/automatas2.png| 100]]
- ***Máquina de Moore***
	El diagrama de Moore es un grafo orientado en el que cada nodo corresponde a un estado; y si $f(\epsilon, q_{i} ) = q_{j}$ y $g(\epsilon, q_{i} ) = s$ existe un arco dirigido del nodo $q_{i}$ al correspondiente $q_{j}$ , sobre el que se pone la etiqueta $\epsilon/ s$
	![[imgs/diagrama de moore.png| 200]]
	Para el ejemplo anterior
	![[imgs/diagrama de moore2.png| 200]]
## Autómatas traductores
Traducen una cadena de entrada en otra cadena de salida. Para esto, trabajan con **dos alfabetos**, que pueden o no ser iguales. Un **alfabeto de entrada** al cual pertenecen los símbolos de la cinta de entrada a la máquina; y un **alfabeto de salida** al cuál pertenecen los símbolos del patrón de salida que produce la máquina abstracta en función de lo que lee en la cinta de entrada.
![[imgs/maquinas abstractas.png| center]]

|Característica|Mealy|Moore|
|---|---|---|
|**Salida depende de**|Estado + Entrada|Solo Estado|
|**Cambio de salida**|Inmediato ante un cambio de entrada|Solo cuando cambia el estado|
|**Estados requeridos**|Menos estados generalmente|Más estados, ya que la salida es fija por estado|
|**Uso típico**|Diseños rápidos y reactivos|Diseños más estables y predecibles|
<mark style="background: #FF5582A6;">Se puede demostrar que dada una máquina de Mealy, siempre se puede encontrar una máquina de Moore equivalente</mark>, a costa de aumentar el número de estados
### Máquina de Mealy
Se observa un **digrafo** que permite representar gráficamente el comportamiento de una máquina de Mealy. Los nodos, representan los distintos estados en que se encuentra la máquina en un momento dado, los arcos representan las transiciones posibles entre un estado y otro, los rótulos de los arcos de la forma $x/y$ representan el símbolo que se lee en la cadena de entrada y el símbolo que se escribe en la cadena de salida.
$$
\begin{align}
\sum e=\{ 0,1 \}  \qquad \sum s=\{ p,i \} \qquad Q=\{ q_{0},q_{1} \}
\end{align}
$$

| Función de Transición                                                                                                                         | Función de Salida                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| $f: Q x\sum e \to Q \text{ sería...}$                                                                                                         | $g: Q x \sum e \to \sum s \text{ sería...}$                                                                                   |
| $$<br>\begin{align}<br>f(q_{0},0) & =q_{0} \\<br>f(q_{0},1) & =q_{1} \\<br>f(q_{1},0) & =q_{1} \\<br>f(q_{1},1) & =q_{0}<br>\end{align}<br>$$ | $$<br>\begin{align}<br>f(q_{0},0) & =p \\<br>f(q_{0},1) & =i \\<br>f(q_{1},0) & =i \\<br>f(q_{1},1) & =p<br>\end{align}<br>$$ |
Para la cadena de entrada $01001$, la cadena de salida sería: $piiip$.
- $q_{0}$ simboliza el estado en el que se encuentra la máquina si, hasta ese instante, se han leído un número par de unos en cadena de entrada
- $q_{1}$ representa el hecho de que se han leído un número impar de unos en la entrada
- La función $f$, permite transitar de un estado a otro en cuanto lee un 1 en la entrada (porque hay cambio de par a impar o visceversa), y no cambia de estado si lee un 0, ya que no cambia la salida
- La función $g$ genera salida correspondiente a ese instante, indicando si hasta ese momento se han leído un número par o impar de unos
**Matriz de transción/salida**

| $Q \|\sum e$    | 0           | 1           |
| --------------- | ----------- | ----------- |
| **$q_{0}$**     | $q_{0} / p$ | $q_{1} / i$ |
| **$q_{1}$**<br> | $q_{1} / i$ | $q_{0} / p$ |
### Máquina de Moore
En una máquina de Moore la función de transición de estados, no difiere de la dada para la Máquina de Mealy. La diferencia, **radica en la función de salida** $g$, que en este caso depende sólo del estado actual en que se encuentre la máquina en un instante dado.
$$
\begin{align}
g(q_{0}) & =p \\
g(q_{1}) & =i
\end{align}
$$
**Matriz de transción**

|                  | Matriz d    | e Transición | Matriz de Salida |
| ---------------- | ----------- | ------------ | ---------------- |
| **$Q \|\sum e$** | **0**       | **1**        | -                |
| **$q_{0}$**      | $q_{0} / p$ | $q_{1} / i$  | p                |
| **$q_{1}$**<br>  | $q_{1} / i$ | $q_{0} / p$  | i                |
Para el ejemplo, la cadena de entrada $01001$, la cadena de salida sería: $piiip$
## Autómatas reconocedores
Los autómatas reconocedores son máquinas abstractas que permiten reconocer si una palabra o cadena (o construcción sintáctica) dada como *input* a la máquina, pertenece a un lenguaje.
![[imgs/automatas reconocedores.png| center]]
### Autómatas de estado finito
Los autómatas o máquinas de Estados Finitos (AEF o AF o FSA) son máquinas reconocedoras de lenguajes.
![[imgs/AEF.png| center | 150]]
Un AF es un grafo dirigido que **tiene un estado inicia**l, **uno o más estados finales** y **un conjunto de transiciones o arcos rotulados** que hacen que la máquina se mueva de un estado a otro. Cualquier cadena que lleve a la máquina desde su estado inicial a un estado final, es una cadena válida en el lenguaje.

> [!important] AF
> Es posible demostrar que existe una relación biunívoca entre los AEF y los lenguajes regulares, de forma tal que para cada lenguaje regular existe, al menos una máquina de estados finitos que reconoce las palabras en el lenguaje; y viceversa. Esto implica también una relación directa entre los AEF y las gramáticas regulares o normales (Tipo 3).

#### Autómatas de Estados Finitos Deterministas
Se define AEFD como la tupla
$$
AFD = \left( \sum,q_{0},Q,F,f \right)
$$
donde:
$$
\begin{align}
 & \sum \text{ es el alfabeto de simobolos de entrada} \\
 & q_{0} \in Q \text{ es el estado inicial} \\
 & Q \text{ es el conjunto de estados} \\
 & F \subset Q \text{ es el conjunto de estado finales} \\
 & f \text{ es la funcion de transicion de estados definida como...}
\end{align}
$$
$$
f: Q x \sum \to Q
$$
⚠️ Es importante, que a diferencia de los autómatas traductores (Mealy y Moore), acá se define un estado inicial por donde empieza a operar la máquina en el reconocimiento de una cadena; y un conjunto de estados finales, en los cuáles la cadena se considera aceptada.
⚠️ A diferencia de los autómatas traductores, no tienen función de salida, ya que el único resultado que arroja un AEF es: la aceptación o no de la cadena de entrada.
![[imgs/algoritmo de implementacion AFD.png | center]]
El estado `0` es un estado de **sumidero** o de **captación global**. Se representa con líneas punteadas, en azul están las entradas. Podemos ver que al sumidero llegan todos pero nada sale.
#### Autómatas de Estados Finitos no Deterministas
El problema del no determinismo, es la presencia de múltiples arcos a partir de un estado con el mismo rótulo, de modo que se tiene opción en cuanto al camino a seguir en el reconocimiento de una cinta de entrada.
La diferencia con AFD es que los AFND:
1. La imagen de la función de transición en un conjunto de estados ($P(Q)$ es el conjunto de Partes de Q, osea cualquier subconjunto de estados). Esto indica que para un estado de partida y un símbolo de entrada leído en la cadena, existe más de un estado al que se puede transitar. 
2. Se aceptan transiciones-$\lambda$. Es decir, transitar de un estado a otro, sin leer nada en la cadena de entrada.

> [!attention] Lenguaje Reconocido por un AFND
> Para un AFND, se dice que el autómata acepta la cadena, si hay algún camino desde el estado inicial a un estado final; aunque puede haber otros caminos que no llegan a un estado final.

## Expresiones Regulares
Las expresiones regulares son una tercera forma de expresar lenguajes regulares. Tenemos una relación directa entre:
- Gramáticas regulares (G3) -> Generan lenguajes regulares
- Autómatas finitos (AFD) -> Reconocen los lenguajes regulares
- Expresiones regulares (ER) -> Expresan de forma consisa los lenguajes regulares
> [!info] Definción ER
> Sólo son expresiones regulares sobre un alfabeto $\lambda$, aquellas que se obtienen aplicando un número finito de veces las siguientes reglas:
> -  $\lambda$ es una ER
> - para cada $a \in \sum$, $a$ es una ER
> - si $\alpha$ y $\beta$ son ambas ER, $\alpha + \beta$es una ER 
> - si $\alpha$ y $\beta$ son ambas expresiones regurales, $\alpha.\beta$ es una ER (o simplemente $\alpha \beta$) 
> - si $\alpha$ es una expresión regular, $\alpha{^*}$ es una ER. (Aquí $*$ es 0 o más - Kleene) 
> - si $\alpha$ es una expresión regular, ($\alpha$) es una ER.

El **Teorema de Kleene**, expresa la relación biunívoca que existe entre expresiones regulares y autómatas de estados finitos. En particular:
> [!important] Teorema
> Sea L un lenguaje sobre un alfabeto $\sum$. $L$ es regular (puede expresarse mediante expresiones regulares), si y solo si, existe un AEF con alfabeto $\sum$ que acepta $L$. 
> Es decir: 
> - **Teorema del Análisis**: Todo lenguaje aceptado por un AEF, es regular.
> - **Teorema de Síntesis**: todo Lenguaje Regular es aceptado por un AEF.
### Operaciones con las expresiones regulares
$\alpha \text{ y } \beta$ son ER
1. Unión $\{ \alpha | \beta \} = \{ \alpha \} \cup \{ \beta \}$
2. Concatenación $\{ \alpha \beta \}=\{ \alpha \} \{ \beta \}$
3. Cierre u operación estrella 
$$\begin{align}
\{ \alpha \}{^*} \text{ denota las cadenas:} \\
 & \lambda \\
 & \alpha \\
 & \alpha \alpha \\
 & \alpha \alpha \alpha \\
 & \dots \\
 & \alpha \alpha \alpha \dots \alpha
\end{align}$$
4. Cierre positivo
$$\begin{align}
\{ \alpha \}{^+} \text{ denota las cadenas:} \\
 & \alpha \\
 & \alpha \alpha \\
 & \alpha \alpha \alpha \\
 & \dots \\
 & \alpha \alpha \alpha \dots \alpha
\end{align}$$
### Conversiones
![[imgs/conversionAEF-ER.png]]
![[imgs/conversionER-AEF.png]]
### Equivalencia de Autómatas
> [!info] Definción Equivalencia de Autómatas
> Dos autómatas $N=\left( \sum, q_{0},Q, F, f \right)$ y $D=\left( \sum,q'_{0}, Q',F', f' \right)$ son equivalentes si ambos reconocen el mismo lenguaje.
> $$
L(D)=L(N)
$$

El no determinismo **no es deseable**, dado que complica la implementación del reconocedor y puede llevar a un reconocimiento erróneo. Por lo tanto, la equivalencia de autómatas:
> [!caution] Equivalencia de Autómatas
> - Se basa en la construcción de subconjuntos
> - Cada estado de AFD contiene un conjunto de estados del AFND
> - $\forall \space AFND \space \exists \space AFD$ (AFD son casos particulares de AFND)
> - $AFND = (\sum,q_{0},Q,F,f)$ equivale a $AFD=\left( \sum,q_{0}',Q',F',f'\right)$
> - Es decir $AFND \equiv AFD / L(AFND) = L(AFD)$, si se cumple que:
> $$
> \begin{align}
>  & Q'  = 2^{|Q|} \text{ conjunto potencia } P(Q) \\
>  & q_{i}'  = [q_{i} \dots q_{f}] \implies q_{i}\dots q_{f} \subset Q' \\
>  & q_{0}'  = q_{0} \\
>  & F'  = q' \in Q' / q' \cap F \neq \emptyset \\
>  & f'(q'a)  = \cup_{q\in Q} f(qa) / q \in Q \wedge a \in \sum
> \end{align}
> $$

El algoritmo parte del concepto de que para todo AFND, existe un AFD equivalente y viceversa.
Así: 
- **(AFD -> AFND)** Dado un AFD, es fácil demostrar que este es un caso particular de un AFND, ya que es en sí mismo un autómata no determinista en el que $\forall q \in Q, a \in \sum, |f(q,a)|=1$ (cantidad de transiciones desde $q$ rotuladas por $a$); y no hay transiciones-$\lambda$. 
- **(AFND -> AFD)** Dado un AFND $N=\left( \sum, q_{0}, Q, F, f \right)$ se puede construir un AFD equivalente $D=\left( \sum, q_{0}', Q', F', f' \right)$ con el algoritmo expuesto anteriormente, el cual podemos sintetizar de la siguiente manera
	- Eliminar estados superfluos (no alcanzables o no llegan a un estado final)
	- Construir el conjunto $2^{|Q|}$ de estados combinados
	- Para cada estado de $2^{|Q|}$ y símbolos de entrada ver estados alcanzables
	- Eliminar los estados
		- No alcanzables (excepto el inicial)
		- Aquellos que sólo son alcanzados por los eliminados en el paso previo
		- Los duplicados (debe queda uno de ellos)
	- Construir el grado del AEFD
		- El grafo obtenido debe ser conexo
#### Ejemplos
![[imgs/ejemplo equivalencia de automatas.png| center]]
![[imgs/ejemplo2 equivalencia de automatas.png| center]]
Se puede observar que la lógica que sustenta al método tiene que ver con reunir en un único estado destino (agrupamiento de estados) aquellos dos o más destinos que convertían a un nodo en NO determinista. De forma de eliminar las bifurcaciones no deterministas en el autómata.
### Minimización de Autómatas
El algoritmo descripto para hallar el AFD equivalente a un AFND no nos asegura que el AFD que se construye sea el mínimo posible en términos de cantidad de estados y transiciones para reconocer un lenguaje.
Para hallar el autómata mínimo equivalente a un AFD dado, se debe aplicar el algoritmo de Minimización de AFD:
![[imgs/minimizacion de automatas.png| center]]
##### Descripción del algoritmo
1. **Partición inicial P en dos grupos $G'(F), G''(Q-F)$**: separar el conjunto cociente $P$, en dos subconjuntos de estados potencialmente equivalentes, el de los estados finales y el de los estados no finales.
2. **Para cada $G$ de $P$ (con más de un estado) obtener una nueva $P_{n}$** de modo que:
	1. $\forall q_{i}q_{j} \in G_{i}⇔\forall \alpha\in \sum / f(q_{i}, \alpha), f(q_{j}, \alpha) \in G$ o sea que la transición va hacia el mismo grupo de P
	2. sustituir $G$ en $P_{n}$ por el nuevo conjunto de subgrupos
	Aquí se pide que para cada par de estados en cada una de las clases de equivalencia $G_{i}$ (que tenga más de un estado), se evalúe si son equivalentes. Dos estados son equivalentes, si partiendo de ellos; y para cada uno de los símbolos del alfabeto, transitan hacia un estado de la misma clase de equivalencia $G$.
3. **Si $P_{n}=P$ (o indistinguible) entonces $P_{final}:=P$ e ir a (5.)**: si ya terminé de evaluar todas las posbiles equivalencias.
4. **Sino $P := P_{n}$ e ir a (2.)**
5. **Elegir en cada grupo de $P_{final}$, un $q_{i}$ como representante del grupo**: armo el autómata mínimo, tomando un estado de cada clase de equivalencia como representante.

La aplicación del algoritmo que hemos explicado aplicando sus pasos sobre la matriz de transición, puede realizarse también trabajando directamente sobre el dígrafo.
![[imgs/minimizacion de automatas2.png| center]]
Lo que hacemos es delimitar las particiones en el grafo (marcando regiones que agrupan a los nodos de una misma partición), y luego observar que transiciones salen de una región hacia otra.
#### Ejemplo
![[imgs/ejemplo minimizacion de automatas.png| center]]