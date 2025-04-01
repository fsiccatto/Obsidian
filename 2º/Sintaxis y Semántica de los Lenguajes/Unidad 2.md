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
La importancia del uso de los autómatas en la lingüistica computacional, radica en que este tipo de máquinas abstractas puede ser utilizada para implementar diversas tareas, tales cómo traducir una cadena de entrada en otra de salida o reconocer si una cadena pertenece o no a un lenguaje. Además, el comportamiento de estos modelos abstractos puede ser fácilmente descripto por un algoritmo, por lo que es muy fácil programar autómatas para incorporarlos a un compilador (o traductor).
## Autómatas traductores
Traducen una cadena de entrada en otra cadena de salida. Para esto, trabajan con **dos alfabetos**, que pueden o no ser iguales. Un **alfabeto de entrada** al cual pertenecen los símbolos de la cinta de entrada a la máquina; y un **alfabeto de salida** al cuál pertenecen los símbolos del patrón de salida que produce la máquina abstracta en función de lo que lee en la cinta de entrada.
![[imgs/maquinas abstractas.png| center]]
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

> [!important] AEF
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
