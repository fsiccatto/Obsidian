# Estructuras de Control de Flujo
## Técnicas de Porgramación
El diseño de un programa establece la descomposición del problema en módulos y su posterior unión con procedimientos ascendentes o descendentes. ==Programación modular y programación estructurada==.
#### Caracterísiticas
Un #programa cumple las siguientes caracterísiticas: 
- Posee un solo punto de entrada y uno de salida para control del programa.
- Existen caminos desde la entrada hasta la salida que se pueden seguir y pasan por todas las partes del programa.
- Todas las instrucciones son ejecutables y no existen lazos o bucles infinitos.
### Programación Modular
El programa se divide en módulos, cada uno de los cuales ejecuta una **ÚNICA** (divide y vencerás) tarea y se codifican **INDEPENDIENTES** (ninguno tiene acceso a otro) de otros módulos.
Existe un programa principal que controla todo lo que sucede.
En el caso de las funciones de entrada, proceso y salida, es conveniente que cada una esté en un módulo separado.
### Programación Estructurada
Hace que los programas sean más fáciles de escribir, verificar, leer y mantener.
Conjunto de técnicas que aumentan considerablemente la productividad del programa:
- ##### Recursos  abstractos
	Se auxilia en recursos abstractos en lugar de recursos concretos. Consiste en descomponer una determinada acción compleja en función de un número de acciones más simples, capaces de ser ejecutadas y que constituirán las instrucciones.
- ##### Diseños descendentes (top-down).
	El problema se descompone en una serie de pasos sucesivos de refinamiento, obteniendo estructras jerárquicas.
	- Nivel n: Vista exterior: ¿Qué hace?
	- Nivel n+1: Vista interior: ¿Cómo lo hace?
- ##### Estructuras básicas
	Un programa puede ser escrito en tres tipos de estructuras de control:
	- Estructuras Secuenciales
	- Estructuras Selectivas
	- Estructuras Repetitivas
#### **Estructuras Secuenciales**
Es una estructura que permite controlar la ejecución de un conjunto de acciones, en orden *secuencial*.
Estas acciones peden ser operaciones primitivas elementales como: declaraciones de variables, leer datos, escribir o mostrar datos, calcular alguna expresión.
![[Secuencializacion|200x200|center]]
#### **Estructuras Selectivas**
Es una estructura que permite controlar la ejecución de acciones que requieren de condiciones (dependiendo el camino que tengamos que seguir) para su realización.
##### Tipos de Estructuras Selectivas
- ###### Simples
	Ejecuta una determinada acción cuando se cumple una condición. Si la condición es verdadera se ejecuta la acción, si es falsa no se ejecuta ninguna acción.
	```
	SI condicion ENTONCES
		Acciones
	FINSI
	```
- ###### Dobles
	Permite elegir entre dos opciones en función del cumplimiento de una determinada condición. Se ejecuta una u otra, pero nunca las dos a la vez.
	```
	SI condicion ENTONCES
		Acciones 1
	SINO
		Acciones 2
	FINSI
	```
- ###### Múltiples
	Es cuando existen más de dos alternativas posibles. Se evalúa una expresión que podrá tomar `n` valores distintos, según el resultado podrá segir una de las `n` acciones posibles
	```
	SEGUN CASO selector HACER
		v1: accion 1
		v2: accion 2
		...
	DE OTRO MODO
		accion n
	FINSEGUN
	```
	También se puede hacer una selección anidada de `SI ENTONCES FINSI`.
#### **Estructuras Repetitivas: Ciclos o Bucles**
Estructuras qe repiten una secuencia de instrucciones un número determinado de veces, iteración se llama al hecho de repetir la ejecución de una secuencia de acciones.
##### Tipos de estructuras repetitivas
- ###### Repetir (Ciclo 1 - X)
	Ejecuta las acciones tantas veces como sea necesario hasta que se cumpla la condición. Se ejecuta por lo menos 1 vez  (`do-while`).
	```
	REPETIR
		Acciones 1
	HASTA QUE condicion
	```
- ###### Mientras (Ciclo 0... X)
	Se analiza la condición, si se cumple (V) se ejecutan las acciones, sino (F) sale del bucle (`while`).
	```
	MIENTRAS condicion HACER
		Acciones 1
	FIN MIENTRAS
	```
- ###### Variar (Ciclo Exacto)
	Se ejecuta determinadas veces, desde 1 hasta vf con el paso que querramos (`for`).
	```
	VARIAR var1 DESDE vi HASTA vf PASO inc
		Acciones 1
	FINVARIAR
	```
- ###### Iterar 
	Es una combinación de repetir y mientras. Se ejecutan las acciones 1 y luego se evalúa la condición, si es F ejecuta las acciones 2. Luego va a ejecutar las acciones 1 y vuelve a evaluar la condición y así sucesivamente.
	La salida del bucle es con la condición V.
	```
	ITERAR
		Acciones 1
	SALIR SI condicion
		Acciones 2
	FINITERAR
	```

<ins>Cuadro Comparativo</ins>

| | Repetir | Mientras | Iterar | Variar|
|:---:|:-------:|:----------:|:-------:|:---------:|
|Ciclo| 1 - x | 0 - x| Acciones 1: 1-x, Acciones2: 0-x | exacto|
|Cond final| Verdadera| Falsa | Verdadera | No tiene |
|Pos de la cond| Final| Principio| Medio| No tiene|

## Puesta a Punto de Programas
Consiste en **localizar, verificar y corregir** los errores de programación. El objetivo es prevenir tantos errores como sea posible a la hora de ejecutar un programa. Una prueba o ensayo es satisfactoria cuando se detectan errores. Consiste en las siguientes fases:
1. Detección de errores
2. Depuración de errores
	1. Localización
	2. Eliminación
3. Prueba del Programa
#### Errores Típicos
- *De sintaxis*: se originan en la fase de compilación del programa y se deben a causas propias de la sintaxis del lenguaje como escrituras incorrectas, omisiones de signo, etc.
- *De lógica*: pueden detener la ejecución o producir resultados erróneos.
#### Pruebas de Programas
Realizar pruebas con conjuntos de datos de muestra, cuya solución sea conocida y correcta.
1. Determinar los caminos del programa que deben ser controlados en cada estructura.
2. Se definen los recorridos del programa.
3. Se deducen a partir del paso 1 los datos que deben introducirse en la entrada.
4. Se deducen los datos que deben obtenerse a la salida del programa.