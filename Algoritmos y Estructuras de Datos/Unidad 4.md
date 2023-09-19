# Suprogramas. Funciones y Procedimientos
## Subprogramas
Nos permiten organizar los problemas complejos y agrupar acciones repetitivas. Los beneficios:
- Menor escritura
- Mayor claridad en la lectura
- Mayor facilidad para modificar sin alterar todo el programa
- Mayor posibilidad de reutilización, incluso con otros programadores
- Mejora la distribución de las tareas entre los programadores

![[Subprograma|300|center]]
### Encabezamiento de Subprogramas
Contiene:
- Tipo de subprograma: Procedimiento o Función
- Nombre del subprograma
- Lista de parámetros
	- Se pasan los valores con los que se debe trabajar el subprograma. Pueden ser constantes, variables, expresiones o funciones.
	- La correspondencia son uno a uno en la misma posición, mismo tipo de dato y misma cantidad.
	- A los parámetros que se usan en el programa que llama son **parámetros reales**.
	- A los parámetros que se usan en el subprograma son **parámetros formales**.
#### Tipos de Subprogramas
| | Procedimiento| Programa|
|--|--------------|-------------|
|Cantidad de Resultados|0... n|1|
|Lugar donde se devuelve el resultado| Parametros| Nombre de la funcion|
|Forma de llamarla|Linea de programa|Expresion|
|Asignacion de lectura y escritura|Si permite|No permite|

![[Subprogramas|center]]
##### Procedimientos
```
PROCEDIMIENTO nombre (lista de parametros formales: tipo de variable)
VAR
(declaracion de variables locales)
INICIO
	Acciones
FINPROCEDIMIENTO
```
##### Funciones
```
FUNCION nombre (lista de parametros formales: tipo de variable): tipo de resultado
VAR
(declaracion de variables locales)
INICIO
	Acciones
	nombre = expresion/variable
RETORNO
```

### Parámetros
A través de la lista de parámetros **se pasan los valores o las direcciones** donde se encuentran los valores, con los que debe trabajar el subprograma.
#### Clasificación de Parámetros
- Entrada: proporcionan los valroes desde el programa o subprograma que llama.
- Salida: valores resultantes del subprograma. Las funciones no usan parámetreos de salida, ya que el resultado lo devuelven en el nombre.
- Entrada/Salida: un mismo parámetro sirve para mandar argumentos a un subprograma y para devolver el resultado.
#### Pasaje de Parámetros
##### Por valor
- Es la forma mas simple. Se comunica con los programas enviando una **copia de la variable original**.
- El subprograma recibe los valores, como valores iniciales, ejecuta las acciones, pero no los devulve con otros valores. No afecta la variable original del programa.
- **Las funciones siempre utilizan parámetros por valor y devuelve el resultado en el nombre de la función**.
##### Por Referencia
- Se comunican los programas, pero el parámetro se escribe en la dirección de la misma.
- El subprograma **recibe la dirección de las variables**, por lo tanto todo lo que ejecute o modifique sobre el parámetro formal recibido, se están realizando directamente en la variable original, ya que es adonde apunta el parámetro formal.
- Se debe **anteponer** en la lista de parámetros formales **"por ref."** al nombre de la variable para indicar que es por referencia.
### Variables
Según el ámbito se definen en:
- ###### Globales
	Se declaran y definen en el programa principal y su **alcance es amplio**, tiene influencia en los subprogramas también.
- ###### Locales
	Se declaran y definen en el subpograma, pero **solo existe dentro** del subprograma.
