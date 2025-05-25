# Traducción de la semántica de datos
## Verificación y conversión de tipos
1. Los siguientes programas en C++ tienen problemas de verificación y conversión de tipos. Indique, si compilan y ejecutan, qué muestran en la salida y cómo se llega al resultado. Una vez identificado el problema corrija el código para que funcione adecuadamente.
```c++
#include <iostream> 
int main() { 
	float tempCelsius = 350.75;   
	// La temperature en Celsius se multiplica por 100 para enviarla en centésimas 
	short int tempTransmision = tempCelsius * 100;   
	std::cout << "Temperatura enviada: " << tempTransmision << "\n";
}
// Compila y ejecuta, pero muestra "Temperatura enviada: 0". Debido a que el short int tiene un rango entre -32,768 to 32,767 (2 bytes).
int tempTransimission = tempCelsius * 100;
```

```c++
#include <iostream> 
#include <cmath> 
int main() { 
	double capital = 10000.75, tasa = 0.057;   
	int anios = 5.2;   
	float interesCompuesto = capital * pow(1 + tasa, anios);   
	std::cout << "Total estimado: " << (int) interesCompuesto << "\n";   
}
// No compila ni ejecuta. La variable anios está definida como int pero está incilizada como float.
float anios = 5.2;
```

```c++
#include <iostream> 
void recorrerCadena(const int* str) { 
	while (*str != '\0') { 
		std::cout << *str << " ";  
		str++; 
	} 
} 
int main() { 
	const char* cadena="Hola Mundo"; 
	recorrerCadena(cadena);  
	return 0; 
}
// No compila ni ejecuta, debido a que la función espera como argumento un const int* pero recibe un const char*.
void reccorrerCadena(const char* str)
```
2. Los siguientes programas en JavaScript++ tienen problemas de verificación y conversión de tipos. Indique qué muestran en la salida y explique cómo se llega a ese resultado. Una vez identificado el problema corrija el código para que funcione adecuadamente.
```js
let precioBase = 49.99, impuesto = "0.21", tasaActualizacion = 1.015;   
let total = (precioBase + impuesto) * tasaActualizacion; 
console.log(`Precio actualizado: $${total.toFixed(2)}`); //NaN
// Esa es la salida debido a que la variable impuesto es un string y no un numero.
impuesto = 0.21
```

```js
let añosFuturos = 2.5;
let milisegundosPorAño = 365 * 24 * 60 * 60 * 1000;
let timestampFuturo = Date.now() + añosFuturos * milisegundosPorAño;
let fechaFutura = new Date(timestampFuturo); 
let diasSemana = ["Domingo", "Lunes", "Martes", "Miércoles", "Jueves", "Viernes", "Sábado"];
console.log(`Día de la semana en ${añosFuturos} años: ${diasSemana[fechaFutura.getDay()]}`);
// Devuelve Dia de la semana en 2.5 años: Lunes
```

```js
function calcularDistanciaEuclideana(x1, y1, x2, y2) { 
	return Math.sqrt((x2 - x1) ** 2 + (y2 - y1) ** 2); 
} 
let coords_1="2326"; 
let dist_1 = calcularDistanciaEuclideana(coords_1[0],coords_1[1],coords_1[2],coords_1[3]); 
console.log(`Distancia entre los puntos: ${dist_1}`); // Muestra 3
let coords_2="23.245"; 
let dist_2 = calcularDistanciaEuclideana(coords_2[0],coords_2[1],coords_2[2],coords_2[3]); 
console.log(`Distancia entre los puntos: ${dist_2}`); // Imprime NaN
// El problema es que al ser un string la coords_2, el valor coords_2[2]=.
let coords_2="23245"
```

## Equivalencias de tipos, subtipos y subrangos
3. Compruebe y compare los siguientes programas en JavaScript y C++. Observe qué, si bien ambos parecen equivalentes, tienen importantes diferencias vinculada a su semántica de tipos. Luego, responda lo solicitado, fundamentando su respuesta.
```js
let x = 42;  
let pi = 3.14; 
let y = 9007199254740991n; 
console.log(typeof x); 
console.log(typeof pi); 
console.log(typeof y); 
```

```c++
#include <iostream> 
#include <typeinfo>

Typedef short Temperatura;

using namespace std; 
	int main() { 
	int x = 42; 
	double pi = 3.14; 
	long y = 9007199254740991; 
	Temperatura t;
	
	cout << "Tipo de x: " << typeid(x).name() << endl; 
	cout << "Tipo de pi: " << typeid(pi).name() << endl; 
	cout << "Tipo de y: " <<  typeid(y).name() << endl; 
	return 0;
}
```

a. ¿JavaScript es un lenguaje de tipado dinámico? 
Si, porque no obliga a declarar explícitamente el tipo de dato. La verificación es en tiempo de ejecución.
b. ¿C/C++ son lenguajes de tipado estático?  
Si, hay que declarar el tipo de datos de forma explícita. La verificación es en tiempo de compilación.
c. En el código JavaScript, ¿Son x y pi de tipos equivalentes?  
Si, porque ambos son del tipo `number`.
d. En el código de C++,  ¿Son x y pi de tipos equivalentes? 
No, uno es de tipo `double` y el otro es `int`. Se representan distinto en memoria.
e. En el código JavaScript, ¿Es x de un subtipo del tipo de y?  
No, x es de tipo `number` y y es de tipo `BigInt`. Ambos son tipos de primitivos diferentes. No son equivalentes, ni uno es subtipo del otro.
f. En el código de C++,  ¿Es x de un subtipo del tipo de y?
No son formatos de representación diferente en memoria,
g. En el código de C++,  ¿Es x de un tipo subrango del tipo de y? 
No, para ser subrango debe tener un rango de valores menor, pero mantener el mismo formato de representación en memoria y el mismo conjunto de operaciones. En este caso, `int` no es un subrango de `long`
h. Agregue una línea al código en C++ para definir un alias de tipo, llamado Temperatura, del tipo `short`. Luego declare una variable tipada con este alias. ¿De qué tipo primitivo es la variable?
t es de tipo `short`
i. ¿Es posible en C/C++ y/o en JavaScript definir subrangos de sus tipos primitivos?
No, no es posible definir subrangos de sus tipos primitivos.

## Manejo de cadenas
4. El siguiente programa en C++ no compila. Indique cuál es el error y cómo corregirlo.
```c++
#include <iostream> 
const char* copiarCadena(const char * origen) { 
	const char *destino = origen; 
	return destino; 
} 
int main() { 
	const char *cadenaOrigen = "Hola Mundo"; 
	char *destino=copiarCadena(cadenaOrigen); 
	std::cout <<destino << std::endl; 
	return 0;
}
// El problema es que la funcion retorna un valor const char* y la variable destino está inicializada como char*, por lo que no compila.
const char* destino = copiarCadena(cadenaOrigen);
```

5. El siguiente programa en JavaScript no tiene el comportamiento esperado. Indique cuál es el error y cómo corregirlo.
```js
function reemplazarLetra(cadena, indice, nuevaLetra) { 
	cadena[indice] = nuevaLetra; // Intento de modificar la cadena en una posición específica 
	return cadena; 
} 
let texto = "Holado"; 
let nuevoTexto = reemplazarLetra(texto, 1, 'e'); 
console.log(`Texto modificado: ${nuevoTexto}`);
// No funciona debido a que las cadenas son inmutables, por lo que no se pueden modificar por índice como un array
function reemplazarLetra(cadena, indice, nuevaLetra) {
    return cadena.slice(0, indice) + nuevaLetra + cadena.slice(indice + 1);
}
```

## Arreglos
6. Dado el siguiente arreglo en C/C++ y suponiendo DB=200, calcule lo solicitado.
```c++
char X[5][4]
```
Cada char ocupa un byte. Por lo que `5*4=20`
a. espacio reservado para X en bytes: 20 bytes
b. espacio dimensional M0: 5
c. espacio dimensional M1: 4

(Offset Value) $OV(i,j)=i⋅M1+j$ con $x[i][j]$
d. OV: $OV(2,1)=2*4+1=9$

$Direccion(X[2][1])=DB+OV$
e. L-value X\[2,1] = 200+9=209

7. Dado el siguiente arreglo (en un lenguaje genérico) y suponiendo DB=100, calcule lo solicitado.
```
X is array [-1..4,-6..-1,-3..0] of integer;
```
M0 tiene 6 elementos, M1 tiene 6 elementos y M2 tiene 4 elementos
a. espacio reservado para X en bytes:  $M_{0}*M_{1}*M_{2}*bytes_{int}=6*6*4 * 4=144*4=576bytes$
b. espacio dimensional M0:  6
c. espacio dimensional M1:  6
d. espacio dimensional M2: 4

$OV(i,j,k)=(i−L0​)⋅M1​⋅M2​+(j−L1​)⋅M2​+(k−L2​)$
$L_{0}=-1, L_{1}=-6, L_{2}=-3, M_{1}=6, M_{2}=4$
e. OV: $OV(0,-3,-2)=37$

Dirección real=(DB)+Offset en elementos×tamaño de cada elemento en bytes
f. L-value $X[0,-3,-2] = 100+37*4=100+148=248$

## Registros unidos
10. Analice el siguiente programa en C++ y responda lo solicitado.
```c++
#include <iostream> 
#include <cstring> 
struct Tarea { 
    int id; 
    char descripcion[30]; 
    Tarea* siguiente; 
}; 
struct Empleado { 
    int id; 
    char nombre[20]; 
    Tarea primeraTarea;   
}; 
int main() { 
    Empleado empleados[3] = { 
        {1, "Ana", {101, "Revisión", new Tarea{102, "Ajustes", new Tarea{103, "Documentación", nullptr}}}},
       {2, "Maria", {201, "Relevamiento", new Tarea{202, "Análisis", nullptr}}}, 
        {3, "Luis", {0, "", nullptr}}   
    }; 
 
for (int i = 0; i < 3; i++) { 
        std::cout << empleados[i].nombre << " tiene las siguientes tareas:\n"; 
        Tarea* tarea = &empleados[i].primeraTarea; 
        while (tarea && tarea->id != 0) { 
            std::cout << "  - " << tarea->descripcion << "\n"; 
            tarea = tarea->siguiente; 
        } 
 
        if (empleados[i].primeraTarea.id == 0) std::cout << "  (Sin tareas asignadas)\n"; 
    } 
return 0; 
}
```
a. Indique qué muestra en la salida. 
```bash
Ana tiene las siguientes tareas:
  - Revisión
  - Ajustes
  - Documentación
Maria tiene las siguientes tareas:
  - Relevamiento
  - Análisis
Luis tiene las siguientes tareas:
  (Sin tareas asignadas)
```

b. Indique los tipos estructurados que se utilizan en el código.
	Tenemos dos estructuras: Tarea y Empleado

c. Indique cuánto espacio en memoria ocupa un registro del tipo tarea. 
```c++
struct Tarea {
    int id;                      // 4 bytes
    char descripcion[30];       // 30 bytes
    Tarea* siguiente;           // 8 bytes en sistemas de 64 bits (4 si es de 32 bits)
};
```
4 (int) + 30 (char\[30]) + 2 bytes de relleno (padding) + 8 (puntero) = **44 bytes**.

d. Indique cuánto espacio en memoria ocupa un registro del tipo empleado. 
```c++
struct Empleado {
    int id;                     // 4 bytes
    char nombre[20];           // 20 bytes
    Tarea primeraTarea;        // 44 bytes (como se calculó en c)
};
```
4 + 20 + (2 padding) + 44 = **68 bytes**

e. Indique cómo cambiar el código para que el registro Empleado tenga un puntero a la primera tarea de la lista, en lugar de incluir una tarea. Indique cuánto pesaría en memoria el registro en este caso. 
```c++
struct Empleado {
    int id;                     // 4 bytes
    char nombre[20];           // 20 bytes
    Tarea* primeraTarea;       // 8 bytes (puntero en 64 bits)
};
```
4 + 20 + (4 padding) + 8 = **36 bytes**.

f. Escriba el código necesario para agregar una nueva tarea “Diseño” a la lista de tareas de María.  
```c++
Tarea* nuevaTarea = new Tarea{203, "Diseño", nullptr};
Tarea* actual = empleados[1].primeraTarea;  // María es empleados[1]

// Recorremos hasta el final de la lista
while (actual->siguiente != nullptr) {
    actual = actual->siguiente;
}
actual->siguiente = nuevaTarea;

```

g. Escriba la línea de código necesaria para agregar una nueva tarea “Limpiar disco” a Luis. Reescriba el programa del ejercicio anterior en JavaScript.
```c++
empleados[2].primeraTarea = new Tarea{301, "Limpiar disco", nullptr};
```

```js
class Tarea {
    constructor(id, descripcion, siguiente = null) {
        this.id = id;
        this.descripcion = descripcion;
        this.siguiente = siguiente;
    }
}

class Empleado {
    constructor(id, nombre, primeraTarea = null) {
        this.id = id;
        this.nombre = nombre;
        this.primeraTarea = primeraTarea;
    }

    mostrarTareas() {
        console.log(`${this.nombre} tiene las siguientes tareas:`);
        if (!this.primeraTarea) {
            console.log("  (Sin tareas asignadas)");
            return;
        }
        let tarea = this.primeraTarea;
        while (tarea) {
            console.log(`  - ${tarea.descripcion}`);
            tarea = tarea.siguiente;
        }
    }
}

// Inicialización
const empleados = [
    new Empleado(1, "Ana", new Tarea(101, "Revisión", new Tarea(102, "Ajustes", new Tarea(103, "Documentación")))),
    new Empleado(2, "Maria", new Tarea(201, "Relevamiento", new Tarea(202, "Análisis"))),
    new Empleado(3, "Luis")
];

// Agregar tarea “Diseño” a Maria
let t = empleados[1].primeraTarea;
while (t.siguiente) t = t.siguiente;
t.siguiente = new Tarea(203, "Diseño");

// Agregar tarea “Limpiar disco” a Luis
empleados[2].primeraTarea = new Tarea(301, "Limpiar disco");

// Mostrar tareas
for (const emp of empleados) {
    emp.mostrarTareas();
}
```

11. Dadas las siguientes declaraciones de tipo, resuelva lo solicitado.
```c++
union EstadisticasDeporte { 
	byte goles;         
	  // futbol 
	double puntos;     
	  // boxeo 
	int setsGanados;     // tenis 
}; 
struct Jugador { 
	int id; 
	char nombre[30]; 
	char deporte;       
	 // 'F' = Fútbol, 'B' = Boxeo, 'T' = Tenis 
	EstadisticasDeporte estadisticas; // Datos específicos para cada deporte 
	float promedioPuntuacion; 
} deportistas [500];
```

a. Indique el peso en memoria de deportistas. 
```c++
struct Jugador {
    int id;                        // 4 bytes
    char nombre[30];              // 30 bytes
    char deporte;                 // 1 byte
    // 3 bytes padding para alinear double
    union EstadisticasDeporte {   // Máximo tamaño entre: byte (1), double (8), int (4)
        byte goles;               // 1 byte
        double puntos;            // 8 bytes
        int setsGanados;          // 4 bytes
    } estadisticas;               // => ocupa 8 bytes
    float promedioPuntuacion;     // 4 bytes
};
```
`4 (int) + 30 (char) + 1 (char) + 8 (union) + 4 (float) = 47 bytes -> 48 bytes`
48 bytes * 500 elementos = 24,000 bytes

b. Indique el peso en memoria de deportistas\[105].estadisticas.
Su tamaño será el del miembro más grande, que es `double`: 8 bytes

c. Suponiendo que la dirección de deportistas es DB=100, indique la dirección de 
deportistas\[5].estadisticas.setsGanados. 
Dirección base de deportistas\[5]: DB + 5 * 48 = 100 + 240 = 340
Jugador tiene 4+30+1+3(padding)=38 offset
Dirección final=`340 + 38 = 378`

d. Suponiendo que la dirección de deportistas es DB=100, indique la dirección de 
deportistas\[5].estadisticas.goles. 
Dirección final es la misma que la anterior: 378

e. Escriba un programa que cargue datos de 3 deportistas, uno de cada deporte y luego muestre correctamente el nombre de cada deportista, el deporte que realiza, sus estadísticas (con indicación de si son goles, puntos o setsGanados) y su promedio de puntuación. 
```c++
#include <iostream>
#include <cstring>
using namespace std;

typedef unsigned char byte;

union EstadisticasDeporte {
    byte goles;         // fútbol
    double puntos;      // boxeo
    int setsGanados;    // tenis
};

struct Jugador {
    int id;
    char nombre[30];
    char deporte; // 'F', 'B', 'T'
    EstadisticasDeporte estadisticas;
    float promedioPuntuacion;
};

int main() {
    Jugador deportistas[3];

    // Fútbol
    deportistas[0].id = 1;
    strcpy(deportistas[0].nombre, "Lionel Messi");
    deportistas[0].deporte = 'F';
    deportistas[0].estadisticas.goles = 12;
    deportistas[0].promedioPuntuacion = 8.5;

    // Boxeo
    deportistas[1].id = 2;
    strcpy(deportistas[1].nombre, "Canelo Álvarez");
    deportistas[1].deporte = 'B';
    deportistas[1].estadisticas.puntos = 98.7;
    deportistas[1].promedioPuntuacion = 9.1;

    // Tenis
    deportistas[2].id = 3;
    strcpy(deportistas[2].nombre, "Rafael Nadal");
    deportistas[2].deporte = 'T';
    deportistas[2].estadisticas.setsGanados = 3;
    deportistas[2].promedioPuntuacion = 7.9;

    // Mostrar info
    for (int i = 0; i < 3; ++i) {
        cout << "Jugador: " << deportistas[i].nombre << endl;
        cout << "Deporte: ";
        switch (deportistas[i].deporte) {
            case 'F':
                cout << "Fútbol\nEstadística: Goles = " << (int)deportistas[i].estadisticas.goles << endl;
                break;
            case 'B':
                cout << "Boxeo\nEstadística: Puntos = " << deportistas[i].estadisticas.puntos << endl;
                break;
            case 'T':
                cout << "Tenis\nEstadística: Sets Ganados = " << deportistas[i].estadisticas.setsGanados << endl;
                break;
        }
        cout << "Promedio de puntuación: " << deportistas[i].promedioPuntuacion << "\n\n";
    }

    return 0;
}

```