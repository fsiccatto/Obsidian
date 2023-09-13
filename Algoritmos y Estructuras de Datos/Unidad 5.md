# Arreglos
[[U5_Arreglos 1.pdf]]
Hasta ahora hemos visto datos simples o pirmitivos en la [[remote-repo/Algoritmos y Estructuras de Datos/Unidad 2]], que solo pueden almacenar un valor a la vez.
## ¿Qué es una #EstructuraDeDatos?
Es un tipo de dato formado por un conjunto de elementos de un mismo tipo de datos. Un #dato de tipo estructurado puede almacenar a más de un elemento a la vez, con la condición de que deben ser del **mismo tipo de dato**.
⚠️ Cada variable representa múltiples datos individuales, y a su vez cada uno de estos elementos se pueden referenciar de manera independiente.
Las estructuras pueden ser:
➡️ **Estáticas**: el tamaño que ocupan se define antes que se ejecte el programa. Por ej: Arreglos
➡️ **Dinámicas**: no tiene la definición del tamaño ocupado. Por ej: Listas.
### Arreglos
Conjunto finito y ordenado de elemtnos homogéneos
- Finito: es un número determinado de elementos
- Ordenado: siguen una secuencia y pueden identificarse
- Homogéneo: todos los elementos son del mismo tipo de dato
Se clasifican dependiendo del número de dimensiones:
#### Arreglos Unidimensionales: #Vectores
Es una variable estructurada de **UNA** dimensión, con elementos del mismo tipo de dato y bajo un nombre, cada elemento tiene una posición dentro del arreglo. `VAR nombre[tamaño]: tipo de dato`
```
Vector: A
tamaño: n
A[1], A[2], A[3], ..., A[n];

VAR nomVector[TAMAÑO]: TIPO DE DATO
```
#Indice Para poder referirnos al vector completo o a un elemtento, debemos hacer `nombre[subindice]`. Tiene que ser de tipo **ENTERO** y va de `1 <= subindice <= tamaño`.
##### Operaciones con Vectores
- Asignación
	Asiganr el valor x al i-ésimo elemento del vector `nombre[i] = x`.
	También podemos asignar valores a todo el vector:
	```
	VARIAR i DESDE 1 HASTA t
		nombre[i] = n
	FINVARIAR
	```
- Lectura/Escritura
	Podemos leer `LEER(nombre[i])` o escribir `ESCRIBIR(nombre[i])`.
- Recorrido
	Es acceder a todos los elementos de un arreglo, en forma ordenada para leer, escribir o asignar. Se utilizan estructuras repetitivas.
- Ordenamiento
- Búsqueda
#### Arreglos Bidimensionales: #Matrices
Es una variable estructurada de **DOS** dimensiones, con elementos del mismo tipo de dato y bajo un nombre y se distribuye en filas y columnas. `VAR nombre[tFila, tColumna]: tipo de dato`
```
Matriz: A
tamaño: n * m
A[1, 1], A[1, 2], A[1, 3], ..., A[1, m]
A[2, 1], A[2, 2], A[2, 3], ..., A[2, m]
A[3, 1], A[3, 2], A[3, 3], ..., A[3, m]
...
A[n, 1], A[n, 2], A[n, 3], ..., A[n, m]

VAR nomMatriz[TAMAÑOFILA][TAMAÑOCOLUMNA]: TIPO DE DATO
```
#Indice Podemos referirnos a la matriz completa o a un único elemento. Debemos hacerlo `nombre[subidndiceFila, subindiceColumna]`.
Cada subíndice va desde 1 hasta el tamaño de la fila o la columna y tiene que se **ENTERO**.
##### Operaciones con Matrices
- Asignación
- Lectura
- Escritura
- Recorrido
	Se deben utilizar dos bucles repetitivos anidados, el primero para filas y el segundo para columnas.
	```
	VARIAR i DESDE 1 HASTA n
		VARIAR j DESDE 1 HASTA m
			LEER(matriz[i, j])
		FINVARIAR
	FINVARIAR
	```
#### Arreglos Tridimensionales:
Es una variable estructurada de **TRES** dimensiones que agrupa varias celdas de memoria distribuidas en filas, columnas y planos. `VAR nombre[tFila, tColumna, tPlano]: tipo de dato´.

![[Arreglos Tridimensionales.png]]
#Indice Podemos referirnos al arreglo completo o a un único elemento. Debemos hacerlo como `nombre[subidndiceFila, subindiceColumna, subindicePlano]`.
Cada subíndice va desde 1 hasta el tamaño de la fila o la columna y tiene que se **ENTERO**.
##### Operaciones con Arreglos Tridimensionales
- Asignación
- Lectura
- Escritura
- Recorrido
	Se deben utilizar tres bucles repetitivos anidados, el primero para filas y el segundo para columnas.
	```
	VARIAR i DESDE 1 HASTA n
		VARIAR j DESDE 1 HASTA m
			VARIAR k DESDE 1 hasta p
				LEER(matriz[i, j, p])
			FINVARIAR
		FINVARIAR
	FINVARIAR
	```

### Sección Transversal
Una sección tranveresal de un arreglo bidimensional #Matrices  se obtine al mantener uno de sus subíndices constantes mientras se hace variar a otro.
Para denotar la sección transversal se usa `*` para el subídince que puede tomar cualquier valor del rango definido. Ej: `B[*, 4]` hacemos variar todas las filas para la columna 4.
### Traspuesta
La traspuesta de las #Matrices es el cambio de las filas por columnas y las columnas por filas.
Por definición `B[i, j] = BT[j, i]`.
## Búsqueda y Ordenamiento
La *búsqueda* es la localización de un elemento y el *ordenamiento* es el secuenciamiento de elementos teniendo en cuenta un determinado criterio. Siempre es más fácil encontrar un elemento dentro de un conjunto si éste se encuentra ordenado.
### Búsqueda Lineal
Es el método más simple, se debe leer consecutivamente un elemento tras otro hasta que coincida el valor buscado con el valor examinado. La búsqueda termina exitosa cuando se ha encontrado el elemento buscado, termina sin éxito cuando llega el final del arreglo y no se encontró el elemento.
###### Ejemplo
```
PROGRAMA BusqLineal
VAR numeros[100], i, buscado: ENTERO
INICIO
	ESCRIBIR("Ingrese el numero a buscar")
	LEER(buscado)
	i = 1
	// Lo hago con un MIENTRAS para no tener que recorrer todo el array
	MIENTRAS i <= 100 [Y] numeros[i] <> buscado HACER
		i = i + 1
	FINMIENTRAS
	SI i <= 100 [Y] numeros[i] = buscado ENTONCES
		ESCRIBIR("El", buscado, "está en el arreglo en posición", i)
	SINO
		ESCRIBIR("EL", buscado, "no esta en el arreglo")
	FINSI
FINPROGRAMA
```
### Búsqueda Binaria
Cuando la cantidad de elementos que queremos buscar es grande utilizamos la *búsqueda binaria*.  Es necesario que los elementos estén **ordenados** #ordenamiento en el arreglo para hacer la búsqueda binaria.
La búsqueda procede mediante una serie de pruebas sucesivas en el arreglo:
 - La primera prueba compara el valor del elemento que está a la mitad del conjunto contra el valor buscado, si el valor buscado es menor, entonces la segunda mitad del conjunto puede ignorarse. Si el valor es mayor se considerará la segunda mitad y se descartará la primera.
 - La segunda prueba compara el valor de la mitad del conjunto que queda, si el valor buscado es menor se parte el conjunto y se descarta la segunda mitad, si es mayor se descarta la primera mitad.
De esta forma se continúa partiendo el conjunto buscando el valor hasta encontrarlo o hasta probar que no existe.

###### Ejemplo
```
FUNCION BusqBin(tamaño, vector[100], valor: ENTERO): LOGICO
VAR band: LOGICO
	inf, sup, mitad: ENTERO
INCIO
inf = 1
sup = tamaño
SI (valor < vector[1]) [O] (valor > vector[tamaño]) ENTONCES
	busqBin = [F]
SINO
	ITERAR
		mitad = (inf + sup) / 2
	SALIR (SI inf >= sup) [O] (vector[mitad] = valor)
		SI vector[mitad] < valor ENTONCES
			sup = mitad - 1 // El valor buscado esta en la primer mitad del conjunto
		SINO
			inf = mitad + 1 // El valor buscado esta en la segunda mitad del conjunto
		FINSI
	FINITERAR
	SI vector[mitad] = valor ENTONCES
		band = [V]
	SINO
		band = [F]
	FINSI
	busqBin = band
FINSI
RETORNO
```

### Ordenamiento por Selección o Burbuja
Consiste en compara elementos sucesivos e intercambiar los elementos fuera de secuencia. El método termina cuando no hay intercambios que hacer durante una iteración.
###### Ejemplo
```
PROCEDIMIENTO burbuja(cant, por ref. vector[100]: ENTERO)
VAR i, j, aux: ENTERO
	señal: LOGICO
INICIO
	señal = [V]
	MIENTAS señal HACER
		señal = [F]
		VARIA j DESDE 1 HASTA cant - 1
			SI vector[j] > vector[j + 1] ENTOCES
				señal = [V]
				aux = vector[j]
				vector[j] = vector[j + 1]
				vector[j + 1] = aux
			FINSI
		FINVARIAR
	FIN MIENTRAS
FIN PROCEDIMIENTO
```
### Ordenamiento por Partición e Intercambio (quicksort)
La idea básica es usar los resultados de cada paso de comparación para guiar el siguiente paso de comparación.
Durante un paso los elementos se intercambian de tal forma que cuando se completa el paso, el conjunto se ha particionado de tal manera que los elementos de una partición son todos menores que un determinado valor y los elementos de la otra partición son todos mayores (aunque desordenados).
"Divide y vencerás" permite ordenar `n` elementos en un tiempo proporcional a O(n log(n)) y en el peor de los casos O(n<sup>2</sup>) .
![[quickSort.webp]]
``` JavaScript
function swap(items, leftIndex, rightIndex){
    let temp = items[leftIndex];
    items[leftIndex] = items[rightIndex];
    items[rightIndex] = temp;
}

function partition(items, left, right) {
    let pivot = items[Math.floor((right + left) / 2)], //middle element
        i = left, //left pointer
        j = right; //right pointer
    while (i <= j) {
        while (items[i] < pivot) {
            i++;
        }
        while (items[j] > pivot) {
            j--;
        }
        if (i <= j) {
            swap(items, i, j); //swap two elements
            i++;
            j--;
        }
    }
    return i;
}

function quickSort(items, left, right) {
    let index;
    if (items.length > 1) {
        index = partition(items, left, right); //index returned from partition
        if (left < index - 1) { //more elements on the left side of the pivot
            quickSort(items, left, index - 1);
        }
        if (index < right) { //more elements on the right side of the pivot
            quickSort(items, index, right);
        }
    }
    return items;
}
// first call to quick sort
let result = quickSort(items, 0, items.length - 1);
```

## Complejidad Computacional
La complejidad computacional estudia los recursos requeridos durante el cálculo para resolver un problema. Los recursos estudiados son:
- Tiempo: número de pasos de ejecución de un algoritmo
- Espacio: cantidad de memoria utilizada
### Clasificiación de los problemas
Dos grandes clasificaciones: 
- Los problemas con solución → requieren grandes cantidades de recursos
- Los problemas sin solución
### Orden de complejidad
El algoritmo más eficiente es:
- el más rápido
- el que menos memoria ocupa
- la eficiencia se expresa como función del tamaño del problema
### Costo computacional
Se habla de dos tipos de casos:
- El **peor** caso, que es el más difícil de calcular, calculando su función de crecimiento dándole la peor de todas las entradas posibles
- El caso **promedio** es el promedio de cuánto tardaría nuestro algoritmo de cada una de las entradas posibles.
Se siguen tres pasos:
1. Suponer el peor de los casos
2. Asignar un costo a cada operación o línea de código
3. Ver cuantas veces va a ser ejecutada cada línea de código
---
# Ejercicios
![[Arreglos]]