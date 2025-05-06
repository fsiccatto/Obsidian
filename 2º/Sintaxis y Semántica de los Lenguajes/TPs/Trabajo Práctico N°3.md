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

3. Trabaje en ANTLR Lab con la gramática ANTLR4 del lenguaje C, para obtener los árboles de análisis sintáctico de los siguientes enunciados. A partir del árbol generado, identifique si hay algún error léxico o sintáctico, e identifique en qué etapa se detecta (lexer o parser). ANTLR Lab se encuentra disponible en línea en https://antlr.org
``` C
int miFunc() {
	int * ?ptr,
	x=10;
	ptr = &x;
}
```

``` C
int main() {
	printf "Hola, mundo!";
}
```

``` C
int main(){
	while(true){
		++a;
		If (a>100) break;
	}
}
```

``` C
int main() {
	switch(1) {
		case 1: printf("Uno");
		default: printf("Por defecto");
	}
}
```

4. Exprese la siguiente gramática EBNF como una gramática en notación ANTLR4; y genere en ANTLR Lab los árboles de derivación para 2 expresiones válidas en la gramática.
![[imgs/tp3ej4.png | center]]

## Análisis Top-Down y Bottom-Up
6. Identifique cuales de las siguientes gramáticas cumplen los requisitos de una gramática LL(1). En caso contrario indique qué requisitos no se cumplen en cada caso y qué tipo de transformaciones deberían aplicarse.
![[imgs/tp3ej6.png | center]]
7. 
8. Dada la siguiente gramática, aplica una estrategia de análisis LR(1) para construir el árbol de derivación de la cadena “cbba” de manera ascendente (bottom-up). En cada paso, determina el símbolo leído en la entrada, el estado de la pila y el estado del árbol (o las reducciones aplicadas).
$$
\begin{align}
S  & \to Aa \\
A  & \to Ab \\
A  & \to 'c'
\end{align}
$$
