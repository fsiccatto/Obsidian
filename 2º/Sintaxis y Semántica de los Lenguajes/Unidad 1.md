## Jerarquía de Chomsky
![[imgs/jerarquia de chomsky.png| center]]
### Gramáticas de Tipo 0
También llamadas **gramáticas no restringidas**. Las reglas de derivación son de la forma:
$$\alpha \to \beta $$
siendo $\alpha \in (V_{N} \cup V_{T}){^+}$ y $\beta \in (V_{N} \cup V_{T}){^*}$, es decir la única restricción es que no puede haber reglas de la forma $\lambda \to \beta$ donde $\lambda$ es la cadena vacía. En la parte izquierda de cada producción, tiene que haber al menos un ***símbolo no Terminal***.
> [!example] Ejemplo
> $$\begin{align*}
> S &\to 0A \\
> 0A &\to B1 \\
> B &\to \lambda
> \end{align*}$$

### Gramática de Tipo 1
También llamadas **gramáticas sensibles al contexto**. En ellas las reglas de producción son de la forma:
$$\alpha S \beta \to \alpha \gamma \beta $$
siendo$S \in V_{N}$, $\alpha, \beta \in (V_{N} \cup V_{T}){^*}$ y $\gamma \in (V_{N} \cup V_{T}){^+}$.
Estas gramáticas se llaman sensibles al contexto, pues se puede reemplazar $S$ por $\gamma$ siempre que estén en el contexto $\alpha \dots \beta$.

La parte izquierda debe tener un símbolo no terminal, que puede estar acompañado por un contexto de símbolos terminales y no terminales. Si este contexto aparece, debe estar presente también en la parte derecha. Sólo se admite como regla compresora la regla $S \to \lambda$ (parte derecha tiene menos símbolos que la parte izquierda).
> [!important] Importante
> Si se admite otra regla compresora (por ej.: la regla nula) que no sea el axioma se dice que la gramática no es estricta.

Otra forma de definir las gramáticas sensibles al contexto, es aquella gramática formal con la única restricción que todas las producciones α -> β en P cumplan que |α| ≤ |β| donde |α| es la longitud de α. Se las llama ***gramáticas de longitud no decreciente***.
> [!example] Ejemplo
> $$\begin{align*}
> S &\to abc | aSBc \\
> cB &\to Bc \\
> bB &\to bb
> \end{align*}$$
> Genera el lenguaje: $\{ a{^n}b{^n}c{^n} : n \geq 1 \}$ que es dependiente del contexto
### Gramáticas de Tipo 2
Las gramáticas de tipo 2 también se denominan **gramáticas libres de contexto**. Sus reglas de producción tan sólo admiten tener un símbolo no terminal en su parte izquierda, es decir:
$$S \to \alpha$$
Siendo $S \in V_{N}$ y $\alpha \in (V_{N} \cup V_{T}){^+}$.
Se llama de contexto libre porque se puede cambiar $S$ por $\alpha$, independientemente del contexto que aparezca $S$. Es decir, a la hora de transformar una palabra en otra, el símbolo no terminal que se transforma no depende de los que estén a la izquierda o derecha de él.
Se dice que una G2 es ***Estricta***, si cumple estrictamente con la restricción de que la única regla compresora sea el axioma $S\to \lambda$. Si no cumple esta condición, se dice que la G2 es ***No Estricta***.
> [!example] Ejemplo
> $$\begin{align*}
> S &\to aSc | B \\
> B &\to bBc | \varepsilon  \\
> \end{align*}$$
> Genera el lenguaje: $\{ a{^n}b{^m}c{^{m+n}} : n \geq 0, m \geq 0 \}$.
### Gramáticas de Tipo 3
Las gramáticas del tipo 3 también denominadas regulares, lineales o normales comienzan sus reglas de producción por un símbolo terminal, que puede ser seguido o no por un símbolo no terminal, es decir son de la forma:
$$\begin{align*}
 S &\to \alpha B \\
 A &\to \alpha \\
 \end{align*}$$
 donde $S, A \in V_{N}$ y $\alpha \in V_{T}$.
 - Regulares por derecha: \<No Terminal> := \<Terminal>|\<Terminal>\<No Terminal>|$\lambda$
 - Regulares por izquierda: \<No Terminal> := \<Terminal>|\<No Terminal>\<Terminal>|$\lambda$
 > [!example] Ejemplo
> ![[imgs/ejemplo g3.png | center | 300]]

> [!summary] Utilización de gramáticas
> - **G3** 
> 	- Generan palabras
> 	- Regulares a derecha, izquierda o lineales
> - **G2** 
> 	- Generan frases
> 	- Las derivaciones se pueden representar mediante árboles
> - **G1**
> 	- Generan enunciados para lenguajes de programación, aunque las reglas se reducen a G2
> 	- Diferentes significados según contexto
> - **G0** -> solo se usan de manera teórica y no son aplicables a los lenguajes de programación

## Árboles de derivación
Son una forma de representar derivaciones. Se usan para definir árboles de derivación para gramáticas de tipo 1 o más restrictivas (tipos 2 y 3):
- El axioma se representa en la raíz del árbol
- Los nodos hojas del árbol son símbolos terminales de la gramática
- Los nodos intermedios son símbolos no terminales de la gramática
- Las derivaciones se representan creando tantos sucesores del símbolo no terminal de la izquierda como símbolos (T y N) aparezcan en la parte derecha de las producciones.
![[imgs/arboles de derivacion.png| center]]
## Ambigüedad
La ambigüedad tiene que ver con que existe más de una forma de generar una palabra a partir del axioma de una gramática. La ambigüedad puede surgir a varios niveles:
- **Sentencia** -> una sentencia es ambigua si tiene más de una derivación o árbol de derivación
	Ejemplo: $G_{B} = \{ \{ S \}, \{ A, B \}, A, \{ (A \to 1B), (A\to S1), (B\to 1) \} \}$
	La sentencia $11$ puede ser obtenida por las dos derivaciones siguientes:
	$A \to 1B \to 11$ y $A \to 11$
- **Gramática** -> una gramática es ambigua si tiene al menos una sentencia ambigua
	Ejemplo: La gramática $G_{B}$ es ambigua, ya que $11$ es una sentencia y es ambigua
- **Lenguaje** -> es ambiguo si existe una gramática ambigua que lo genera
	Ejemplo: El lenguaje $L_{B}=\{ 11 \}$ es ambiguo a que la gramática $G_{B}$ lo genera y es ambigua.
	- Si todas las gramáticas que generan un lenguaje son ambiguas, el lenguaje es inherentemente ambiguo.
		Ejemplo: El lenguaje $L_{B}$ no es inherentemente ambiguo ya que la siguiente gramática lo genera y no es ambigua.
	$$
	G_{9}=\{ \{ 1 \}, \{ A \}, A, \{ (A \to 11) \} \}
	$$
## Recursividad
Una gramática es **recursiva** cuando <mark style="background: #FF5582A6;">existe al menos una producción recursiva en ese conjunto de producciones</mark>. Cuando el primer símbolo del lado derecho de una producción es el mismo que el del lado izquierdo, se dice que la regla es Recursiva a Izquierda inmediata.
Ejemplo:
$$
\begin{align}
A  & \to AB | B \\
B  & \to \lambda
\end{align}
$$
✔ Las gramáticas que tienen reglas recursivas a izquierda, presentan problemas para algunos tipos de analizadores, por lo que se deben intentar eliminar este tipo de recursividad.
![[imgs/recursividad por izquierda.png| center | 300]]
## Notación BNF (*Backus Naur Form*)
La notación BNF (*Backus Naur Form*) incorpora los mismos elementos que hemos utilizado hasta ahora para escribir producciones.
> [!todo] BNF
> `\<no terminal\>` los no terminales se encierran entre signos \<y>
> `::=` las reglas de producción se leen como "se define como"
> `|` significa "o"

Ejemplo:
En el caso más sencillo podemos enumerar los elementos de un lenguaje finito por extensión a partir de una regla gramatical.
```
<digito> ::= 0|1|2|3|4|5|6|7|8|9
```
Una vez que se ha definido un conjunto básico de categorías sintácticas se pueden usar para construir estructuras más complejas.
```
<enunciado-iterativo> ::= while { <enunciado> }
```
También podemos usar esta regla para reglas recursivas
```
<cadena> ::= <letra>|<cadena><letra>
<letra> ::= a|b|c...
```
![[imgs/bnf regla recursiva.png| center | 300]]
Una gramática BNF completa es tan solo un conjunto de esta clase de reglas gramaticales, las cuales definen en conjunto una jerarquía que conduce a la categoría sintáctica de máximo nivel; es decir al axioma de la gramática. programación, la categoría sintáctica de máximo nivel es En un lenguaje de programación, la categoría sintáctica de máximo nivel es \<programa\>
✔ Las gramáticas BNF como las gramáticas de libre contexto (tipo 2) son equivalentes en cuanto a su poder descriptivo, su única diferencia radica en la forma rotacional.
## Notación EBNF (BNF Extendida)
La EBNF es una notación que define algunas extensiones o agregados sobre las gramáticas BNF. Estas extensiones no implican modificación sobre los alcances o restricciones de una gramática BNF, pero facilitan la escritura de reglas sintácticas complejas
Las extensiones son:
- `[...]` lo que está entre corchetes es un elemento **optativo**
- `{...}^+` los elementos que están entre llaves con + se pueden **repetir 1 o más veces**
- `{...}^*{}` los elementos que están entre llaves con/sin estrella se repiten **0 o más veces**
![[imgs/bnf vs ebnf.png| center | 400]]
## Diagramas de sintaxis, diagramas sintácticos o diagramas de ferrocarril
Un diagrama sintáctico, o diagrama de ferrocarril es una forma gráfica de expresar reglas EBNF (BNF Extendida). Cada regla se representa por un camino que va **de izquierda** (entrada) **a derecha** (salida). Los **círculos** en ese camino representan elementos terminales y los **recuadros** representan nodos no terminales.
![[imgs/diagramas.png| center | 200]]
Cualquier **trayecto válido** de la entrada a la salida representa una cadena válida para esa regla.
![[imgs/ejemplo diagramas.png| center | 300]]
## Notación en Expresiones
### Notación Infija
La sintaxis establece que el operador va entre los dos operandos. El problema con esto es que siempre tengo que avanzar hacia delante en el recorrido de la expresión para saber si puedo ir resolviendo partes o no.
✔ Es la más usual (requiere paréntesis)
Ejemplo $A + B * C$
### Notación Postfija o Polaca Inversa
La sintaxis establece que el operador va a la derecha de los operandos. Esta otra alternativa es deseable para los lenguajes interpretados porque el recorrido o su evaluación resulta más directo. Aquí nunca aparecen paréntesis.
✔ Evaluación muy eficiente
Ejemplo $ABC*+$
### Notación Prefija o Funcional
En este caso la regla sintáctica establece que el operador va a la izquierda de los operandos.
✔ Notación funcional
Ejemplo: $+A*BC$
![[imgs/expresiones.png|center]]
--- 
### Ejercicios importantes
Ejercicios de final
1. $$
L=\{ w/w \in (xyx){^{2n}}, n> 0 \}
$$
2. $$
M = \{ a{^n}b{^2}c{^n} / n\geq 0 \}
$$
3. $$
N = \{ zw / z \in ((10){^{-1}}){^n}, w \in (ab){^n}, n \geq 0 \}
$$