# Listas, Pilas y Colas
Las estructuras de datos es un tipo de dato formado por un conjunto de elementos de un mismo tipo de dato. Pueden ser:
- Estáticas: el tamaño que ocupan se define antes de que se ejecute el programa
- Dinámicas: su tamaño crece y se encoje en tiempo de ejecución
### Estructuras Dinámicas Lineales
Pueden implementarse mediantes punteros o arreglos.
Para poder utilizar arreglos se debe establecer un tamaño suficiente para que contengan todos los elementos posibles.
### Enalces
Existe la necesidad de querer relacionar arreglos y para eso utilizamos enlaces. Pueden ser: 
- Implícitos: dado el número de subíndices.
- Explícitos: en uno de los arreglos debe existir un elemento que indique (valor entero) la posición donde está ubicado el elemento relacionado del otro arreglo.
![[imagenes/Enlaces.png]]
## Pilas
Es una estructura lineal donde la inserción y eliminación de elementos se hacen por un solo extremo que se denomina cima o tope. Modelo LIFO.
Casos aplicación natural, por ej.: pila de platos, pila de cajas, pila de libros.
### LIFO
 Insertamos (apilar) elementos por la cima (final), incrementando en 1
 Eliminamos (desapilar) por la cima (final), restando 1
 Pila llena: Cima = Longitud 
 Pila vacía: Cima = 0

Operaciones:
##### Insertar elementos
```
PROCEDIMIENTO insertarPila(longitud, por ref. cima: ENTERO; por ref. pilaLibros[100], libro: CADENA)
INICIO
	SI cima < longitud ENTONCES
		cima = cima + 1
		pilaLibros[cima] = libro
	SINO
		ESCRIBIR("Pila llena")
	FINSI
FINPROCEDIMIENTO
```
##### Eliminar elementos
```
PROCEDIMIENTO eliminarPila(por ref. cima: ENTERO; por ref. pilaLibros[100], por ref. libro: CADENA)
INICIO
	SI cima = 0 ENTONCES
		ESCRIBIR("Pila vacia")
	SINO
		libro = pilaLibros[cima]
		pilaLibros[cima] = ""
		cima = cima - 1
	FINSI
FINPROCEDIMIENTO
```
## Colas
Es un estructura lineal donde la inserción se realiza por el final de la lista y la eliminación de elementos se hace por el principio. Modelo FIFO.
Casos de aplicación natural, por ej.: cola del supermercado, atención por orden de llegada en el médico, cola de impresión.
### FIFO
 Insertamos (encolar) elementos por el final, incrementado en 1
 Eliminamos (desencolar) por el principio, restando 1
 Cola llena: Final = Longitud
 Cola vacía: Final = 0

Operaciones:
##### Insertar elementos
```
PROCEDIMIENTO insertarCola(por ref. inicio, por ref. final: ENTERO; por ref. colaPacientes[100], nomPaciente: CADENA)
INICIO
	SI final = 0 ENTONCES
		inicio = 1
	FINSI
	SI final < longitud ENTONCES
		final = final + 1
		colaPaciente[final] = nomPaciente
	SINO
		ESCRIBIR("Cola llena")
	FINSI
FINPROCEDIMIENTO
```
##### Eliminar elementos
```
PROCEDIMIENTO eliminarCola(inicio, por ref. final: ENTERO; por ref. colaPacientes[100]: CADENA, por ref. nomPaciente: CADENA)
INICIO
	SI final = 0 ENTONCES
		ESCRIBIR("Cola vacia")
	SINO
		nomPaciente = colaPacientes[inicio]
		VARIAR i DESDE inicio HASTA final - 1
			colaPacientes[i] = colaPacientes[i + 1] // corro elementos
		FINVARIAR
		colaPacientes[final] = ""
		final = final - 1
	FINSI
FINPROCEDIMIENTO
```
## Listas
Estructura lineal cuyos elementos están en un determinado orden. Los elementos se almacenan en la memoria en **posiciones consecutivas**, por eso se llaman listas contiguas.
Para insertar o eliminar un elemento, salvo en el principio o en el final que son directas, se necesita una *traslación* de elementos. Casos aplicación natural, ej: lista de alumnos, lista de comercios adheridos.
##### Insertar elementos
Inserta al final en este ejemplo
```
PROCEDIMIENTO insertarVentas(por ref. longitud: ENTERO; por ref. ventas[30], ventaDia: REAL)
INICIO
	SI longitud = tope ENTONCES
		ESCRIBIR("Lista completa")
	SINO
		longitud = longitud + 1
		ventas[longitud] = ventaDia
	FINSI
FINPROCEDIMIENTO
```
##### Eliminar elementos
```
PROCEDIMIENTO borrarVentas(por ref. longitud: ENTERO, por ref. ventas[30]: REAL, elemento: ENTERO)
VAR i: ENTERO
INICIO
	SI longitud = 0 ENTONCES
		ESCRIBIR("Lista vacia")
	SINO
		SI elemento >= 1 [Y] elemento < longitud ENTONCES
			VARIAR i DESDE elemento HASTA longitud - 1
				ventas[i] = ventas[i + 1]
			FIN VARIAR
		FINSI
	FINSI
	SI elemento >= 1 [Y] elemento <= longitud ENTONCES
		ventas[longitud] = 0.0
		longitud = longitud - 1
	SINO
		ESCRIBIR ("Error, elemento inexistente")
	FINSI
FINPROCEDIMIENTO
```
## Listas Enlazadas
Se pueden almacenar los elementos en posiciones de memoria **no consecutivas**. Cada elemento contiene la posición o dirección del siguiente elemento de la lista.
Caso de aplicación natural, ej: en un zoológico el orden de las jaulas para dar la comida.
![[imagenes/Listas Enlazadas.png|200]]
Para trabajar con datos tipo cadena se necesita usar 2 arreglos, uno tipo cadena con los datos y otro tipo entero con la posición “siguiente”. En este caso relacionamos ambos arreglos con *enlace implícito*.
##### Insertar elementos
```
PROCEDMIENTO insertarElem(por ref. longitud, por ref. inicio, por ref. vacio, por ref. listaE[100, 2], jaula: ENTERO)
VAR i: ENTERO
INICIO
	SI vacio <> 0 ENTONCES // Si vacio = 0 lista llena
		listaE[vacio, 1] = jaula
		listaE[vacio, 2] = 0 // posicion siguiente 0
		asignoSig(listaE[], inicio, vacio) // Busco ultimo elemento de lista
		vacio = buscoVac(longitud, listaE[]) // Busco primer lugar vacio
	SINO
		ESCRIBIR("Lista llena")
	FINSI
FINPROCEDIMIENTO
```
###### Procedimiento asignoSig
```
PROCEDIMIENTO asignoSig(por ref. listaE[100, 2], inicio, vacio: ENTERO)
VAR i: ENTERO
INCIO
	i = inicio
	MIENTRAS listaE[i, 2] <> 0 HACER
		i = listaE[i, 2]
	FINMIENTRAS
	listaE[i, 2] = vacio // al ultimo le asigno como 'sig' el nuevo elem insertado
FINPROCEDIMIENTO
```
###### Procedimiento buscoVac
```
FUNCION buscoVac(longitud, listaE[100, 2]: ENTERO): ENTERO
VAR i, j: ENTERO
	bandera: LOGICO
INICIO
	bandera = [F]
	i = 0
	REPETIR
		REPETIR
			i = i + 1
		HASTA i > longitud [O] listaE[i, 1] = 0 [Y] listaE[i, 2] = 0
			SI i > longitud ENTONCES // si no hay elementos en 0
				vacio = 0 // lista llena
				bandera = [V]
			SINO 
			// verifico que la fila encontrada no es el ultimo elemento de la lista y contiene 0
				j = 0
				REPETIR
					j = j + 1
				HASTA j > longitud [O] listaE[j, 2] = i
					SI j > longitud ENTONCES
						vacio = i
						bandera = [V]
					SINO
						//es el ultimo elemento de la lista, sigo buscando
						bandera = [F]
					FINSI
			FINSI
	HASTA bandera
	buscoVac = vacio
RETORNO
```
##### Eliminar elementos
```
PROCEDIMIENTO eliminarElem(por ref. iniciar, por ref. listaE[100, 2], valor: ENTERO)
VAR i, anterior: ENTERO
INICIO
	i = iniciar
	anterior = iniciar
	MIENTRAS listaE[i, 1] <> valor [Y] listaE[i, 2] <> 0 HACER
		anterior = i
		i = listaE[i, 2]
	FINMIENTRAS
	SI listaE[i, 1] <> valor ENTONCES
		ESCRIBIR("No se encontro el elemento a eliminar")
	SINO
		SI i = iniciar ENTONCES
			iniciar = listaE[i, 2]
		SINO
			listaE[anterior, 2] = listaE[i, 2]
		FINSI
		listaE[i, 1] = 0 // borro elemento dado
		listaE[i, 2] = 0 // borro siguiente
	FINSI
FINPROCEDIMIENTO
```

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Libro {
	char titulo[50];
	char autor[50];
	char isbn[13];
} Libro;

typedef struct Nodo {
	Libro libro;
	struct Nodo* siguiente;
} Nodo;

typedef struct Lista {
	Nodo* cabeza;
} Lista;

Nodo* CrearNodo(Libro* libro) {
	Nodo* nodo = (Nodo *) malloc(sizeof(Nodo));
}
[Estructuras de datos – 3. Listas enlazadas en C (COMPLETO) - YouTube](https://www.youtube.com/watch?v=vldM-3PYAmo)
```
## Lista Doblemente Enlazadas
Se pueden almacenar los elementos en posiciones de memoria no consecutivas
Cada elemento contiene *dos punteros*, uno apuntando al siguiente elemento de la lista, es decir del sucesor, y otro al predecesor.
Estas listas permiten avanzar o retroceder a través de la misma.
![[imagenes/Listas Doblemente Enlazadas.png]]
#### Operaciones
- Inserción de un elemento: al final, al principio o en medio.
- Borrado de un elemento: el primero, el último o en medio.
## Cuadro Comparativo

|                                                           |           Pilas                         |           Colas                          |          Listas                         |         Listas Enlazadas                            |
|:----------------------------------------------------------|:----------------------------------------|:-----------------------------------------|:----------------------------------------|:----------------------------------------------------|
|  Inserción                                                |        Final(cima)                      |           Final                          |      Cualquier lado                     |          Cualquier lado                             |
|  Eliminación                                              |        Final(cima)                      |         Principio                        |      Cualquier lado                     |          Cualquier lado                             |
|  Recorrido p/datos&nbsp;<div>Rec. p/incializar     </div> |  1 a cima&nbsp;<div>1 a longitud </div> |  1 a final&nbsp;<div>1 a longitud </div> |  1 a longitud&nbsp;<div>1 a tope </div> |  Mientras i &lt;&gt; 0&nbsp;<div>1 a longitud</div> |
|  Esta llena cuando                                        |      Longitud = Cima                    |      Longitud = Final                    |      Tope = Longitud                    |            Vacio = 0                                |
|  Esta vacía cuando                                        |         Cima = 0                        |         Final = 0                        |       Longitud = 0                      |            Inicio = 0                               |
|  Uso de punteros                                          |            No                           |             No                           |            No                           |                Si                                   |
|  Luego de una operación se corren los elementos           |            No                           |             Si                           |            Si                           |                No                                   |  
# Estructuras de Datos NO Lineales
## No Lineales
Las estructuras dinámicas lineales de datos tienen grandes ventajas, sin embargo tienen un punto débil, son listas secuenciales, están dispuestas de modo que es necesario moverse a través de ellas una posición a la vez.
Las estructuras de datos no lineales tienen la característica que cada elemento puede tener diferentes siguientes elementos.
### Árbol
Es una estructura de datos muy utilizada porque se adapta a la representación natural de informaciones homogéneas organizadas y de una gran comodidad y rapidez de manipulación.
Se usan para representar datos con una *relación jerárquica* entre sus elementos, como son árboles genealógicos, organigramas, llamadas a subprogramas, entre otros.
#### Características
- Cada elemento del árbol se denomina **nodo**.
- Existe un nodo especial: nodo raíz.
- Los nodos sin ramificaciones se llaman terminal u hoja.
- Cada nodo apunta a uno o más nodos.
- A un nodo le apunta sólo un nodo.
- El *grado* es el número de descendientes DIRECTOS de un nodo.
![[imagenes/Arbol.png|200]]
#### Árboles Binarios
Los árboles de *grado 2* representan una estructura importante. En los árboles binarios todos sus nodos excepto los del último nivel, tienen dos hijos: el subárbol izquierdo y el subárbol derecho.
![[imagenes/Arboles binarios.png|200]]

### Grafos
Si en los árboles eliminamos la restricción de que un nodo sólo puede ser apuntado por un solo nodo obtenemos un grafo.
Un grafo tiene una gran número de aplicaciones, por ej.: red de caminos, red de enlaces aéreos, entre otros.
![[imagenes/Grafo.png|200]]
#### Ciclo
Un ciclo es una trayectoria, secuencia de una o más aristas que conectan a 2 nodos, que se dan las siguientes condiciones:
- Ninguna arista puede aparecer más de una vez en una secuencia.
- El nodo inicial de la trayectoria es el mismo que el nodo final.
![[imagenes/Ciclo.png|200]]
