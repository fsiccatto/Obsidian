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
En una máquina de Moore la función de transición de estados, no difiere de la dada para la Máquina de Mealy. La diferencia, radica en la función de salida $g$, que en este caso depende sólo del estado actual en que se encuentre la máquina en un instante dado.
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
Existe una relación directa entre la jerarquía de gramáticas propuesta por Chomsky y las categorías de lenguajes generados.
De igual manera, existe una relación directa entre los tipos de lenguajes y los tipos de autómatas que los reconocen.
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
 & Q \text{ es el conjunto de estados} \\
 & q_{0} \subset Q \text{ es el estado inicial} \\
 & F \subseteq Q \text{ es el conjunto de estado finales} \\
 & f \text{ es la funcion de transicion de estados definida como...}
\end{align}
$$
$$
f: Q x \sum \to Q
$$
⚠️ Es importante, que a diferencia de los autómatas traductores (Mealy y Moore), acá se define un estado inicial por donde empieza a operar la máquina en el reconocimiento de una cadena; y un conjunto de estados finales, en los cuáles la cadena se considera aceptada.
⚠️ A diferencia de los autómatas traductores, no tienen función de salida, ya que el único resultado que arroja un AEF es: la aceptación o no de la cadena de entrada.
![[imgs/algoritmo de implementacion AFD.png | center]]
#### Autómatas de Estados Finitos no Deterministas
El problema del no determinismo, es la presencia de múltiples arcos a partir de un estado con el mismo rótulo, de modo que se tiene opción en cuanto al camino a seguir en el reconocimiento de una cinta de entrada.
La diferencia con AFD es que los AFND:
1. La imagen de la función de transición en un conjunto de estados ($P(Q)$ es el conjunto de Partes de Q, osea cualquier subconjunto de estados). Esto indica que para un estado de partida y un símbolo de entrada leído en la cadena, existe más de un estado al que se puede transitar. 
2. Se aceptan transiciones-$\lambda$. Es decir, transitar de un estado a otro, sin leer nada en la cadena de entrada.
![[imgs/AFND.png| center]]

> [!attention] Lenguaje Reconocido por un AFND
> Para un AFND, se dice que el autómata acepta la cadena, si hay algún camino desde el estado inicial a un estado final; aunque puede haber otros caminos que no llegan a un estado final.

## Expresiones Regulares
