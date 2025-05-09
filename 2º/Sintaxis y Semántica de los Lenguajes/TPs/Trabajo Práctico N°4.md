# Lenguajes y Traductores
## Compiladores, Intérpretes y Pseudo-compiladores
## Tabla de símbolos
2. Dado el siguiente código en C++, construya la tabla de símbolos correspondiente.
``` C++
#include <iostream>
using namespace std;

struct Persona {
    string nombre;
    int edad;
};

int x = 100;

int main() {
    int y = 10;
    Persona p1 = {"Carlos", 25};
    int* ptr = new int(30);
    Persona* p2 = new Persona{"Ana", 22};

    if (y > 5) {
        int z = 50;
        cout << "Variable de bloque: " << ++z << endl;
    }

    cout << p1.nombre << ", edad: " << p1.edad << endl;
    cout << p2->nombre << ", edad: " << p2->edad << endl;

    delete ptr;
    delete p2;

    return 0;
}
```

## Optimización de código
4. Identifique las optimizaciones posibles para los siguientes bloques de código.
``` C++
int sum(int a, int b) {
	int deadCode = a - b;
	return a+b;
}

int calculate() {  
    int x = 5 * 10;  
    return x;  
} 

void sumArray() {  
    int sum = 0;  
    for (int i = 0; i < 10; i++) 
        sum += i;  
} 

void checkValues(int a, int b, int c) { 
    if ((a * b + c) > 100 && (b * a / c) < 1000) { 
        printf("condición aceptada"); 
    } 
}
```

## Construcción de un analizador en ANLTR4 y JavaScript
5. Implemente un analizador que procese declaraciones, asignaciones y expresiones aritméticas simples escritas en JavaScript (desde un archivo de entrada input.js). El analizador deberá validar la sintaxis, mostrar la tabla de lexemas y tokens construida; y ejecutar el programa, evaluando las expresiones, asignando y calculando valores como lo haría un intérprete reducido de JavaScript.
