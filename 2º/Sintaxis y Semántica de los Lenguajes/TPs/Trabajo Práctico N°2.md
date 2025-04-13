# Máquinas Secuenciales y Autómatas
## Máquinas Abstractas
1. Dadas las cadenas de entrada $\{0010100,110011,00100\}$ procéselas con la máquina de Mealy dada, e indique la salida para cada caso. Determine cuál es la traducción que realiza la máquina.![[imgs/tp2ej1.png| center]]
2. Dibuje la máquina de Moore, equivalente a la máquina de Mealy del ejercicio anterior.
## Gramáticas regulares, expresiones regulares y autómatas de estado finito
3. Dada la expresión regular $(a | b.c){^*}$, indique cuales de las siguientes serían palabras inválidas: $a, bca, aa, bc, aabc, abc, aab$.
	$(a|bc){^*}$
4. Dado el lenguaje $L = \{ a^{2n} b^{2m} b / n, m > 0 \}$ escriba la expresión regular que lo representa.
	$aabbbb \space b$ -> cadena ejemplo
	$b$ -> minima cadena
	$(a.a){^*}(bb){^*}b$
5. Para el siguiente autómata determine, su matriz de transición de estados y la expresión normal (regular) equivalente.![[imgs/tp2ej5.png| center]]
$$
\begin{align} \\
 \text{Expresion regular} =  & b{^*}ab{^*}a(a+b){^*} \\ \\
f(q_{0}, a) = q_{1} \\
f(q_{0}, b) = q_{0} \\
f(q_{1}, a) = q_{2} \\
f(q_{1}, b) = q_{1} \\
f(q_{2}, a) = q_{2} \\
f(q_{2}, b) = q_{2}
\end{align}
$$

|             |  **a**  |  **b**  |
| :---------: | :-----: | :-----: |
| **$q_{0}$** | $q_{1}$ | $q_{0}$ |
| **$q_{1}$** | $q_{2}$ | $q_{1}$ |
| **$q_{2}$** | $q_{2}$ | $q_{2}$ |
   
6. Para la expresión regular $aa^{*}b(b|a)^{*}$ construya el AFD equivalente. Realice la descripción en forma gráfica, funcional y tabular.
![[imgs/tp2ej6.png | center | 200]]
$$
\begin{align} \\
 \text{Expresion regular} =  & aa{^*}b(a|b){^*} \\ \\
f(q_{0}, a) = q_{1} \\
f(q_{0}, b) = - \\
f(q_{1}, a) = q_{1} \\
f(q_{1}, b) = q_{2} \\
f(q_{2}, a) = q_{2} \\
f(q_{2}, b) = q_{2}
\end{align}
$$

|             |  **a**  |  **b**  |
| :---------: | :-----: | :-----: |
| **$q_{0}$** | $q_{1}$ |   $-$   |
| **$q_{1}$** | $q_{1}$ | $q_{2}$ |
| **$q_{2}$** | $q_{2}$ | $q_{2}$ |

7. Para la expresión regular $00^{*}1(1+00^{*}1)^{*}$ construya el AFD equivalente. Realice la descripción en forma gráfica, funcional y tabular.
   ![[imgs/tp2ej7.png | center | 200]]
$$
\begin{align} \\
f(q_{0}, 1) = - \qquad f(q_{1}, 1) = q_{2} \\
f(q_{0}, 0) = q_{1} \qquad f(q_{1}, 0) = q_{1} \\ \\

f(q_{2}, 1) = q_{2} \qquad f(q_{3}, 1) = q_{2} \\
f(q_{2}, 0) = q_{3} \qquad f(q_{3}, 0) = q_{3} \\
\end{align}
$$

|             |  **a**  |  **b**  |
| :---------: | :-----: | :-----: |
| **$q_{0}$** |   $-$   | $q_{1}$ |
| **$q_{1}$** | $q_{2}$ | $q_{1}$ |
| **$q_{2}$** | $q_{2}$ | $q_{3}$ |
|   $q_{3}$   | $q_{2}$ | $q_{3}$ |

8. Dada la gramática regular $G=\{\{S,A,B\},\{a\},P,S\}$, donde $P=\{S->λ, S->aA, S->aB, A->a, B->aA\}$, determine la expresión regular equivalente.
$$
\text{Expresion regular}= \lambda + aa + aaa
$$
![[imgs/tp2ej8.png| center | 150]]

9. Dibuje un AFD que reconoce el lenguaje generado por la gramática regular $G = (\{S,A, B, C, D, E\}, \{a, b, c\}, P, S)$, siendo $P$ el siguiente conjunto de producciones:
$$
\begin{align}
S & \to aA | bB | cC | a | \epsilon \\
A  & \to aA | bB | cC | a  \\
B  & \to aB | bA | b \\
C  & \to cD \\
D  & \to cE | c \\
E & \to cC
\end{align}
$$
![[imgs/tp2ej9.png | center | 250]]
10. Dada la siguiente especificación, dibuje el AFD que reconoce el lenguaje: $L = \{a^{n}cb^{m}/ n > 0 \text{ y } m ≥ 0 \}$
$$
\begin{align}
M  & = \left\{  Q, \sum, f, e_{0}, F \right\} \\
Q  & = \{  e_{0}, e_{1}, e_{2} \} \\
\sum  & = \{ a,b,c \} \\
e_{i} & = e_{0} \\
F & = \{ e_{2} \}
\end{align}
$$
![[tp2ej10.png | center | 200]]
11. Obtenga el AFD equivalente para el siguiente AFND, dibuje el autómata AFD indicando a cuáles nodos del AFND, representa cada nodo. Describa la tabla completa de transiciones $P(Q)$.![[imgs/tp2ej11.png | center]]

|                   | a                 | b       | c            |
| :---------------- | :---------------- | :------ | ------------ |
| $\{  \}$          | $-$               | $-$     | $-$          |
| $q_{0}$           | $q_{0}q_{1}q_{2}$ | $q_{2}$ | $q_{1}$      |
| $q_{1}$           | $-$               | $-$     | $q_{2}$      |
| $q_{2}$           | $-$               | $q_{2}$ | $q_{1}$      |
| $q_{0}q_{1}$      | $q_{0}q_{1}q_{2}$ | $q_{2}$ | $q_{1}q_{2}$ |
| $q_{0}q_{2}$      | $q_{0}q_{1}q_{2}$ | $q_{2}$ | $q_{1}$      |
| $q_{1}q_{2}$      | $-$               | $q_{2}$ | $q_{1}q_{2}$ |
| $q_{0}q_{1}q_{2}$ | $q_{0}q_{1}q_{2}$ | $q_{2}$ | $q_{1}q_{2}$ |
![[tp2ej11 1.png | center | 250]]
12. Obtenga el AFD equivalente para el siguiente AFND, dibuje el autómata AFD indicando a cuáles nodos del AFND, representa cada nodo. Describa la tabla completa de transiciones $P(Q)$.
![[tp2ej12.png | center | 250]]

|                   | a                 | b            | Eliminar |
| :---------------- | :---------------- | :----------- | -------- |
| $\{  \}$          | $-$               | $-$          | X        |
| $q_{0}$           | $q_{0}q_{1}q_{2}$ | $-$          | >        |
| $q_{1}$           | $q_{2}$           | $q_{1}$      |          |
| $q_{2}$           | $-$               | $q_{1}$      | \*       |
| $q_{0}q_{1}$      | $q_{0}q_{1}q_{2}$ | $q_{1}$      | X        |
| $q_{0}q_{2}$      | $q_{0}q_{1}q_{2}$ | $q_{1}$      | X        |
| $q_{1}q_{2}$      | $q_{0}$           | $q_{1}q_{2}$ | X        |
| $q_{0}q_{1}q_{2}$ | $q_{0}q_{1}q_{2}$ | $q_{1}q_{2}$ | \*       |
![[tp2ej12 1.png | center]]
13. Obtenga el $AFD_{min}$ equivalente al siguiente AFD. Indique la secuencia de particiones obtenidas y dibuje el el AFD resultante.
![[tp2ej13.png | center | 250]]
$$
\begin{align}
G_{0} = &  \{ q_{0},q_{1},q_{2},q_{3} \} \\
G_{0} = & \{ q_{3} \} \quad G_{1} = \{ q_{0},q_{1},q_{2} \} \\
\text{por a} \to G_{0} =  & \{ q_{3} \} \quad G_{1} = \{ q_{0},q_{2} \} \quad G_{2} = \{ q_{1} \}
\end{align}
$$
## Autómatas de pila
15. Defina el $APD=\{Q,\sum,\Gamma,\delta,q_{0},z_{0} \}$, donde $Q={q_{0},q_{1},q_{2}}$, $\sum=\{a,b,c\}$, $\Gamma = \{\#,z_{0}\}$, quereconoce el lenguaje $L =\{a^{n}b^{n}c / n \geq 1\}$ por vaciado de pila.
16. Defina el $APD=\{Q,\sum,\Gamma,\delta,q_{0},z_{0} \}$, donde $Q={q_{0},q_{1},q_{2}}$, $\sum=\{a,b,c\}$, $\Gamma = \{\#,z_{0}\}$, quereconoce el lenguaje $L =\{a^{n}b^{2n}c / n \geq 1\}$  por vaciado de pila y por alcanzar el estado final.
17. Defina el APD que reconoce el lenguaje $L =\{X^{n}Y^{n} / n \geq 0\}$  por vaciado de pila y por alcanzar el estado final.
18. Indique si los siguientes AP son Deterministas ó No Deterministas. Justifique.
![[tp2ej18.png | center]]
19. Dada la gramática independiente del contexto $G=\left( N,\sum,P,S \right)$, donde $N=\{S,A,B\}$, $\sum=\{0,1,c\}$ y $P=\{S \to 0S0 | 1S1 | cA; A \to cB; B \to ca | \epsilon\}$, aplique el algoritmo de la transformación para obtener el APND que reconoce el lenguaje $L={w.(c)^{2n}.w^{-1} / w \in \{0,1\}^{*}, n>=1}$.