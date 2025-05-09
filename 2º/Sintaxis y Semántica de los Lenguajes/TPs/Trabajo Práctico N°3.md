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

8. Dada la siguiente gramática, aplica una estrategia de análisis LR(1) para construir el árbol de derivación de la cadena “cbba” de manera ascendente (bottom-up). En cada paso, determina el símbolo leído en la entrada, el estado de la pila y el estado del árbol (o las reducciones aplicadas).
$$
\begin{align}
S  & \to Aa \\
A  & \to Ab \\
A  & \to c
\end{align}
$$
Empezamos con una forma extendida añadiendo $S'$
$$
\begin{align}
1- & \quad S' → S \\
2- & \quad S → A a \\
3- & \quad A → A b \\
4- & \quad A → c
\end{align}
$$

Pila:       \[0]
Entrada:    c b b a $

|Estado|Entrada →|Acción|
|---|---|---|
|0|c|cambiar a estado 2|
|2|b|reducir A → c|
|0|A|ir a estado 1|
|1|b|cambiar a estado 3|
|3|b|reducir A → A b|
|1|a|cambiar a estado 4|
|4|$|reducir S → A a|
|0|S|fin|
           S
          /   \
         A     a
       /   \
      A     b
       |
       c

## Análisis Semántico
### Semántica estática vs dinámica
9. Identifique el error que contienen los siguientes programas en C++ e indique de qué tipo es y en qué etapa se detecta: léxico, sintáctico, semántica estática o semántica dinámica. Corrija el error y compruebe su correcto funcionamiento.
```C++
#include <iostream>
using namespace std;

int main() {
    string nombre;
    cin << nombre; // ❌ Debería ser >> para leer datos de entrada. Error semántica estática
    cout << "¡Hola, " << nombre << endl;
}

///////////////////////////////////////////////////
int main() {
    string nombre;
    cin >> nombre;
    cout << "¡Hola, " << nombre << endl;
}
```

```C++
#include <iostream>
using namespace std;

int main() {
    int númeroDeUsuarios = 5;
    cout << númeroDeUsuarios << endl;
}
```

```C++
#include <iostream>
using namespace std;

#define uno 1

int a = dos; // ❌ 'dos' no está definido, error sintáctico
++a // ❌ fuera de función, error sintáctico

int main() {
    a = dos;
    cout << a;
}

/////////////////////////////////////////////////////
int a = uno;

int main() {
	++a;
	cout << a;
}
```

```C++
#include <iostream>
using namespace std;

void sumar(int a, int b) {
    return a + b; // ❌ función 'void' no puede retornar un valor, error semántico estático
}

int main() {
    sumar(3, 4);
}

////////////////////////////////////////////////////
void sumar(int a, int b) {
    cout << a + b << endl;
}

int main() {
    sumar(3, 4);
}
```

```C++
#include <iostream>
#include <cstring>
using namespace std;

int main() {
    char buffer[10];
    const char* text = "Estoy aprendiendo a detectar errores léxicos, sintácticos y semánticos";

    std::strcpy(buffer, text); // ❌ Desbordamiento, error sintáctico dinámico 
    std::cout << buffer << std::endl;

    return 0;
}

///////////////////////////////////////////////
int main() {
    char buffer[1000]; // Agrandamos el buffer
    const char* text = "Estoy aprendiendo a detectar errores léxicos, sintácticos y semánticos";

    strncpy(buffer, text, sizeof(buffer) - 1); // Copia segura limitada al tamaño del buffer
    buffer[sizeof(buffer) - 1] = '\0'; // Asegura terminación null
    std::cout << buffer << std::endl;

    return 0;
}
```

```C++
#include <iostream>
using namespace std;

int main() {
    char c = 'A';
    int* ptr = &c; // ❌ Conversión entre 'char*' y 'int*'. Error semántico estático
    cout << *ptr << endl;
    return 0;
}

////////////////////////////////////////////////
char* ptr = &c;
```

11. Indique si los siguientes programas en JavaScript compilan y ejecutan. Si hay error, identifique la causa y en qué etapa se producen (análisis léxico, sintáctico, semántica estática o semántica dinámica).

```JavaScript
function validarEmail(email) {  
  const regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;  
  return regex.test(email);  
}  
console.log(validarEmail("usuario@example.com"));
// Compila y ejecuta
```

```JavaScript
const x = 10; 
const y = 20; 
if (x === 10) { 
  var y = 30; // Error al declarar y como constante y despues declarlalo como variable. Error de semántica estática
  console.log("Dentro del bloque: " + y); 
} 
console.log("Fuera del bloque: " + y);
```

```JavaScript
let num = "10"; 
let result = num * 2; 
console.log("Resultado: " + result); 
result = num - "a"; // NaN pero ejecuta igual
console.log("Resultado: " + result);
// Compila y ejecuta
```

```JavaScript
function calculateSum(a, b) { 
    let sum = a + b; 
    return sum; 
} 
let total# = calculateSum(5, 10); // Error léxico #.
console.log("Resultado: " + total#);
```

