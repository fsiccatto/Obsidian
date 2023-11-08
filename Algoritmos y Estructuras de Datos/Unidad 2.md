# Tipos de Datos, Operaciones y Expresiones
## Estructuras de Datos
Dijimos que un programa es: ![[imagenes/Programa.png]]
###### <ins>Dato</ins>
Es la representación de los objetos con los que opera una computadora. 
###### <ins>Las Estructuras de Datos</ins>
Es la representación interna de datos en la computadora.
### Tipos de Datos
- ##### Númerico
	- Entero: no contienen componentes decimales. Ej `450, -325, 4, -4` 
	- Real: contienen una parte decimal. Ej `465.25, 800.02, -1036.44`
- ##### Cadena de caracteres
	- Alfabéticos
	- Alfanuméricos
- ##### Caracter
- ##### Lógico
#### Variables
Son valores que cambian a lo largo del programa. Debe identificarse y manejarse en forma de variable. Tiene:
- Nombre
- Contenido
- Tipo de Dato
`VAR nomVar: TIPO DE DATO`
![[imagenes/Variables.canvas]]
#### Constantes
Son valores que no varían durante la ejecución del algoritmo.
`CONST nomConst: TIPO DE DATO`
#### Lectura de datos
Permite introducir los datos. Puede hacerse desde el teclado, lector de códigos de barra, mouse, etc.
`LEER(nomVar1, nomVar2)`
#### Escritura de datos
Permite mostrar por pantalla datos o cadenas.
`ESCRIBIR(nomVar1, nomVar2, nomVar3, ..., nomVarN)`

## Expresiones
Las expresiones son __combinaciones válidas de operandos y operadores__.
Prioridad: 
1. ^
2. \*, /
3. +, -
4. <, >, <=, >=, =, !=
5. \[NO]
6. \[Y]
7. \[O]
Los paréntesis indican orden de prioridad 0, es decir, que se tiene que resolver de más adentro y luego ir hacia afuera.
#### Expresiones Aritméticas
Deben escribirse en una sola línea: `variable = expresión aritmética`. Por ejemplo: `n = (x + y ) / (y - 2)`.
#### Operadores Lógicos
Permiten formular condiciones complejas a partir de condiciones simples.

|Operador|Álgebra|Pseudocódigo|
|:---:|:---------:|:---------:|
|Conjunción|\[AND]|\[Y]|
|Disyunción|\[OR]|\[O]|
|Negación|\[NO]|\[NO]|