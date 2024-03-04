#### Ejercicio 1
Hacer un algoritmo que llene una matriz 10 * 10 y determine la posicion \[fila, columna] del numero mayor almacenado en la matriz. Los numeros son diferentes.
```
PROGRAMA MaxMatriz
VAR i, j, matriz[10, 10], posI, posJ, maxNum: ENTEROS
INICIO
	ESCRIBIR("Ingrese 100 valores diferentes")
	VARIAR i DESDE 1 HASTA 10 // Leemos los valores de la matriz
		VARIAR j DEDES 1 HASTA 10
			LEER(matriz[i, j])
		FIN VARIAR
	FINVARIAR
	maxNum = matriz[1, 1]
	posI = 0
	posJ = 0
	VARIAR i DESDE 1 HASTA 10
		VARIAR j DEDES 1 HASTA 10
			SI matriz[i, j] > maxNum ENTONCES
				maxNum = matriz[i, j]
				posI = i
				posJ = j 
			FIN SI
		FIN VARIAR
	FINVARIAR 
	ESCRIBIR("El mayor numero de la matriz es: ", maxNum, " en las posicion [", i, ", ", j, "]")
FIN PROGRAMA
```
#### Ejercicio 2
Hacer un algoritmo que llene una matriz de 10 * 10 y que almacene en la diagonal principal unos y en las demas posiciones ceros.
```
PROGRAMA MatrizDiagonal
VAR i, j, matriz[10, 10]: ENTEROS
INICIO
	VARIAR i DESDE 1 HASTA 10
		VARIAR j DEDES 1 HASTA 10
			SI (i = j)ENTONCES
				matriz[i, j] = 1
			SINO
				matriz[i, j] = 0
			FIN SI
			ESCRIBIR(matriz[i, j] + ",");
		FIN VARIAR
		ESCRIBIR(\n) // Fin de linea
	FIN VARIAR
FIN POGRAMA
```

