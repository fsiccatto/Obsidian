# Ejercicio 1
Desarrollar un subprograma que recibe tres valores no nulos, devuelva el menor de ellos. En caso de que sean iguales, que retorne cero.
```
PROGRAMA MostrarMenor
VAR arr[3], minVal, i, num: ENTERO
INICIO
	ESCRIBIR("Ingrese tres valores enteros no nulos")
	VARIAR i DESDE 1 HASTA 3
		REPETIR
			ESCRIBIR("Ingrese el valor ", i, ": ")
			LEER(num)
		HASTA QUE (num < 0)
		arr[i] = num
	FIN VARIAR
	minVal = valorMinimo(arr)
	ESCRIBIR("El valor minimo es: ", minVal)
FIN PROGRAMA

FUNCION valorMinimo(arr[3]: ENTERO): ENTERO
	VAR minVal, i: ENTERO
	minVal = arr[1]
	INICIO
	VARIAR i DESDE 2 HASTA 3
		SI (minVal > arr[i]) ENTONCES 
			minVal = arr[i]
		SINO
			SI minVal = arr[i] ENTONCES
			minVal = 0
		FIN SI
	FIN VARIAR
	SI (arr[0] = arr[1]) [Y] (arr[1] = arr[2]) ENTONCES
		minValor  = 0;
	FIN SI
	valorMinimo = minVal
RETORNO
```

|Datos ingresados| Resultado esperado | Resultado obtenido |
|:----:|:-----:|:-----:|
|3, 3, 3| El valor minimo es 0| El valor minimo es 0 |
|-1, 2, 5|Ingrese el valor 1: | Ingrese el valor 1 |
|1, -2, 6| Ingrese el valor 2: | Ingrese el valor 2: |
|5, 1, 3| El valor minimo es 1 | El valor minimo es 1 |
|9, 7, 7| El valor minimo es 7 | El valor minimo es 7 |

## Ejercicio 2
Diseñe un subprograma que determine el porcentaje de varones y de mujeres que hay en un salón
```
PROGRAMA PorcentajeVaronesYMujeres
VAR varones, mujeres, varMuj[2], porcenVarMuj[2]: ENTERO
INICIO
	REPETIR
		ESCRIBIR("Ingrese la cantidad de varones: ")
		LEER(varones)
	MIENTRAS varones < 0
	varMuj[1] = varones
	REPETIR
		ESCRIBIR("Ingrese la cantidad de mujeres: ")
		LEER(mujeres)
	MIENTRAS mujeres < 0
	varMuj[2] = mujeres
	porcenVarMuj = porcentajeVaronesMujeres(varMuj)
	
	ESCRIBIR("El porcentaje de varones es: ", porcenVarMuj[1], "%")
	ESCRIBIR("El porcentaje de mujeres es: ", porcenVarMuj[2], "%" )
FIN PROGRAMA

FUNCION porcentajeVaronesMujeres(varMuj[2]: ENTERO): ENTERO
	VAR suma, porcenVarMuj[2], varones, mujeres: ENTERO
	INICIO
		suma = 0
		varones = varMuj[1]
		mujeres = varMuj[2]
		suma = varones + mujeres
		porcenVarMuj[1] = varones / suma * 100
		porcenVarMuj[2] = mujeres / suma * 100
		porcentajeVaronesMujeres = porcentVarMuj
RETORNO
```

|Datos ingresados| Resultado esperado | Resultado obtenido |
|:----:|:-----:|:-----:|
|35, 50| El porcentaje de varones es: 41% y El porcentaje de mujeres es: 59%|El porcentaje de varones es: 41% y El porcentaje de mujeres es: 59%|
|25, 25 |El porcentaje de varones es: 50% y El porcentaje de mujeres es: 50%| El porcentaje de varones es: 50% y El porcentaje de mujeres es: 50%|
|-32, 25| Ingrese la cantidad de varones: | Ingrese la cantidad de varones: |
|2, -52| Ingrese la cantidad de mujeres: | Ingrese la cantidad de mujeres: |
|7, 0| Ingrese la cantidad de mujeres: | Ingrese la cantidad de mujeres: |
