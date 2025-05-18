# Semántica de enunciados
La mayor parte de los lenguajes de programación definen estructuras sintácticas para construir:
- Enunciados declarativos
- Enunciados de asignación
- Enunciados de control de flujo 
- Enunciados de Input/Output que manejan la entrada y salida desde y hacia el programa
### Declaraciones
Una declaración es un enunciado de programa del tipo
``` ebnf
<tipo_de_dato><identificado>[‘(’<lista_argumentos>’)’]
```
Las declaraciones sirven para comunicar al traductor información sobre el nombre y tipo de dato de las variables, constantes o funciones/procedimientos/operaciones que se van a utilizar.
Indican también el scope, el alcance y el tiempo de vida deseada para la variable, constate u operación.

### Asignación
Toda instrucción de asignación presenta una parte izquierda (Left) relativa a ubicaciones de memoria y expresiones a la derecha (Right) relativas a valores.
```ebnf
<asignacion> ::= <variable><asignador><expresion>
```

### Control de flujo de ejecución
La semántica de control de flujo se ocupa de determinar en qué orden deben ejecutarse los enunciados y bloques de enunciados de un programa.
Los lenguajes que vemos son lenguajes **imperativos**, implican que llegan a la solución de un problema a través de un proceso de transformación de los datos o estados de la memoria.
Para estos lenguajes imperativos existen 2 formas de organizar el flujo de ejecución de los enunciados.
1. Flujo no estructurado
2. Flujo estructurado -> programación estructurada

#### Flujo no estructurado 
Este tipo de control de flujo, muy utilizado por los primeros lenguajes (Fortran, Algol), supone que los enunciados se ejecutan en secuencia, y que el programador controla explícitamente las bifurcaciones o saltos en el orden de ejecución a través de enunciados goto (ir a) y etiquetas de enunciado.
#### Flujo estructurado
Un concepto importante a tener en cuenta es que estas estructuras constituyen **enunciados básicos de entrada por salida**. Es decir, enunciados que tienen un único punto de entrada y un único punto de salida.
De esta forma, al leer un programa construído exclusivamente con enunciados de entrada por salida organizados **jerárquicamente** (estructuras anidables), el flujo de ejecución del programa deberá coincidir con el orden de los enunciados en el texto del programa.

#### Flujo estructurado vs Flujo no estructurado
La propuesta conceptual de la **Programación Estructurada**: combinar apropiadamente grupos de enunciados básicos de entrada por salida (estructuras de decisión, iteración, subrutinas, corrutinas y excepciones); donde cada uno sirve para un solo propósito (resuelve una parte del problema) dentro de la estructura global del programa.

#### Bifurcaciones
```ebnf
<bifurcacion> ::= si<expr_logica> entonces <bloque>
<bifurcacion> ::= si<expr_logica> entonces <bloque> sino <bloque>
```
##### Bifurcación Simple
Expresa la ejecución condicional de un enunciado.
![[bifurcacion simple.png | center | 400]]
##### Bifuración Doble
Expresa la alternancia entre la ejecución de un bloque u otro, pero no ambos, ante la evaluación de una condición.
![[bifurcacion doble.png | center | 400]]
##### Bifuración Múltiple
No todos los lenguajes la proveen y no todos la proveen de la misma forma. Una forma de lograr bifurcaciones múltiples es anidar bifurcaciones dobles.
Otra forma de selección múltiple es el selector de casos que sería el equivalente a la selección doble anidada de la izquierda `switch`.
El **rótulo** (valor de cada caso) tiene que ser un valor entero de cualquier tipo o carácter. Las últimas versiones de algunos lenguajes han incorporado la posibilidad de aceptar cadenas. Si no uso el `break`, lo que estoy haciendo es implementar el concepto de rótulos múltiples. La opción de descarte `default`, es opcional y de usarse debe colocarse al final para que sólo entre en ella cuando no se satisfaga ninguno de los casos previos.

##### Iteraciones
```ebnf
<iteracion> ::= mientras <expr_logica> hacer <bloque>
<iteracion> ::= repetir <expr_logica> hasta <bloque>
<iteracion> ::= para <inicial> hasta <final>[<incremento>] hacer <bloque>
```
Los primeros lenguajes implementaban las iteraciones con sentencias de control explícito **goto**.
Luego, aparecieron los que hoy conocemos.
1. Pre-test / Evaluación Inicial / Mientras
2. Post-test / Evaluación final / Repetir-Hasta
3. Midle-test (while con if)

Con cantidad determinada de ciclos
1. Enumerativa / Variar (`for`)
Ver siguientes casos!
 ![[for.png]]