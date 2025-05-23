# Traducción de la semántica de los enunciados
## Semántica de enunciados de declaración y asignación
1. Edite y ejecute los siguientes programas, observando la diferencia entre la declaración estática versus dinámica de tipos de datos.
```C++
#include <iostream>
using namespace std;

int main() {
    int x = 5;
    double y = x / 2;
    cout << "x: " << x << ", y: " << y << endl;
    return 0;
}
```

```js
let x = 5;
let y = x / 2;
console.log(`x: ${x}, y: ${y}`);
```
2. Edite y ejecute el siguiente programa en JavaScript. Indique qué muestra en la salida y por qué. Indique qué efecto tiene cambiar var por let en la declaración de x dentro del bloque if. Cambie el código para que la declaración de las variables globales sea constante.
```js
let x = 10;
let y = 5;

function test() {
    if (y > 1) {
        var x = 20; // Esta x es diferente a la x global debido a var y el alcance de función
    }
    console.log(x); // Imprimirá 20, ya que var x = 20 se eleva dentro de la función test
}

test();
console.log(x); // Imprimirá 10, ya que se refiere a la x global

// Si cambio var por let voy a obtener en ambos console.log(x) el valor de 20.
```
3. Indique si los siguientes códigos compilan y ejecutan. En caso de tener error, indique por qué se producen y corrija el error para que funcionen correctamente.
```C++
#include <iostream>
using namespace std;

int main() {
    const int x[5]; // Declaración de un array de 5 enteros constantes sin inicializar
    // const int x[5] = {0, 1, 2, 3, 4};
    for (int i = 0; i < 5; ++i) {
        x[i] = i; // Esto causará un error de compilación porque 'x' es const
        cout << x[i] << endl; // Se intentará imprimir valores no inicializados
    }
    return 0;
}
```

```js
const numeros = [1, 2, 3, 4, 5]; // referencia constante a un arreglo
// podemos poner let numeros = [1,2,3,4,5]
let otrosNumeros = [6,7,8, 9, 10];
numeros[0] = 100; // El primer valor de numeros es 100, numeros=[100,2,3,4,5], no cambia la referencia
numeros = otrosNumeros; // no puedo asignar un valor porque numeros es constante, cambia la referencia
console.log(numeros);
//TypeError: Assignment to constant variable.
```

## Semántica de evaluación de expresiones - precedencia y asociatividad
4. Indique el resultado de evaluar las siguientes expresiones en C/C++ (suponiendo que se ejecutan en secuencia).
```C++
int a = 10, b = 5, c = 2;
int x = 5, y = 10;
int* p = &x, *q = &y;

bool result1 = a + b * c > 10 && b - c < 5 || a / c == 5; // -> true
bool result2 = (p != q) && (*p < *q); // -> true

int result3 = *p++ + a++; // -> 15
int result4 = (a > b ? b : c) + (b > c ? a : b); // -> 16

bool result5 = (a += 2) > b && (b -= 1) < a; // -> true
bool result6 = (a > b ? b : c) + (b > c ? a : b); // -> 17 -> true
```
5. Indique el resultado de evaluar las siguientes expresiones en JavaScript (suponiendo que se ejecutan en secuencia).
```js
let a = 8, b = 4, c = 3;  
let x = 7, y = 15; 
let p=undefined, q=”JS”;

let result1 = a - b / c >= 6 || b * c % 2 == 0 && a % 3 !== 0; // true
let result2 = x-- < ++y && y % 5 === 0; // false
let result3 = a > b ? (b % 2 === 0 ? b / 2 : c) : (a * c); // 2
let result4 = typeof a + (b / 2) === "boolean5"; // false
let result5 = a -= b += 2; // 2
let result6 = p ?? q; // JS
```

## Semántica del control de fljo de ejecución: secuencia, bifurcaciones e iteraciones
6. Dados los siguientes programas en C/C++ evalúe si compilan y ejecutan correctamente. En ese caso, indique lo que muestran en la salida, fundamentando su respuesta. Si presentan algún error léxico, sintáctico, semántico o de lógica; indique el motivo y cómo corregirlo.
```c++
#include <iostream> 
using namespace std; 
int main() { 
	for (int i = 1; i <= 10; i += 2) 
		switch (i % 3) { 
			case 0: 
				cout << i << " es múltiplo de 3" << endl; 
				i++; 
				break; 
			case 1: 
				cout << i << " no es múltiplo de 3" << endl; 
			case 2: 
			        cout << i << " tiene residuo 2 al dividir por 3" << endl; 
			        i += 1; 
	} 
	return 0; 
}

/*
Sí, el programa compila y ejecuta sin errores. No hay errores léxicos, sintácticos ni semánticos.
Falta un break en el case1, lo que modifica el contador despues en case2
*/
```

```c++
#include <iostream> 
using namespace std; 
int main() { 
    int a = 1, contador = 0; 
    while (a < 50) { 
        if (a % 5 == 0) { 
            a += 7;   
            continue;   
        }  
        if (a % 7 == 0)  
            a *= 2;   
        else  
            a += 3; 
        contador++; 
        if (contador > 10) { 
            cout << "Se alcanzó el límite de iteraciones" << endl; 
            break; 
        } 
        cout << "a = " << a << endl; 
    } 
    return 0; 
}
/*
Compila y ejecuta correctamente. No tiene errores lexicos, sintácticos ni semánticos
a nunca toma el valor 5, 10, 15, ...
el break no se alcanza porque el bucle termina antes
*/
```

```c++
#include <iostream> 
using namespace std; 
int main() { 
    int i=1, j=100; 
    for (;;i += 2,j -= 10); 
    cout << i << " " << j; 
}
/*
Compila pero... No muestra nada por pantalla. Queda en bucle infinito, no hay corte.
*/
```