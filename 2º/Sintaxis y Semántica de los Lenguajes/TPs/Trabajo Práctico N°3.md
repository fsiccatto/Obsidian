# Máquinas y Lenguajes
## Analizadores Léxicos (Scanner o Lexer)
1. En base al documento con las reglas de sintaxis del lenguaje C (C-ANSI.pdf), complete la tabla de lexemas y tokens para las siguientes declaraciones.
``` C
if (x > y){
	z=x * y;
	++z;
}
```

| Lexema | Token |
|--------|--------|
| if | KEYWORD |
| ( | LPAREN |
| x | ID |
| > | GT |
| y | ID |
| ) | RPAREN |
| { | LBRACE |
| z | ID |
| = | ASSIGN |
| x | ID |
| * | MUL |
| y | ID |
| ; | SEMICOLON |
| ++ | INCREMENT |
| z | ID |
| ; | SEMICOLON |
| } | RBRACE |

``` C
int main() {
	int numero=10;
	float valor;
}
```

| Lexema | Token     |
| ------ | --------- |
| int    | KEYWORD   |
| main   | KEYWORD   |
| (      | LPAREN    |
| )      | RPAREN    |
| {      | LBRACE    |
| int    | KEYWORD   |
| numero | ID        |
| =      | ASSIGN    |
| 10     | NUMBER    |
| ;      | SEMICOLON |
| float  | KEYWORD   |
| valor  | ID        |
| ;      | SEMICOLON |
| }      | RBRACE    |
## Analizadores Sintácticos (Parser)
### Árboles de análisis sintáctico
2. En base los documentos con las reglas de sintaxis del lenguaje C (C-ANSI.pdf) y ECMAScript (Estandar de implementación de JavaScript – ECMAScript.pdf), construya el árbol de análisis sintáctico para los siguientes enunciados.
``` C
for ( i = 1; i <= n; i++ ) {
	sum += i;
}
```

| Lexema | Token |
|--------|--------|
| for | KEYWORD |
| ( | LPAREN |
| i | ID |
| = | ASSIGN |
| 1 | NUMBER |
| ; | SEMICOLON |
| i | ID |
| <= | LE |
| n | ID |
| ; | SEMICOLON |
| i | ID |
| ++ | INCREMENT |
| ) | RPAREN |
| { | LBRACE |
| sum | ID |
| + | PLUS |
| = | ASSIGN |
| i | ID |
| ; | SEMICOLON |
| } | RBRACE |

``` JavaScript
function saludo(nombre) {
	return “Hello, ${nombre}!”;
}
```

3. Trabaje en ANTLR Lab con la gramática ANTLR4 del lenguaje C, para obtener los árboles de análisis sintáctico de los siguientes enunciados. A partir del árbol generado, identifique si hay algún error léxico o sintáctico, e identifique en qué etapa se detecta (lexer o parser). 
Error `?`. Se detecta en la etapa de *lexer*
``` C
int miFunc() {
	int * ?ptr,
	x=10;
	ptr = &x;
}
```
![[imgs/tp3ej 3 1.png]]

Error en la función `printf()` ya que no tiene los paréntesis. Etapa *parser*
``` C
int main() {
	printf "Hola, mundo!";
}
```
![[imgs/tp3ej3 2.png | center]]
Error en la palabra reservada `if`. Error detectado por *lexer*
``` C
int main(){
	while(true){
		++a;
		If (a>100) break;
	}
}
```
![[imgs/tp3ej3 3.png| center]]
No hay errores
``` C
int main() {
	switch(1) {
		case 1: printf("Uno");
		default: printf("Por defecto");
	}
}
```
![[imgs/tp3ej3 4.png| center]]
4. Exprese la siguiente gramática EBNF como una gramática en notación ANTLR4; y genere en ANTLR Lab los árboles de derivación para 2 expresiones válidas en la gramática.
![[imgs/tp3ej4.png | center]]

## Análisis Top-Down y Bottom-Up
6. Identifique cuales de las siguientes gramáticas cumplen los requisitos de una gramática LL(1). En caso contrario indique qué requisitos no se cumplen en cada caso y qué tipo de transformaciones deberían aplicarse.
![[imgs/tp3ej6.png | center]]

$$
\begin{align}
S  & → A b | c D   \\
A  & → S d | e F   \\
D  & → A g | h   \\
F  & → i | j
\end{align}
$$
Tenemos recursividad a izquierda, por lo que ya no cumple con los requisitos de LL(1). Deberíamos eliminar la recursividad indirecta, reemplazando $S$ en $A$, para luego eliminar la recursividad a izquierda en $A$.

---
$$
\begin{align}
S  & → A B | A C  \\
A  & → a | b  \\
B  & → c | d  \\
C  & → e | f
\end{align}
$$

En este caso, no hay recursividad. Tampoco tenemos producciones con prefijos comunes. Por lo tanto, cumple con los requisitos y es una LL(1).

---

$$
\begin{align}
S  & → A B  \\
A  & → a A' | ε  \\
A'  & → a A' | ε  \\
B  & → b B' | ε  \\
B'  & → b B' | ε
\end{align}
$$
No tenemos recursividad a izquierda. Tampoco tenemos problemas con producciones con prefijo común. Por lo que es una gramática de tipo LL(1).

---

$$
\begin{align}
S  & → A B | A C  \\
A  & → a  \\
B  & → b C  \\
C  & → b | B
\end{align}
$$
Podemos reescribir la gramática para $C$ y para $S$:
$$
\begin{align}
S  & → A S'  \\
S'  & → B | C  \\
A  & → a  \\
B  & → b C  \\
C  & → b C'  \\
C'  & → b C' | ε
\end{align}
$$
Ahora sí vemos que no existe recursividad ni producciones con prefijo común. Por lo que es una LL(1).

---

7. Define en ANTLR4, una gramática LL(1), que describa la sintaxis de las sentencias de declaración y asignación de variables en JavaScript.
8. Dada la siguiente gramática, aplica una estrategia de análisis LR(1) para construir el árbol de derivación de la cadena “cbba” de manera ascendente (bottom-up). En cada paso, determina el símbolo leído en la entrada, el estado de la pila y el estado del árbol (o las reducciones aplicadas).
$$
\begin{align}
S  & \to Aa \\
A  & \to Ab \\
A  & \to 'c'
\end{align}
$$
