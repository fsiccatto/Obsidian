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
using namespace std; 
	int main() { 
	int x = 42; 
	double pi = 3.14; 
	long y = 9007199254740991; 
	cout << "Tipo de x: " << typeid(x).name() << endl; 
	cout << "Tipo de pi: " << typeid(pi).name() << endl; 
	cout << "Tipo de y: " <<  typeid(y).name() << endl; 
	return 0;
}
```

a. ¿JavaScript es un lenguaje de tipado dinámico? 
b. ¿C/C++ son lenguajes de tipado estático?  
c. En el código JavaScript, ¿Son x y pi de tipos equivalentes?  
d. En el código de C++,  ¿Son x y pi de tipos equivalentes?  
e. En el código JavaScript, ¿Es x de un subtipo del tipo de y?  
f. En el código de C++,  ¿Es x de un subtipo del tipo de y? 
g. En el código de C++,  ¿Es x de un tipo subrango del tipo de y?  
h. Agregue una línea al código en C++ para definir un alias de tipo, llamado Temperatura, del 
tipo short. Luego declare una variable tipada con este alias. ¿De qué tipo primitivo es la variable? 
i. ¿Es posible en C/C++ y/o en JavaScript definir subrangos de sus tipos primitivos?

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
```

## Arreglos
6. Dado el siguiente arreglo en C/C++ y suponiendo DB=200, calcule lo solicitado.
```c++
char X[5][4]
```
a. espacio reservado para X en bytes: 
b. espacio dimensional M0: 
c. espacio dimensional M1:  
d. OV:  
e. L-value X\[2,1] =  

7. Dado el siguiente arreglo (en un lenguaje genérico) y suponiendo DB=100, calcule lo solicitado.
```
X is array [-1..4,-6..-1,-3..0] of integer;
```
a. espacio reservado para X en bytes:  
b. espacio dimensional M0:  
c. espacio dimensional M1:  
d. espacio dimensional M2: 
e. OV: 
f. 
L-value X\[0,-3,-2] = 

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
        {1, "Ana", {101, "Revisión", new Tarea{102, "Ajustes", new Tarea{103, "Documentación", 
nullptr}}}},                                                                        
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
b. Indique los tipos estructurados que se utilizan en el código. 
c. Indique cuánto espacio en memoria ocupa un registro del tipo tarea. 
d. Indique cuánto espacio en memoria ocupa un registro del tipo empleado. 
e. Indique cómo cambiar el código para que el registro Empleado tenga un puntero a la 
primera tarea de la lista, en lugar de incluir una tarea. Indique cuánto pesaría en 
memoria el registro en este caso. 
f. Escriba el código necesario para agregar una nueva tarea “Diseño” a la lista de tareas de 
María.  
g. Escriba la línea de código necesaria para agregar una nueva tarea “Limpiar disco” a Luis. Reescriba el programa del ejercicio anterior en JavaScript.
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
b. Indique el peso en memoria de deportistas\[105].estadisticas. 
c. Suponiendo que la dirección de deportistas es DB=100, indique la dirección de 
deportistas\[5].estadisticas.setsGanados. 
d. Suponiendo que la dirección de deportistas es DB=100, indique la dirección de 
deportistas\[5].estadisticas.goles. 
e. Escriba un programa que cargue datos de 3 deportistas, uno de cada deporte y luego muestre correctamente el nombre de cada deportista, el deporte que realiza, sus estadísticas (con indicación de si son goles, puntos o setsGanados) y su promedio de puntuación.  