# Programación Lógica
El paradigma de programación lógica deriva del cálculo de predicados, centrado en la demostrabilidad de afirmaciones. Se trata de expresar **qué** es la solución de un problema, no **cómo** calcularla, como lo haríamos en paradigmas imperativos.

En lugar de dar un algoritmo, en programación lógica definimos qué es la suma declarando hechos y reglas. Por ejemplo:
- `suma(1,1,2).` (La suma de 1 y 1 es 2).
- `suma(X,Y,Z) :- suma(Y,X,Z).` (Propiedad conmutativa).
## Prolog y sus aplicacioenes
Prolog (1972) es el lenguaje más usado para la programación lógica, con aplicaciones en:
- Sistemas expertos.
- Inteligencia artificial.
- Sistemas basados en conocimiento.

Este paradigma se basa en conceptos de lógica proposicional y predicados. Un **predicado** es una proposición sobre entidades de un dominio (ej. "Juan es programador"). Se amplía con el uso de cuantificadores para expresar reglas generales como “Todo humano es mortal”.
## Hechos y Reglas
Un programa Prolog consta de **hechos** (declaraciones categóricas) y **reglas** (predicados que infieren conclusiones). Prolog resuelve problemas estableciendo relaciones y utilizando un motor de inferencia sobre una base de conocimiento.
## Variables y Sintaxis
Las **variables** en Prolog representan entidades lógicas y se instancian según el contexto. La sintaxis requiere que los predicados terminen en punto, usen letras minúsculas y mayúsculas para variables.
Ejemplo:
- `licencia(luis,camion).`
- `utiliza(lopez,camion).`
- `trabaja(P,E):- licencia(P,V), utiliza(E,V).`
Esta regla define que una persona trabaja para una empresa si tiene licencia para el vehículo que utiliza dicha empresa.
![[imgs/sintaxis prolog.png | center]]

---
## Inferencia y Lenguaje
Prolog permite inferir nuevas conclusiones basadas en hechos y reglas previas. Este mecanismo, junto con la capacidad de acumular conocimiento, lo vincula con el aprendizaje automático (machine learning).

Definimos relaciones como:
- `padre(juan,carlos).`
- `hijo(X,P):- padre(P,X).`

Reglas como `primo(X,Y)` o `ancestro(X,Y)` permiten definir relaciones familiares más complejas, usando recursividad, una técnica clave en la programación lógica.
![[imgs/inferencia y lenguaje.png | center]]
## Consultas a la base de conocimiento
En Prolog, una de las características más destacadas es la capacidad de realizar consultas directas a la base de conocimientos. El lenguaje cuenta con un mecanismo interactivo integrado que permite realizar preguntas (consultas) sobre hechos y reglas sin necesidad de programar un sistema separado para las consultas.
### Clasificación de las consultas
Las consultas en Prolog se dividen en dos tipos:
1. **Test**: No se instancian variables, solo se verifica si una afirmación es verdadera o falsa.
   Ejemplo:
   - `?- padre(juan, carlos).` → True
   - `?- padre(omar, marcos).` → False
2. **Generador**: Instancia variables en una o más respuestas, dependiendo de los argumentos en la consulta.
   Ejemplo:
   - `?- padre(luis, X).` 
   - `X = david`; 
   - `X = omar`;
   - no

Según el número de respuestas que generan, las consultas generadoras pueden ser:
- <mark style="background: #FF5582A6;">Generador único</mark>: Una sola respuesta.
- <mark style="background: #BBFABBA6;">Generador acotado</mark>: Respuestas finitas. 
- <mark style="background: #FFB86CA6;">Generador no acotado</mark>: Respuestas infinitas.

---
## Funcionamiento de las metas
En Prolog, las consultas se conocen como **metas**. El sistema de inferencia busca predicados en la base de conocimientos que satisfagan dichas metas. Este proceso se realiza de:
- *Arriba hacia abajo* en la base de conocimiento.
- *De izquierda a derecha* cuando hay submetas.

Si la meta no puede ser satisfecha, se considera falsa, ya que Prolog usa una lógica de negación por defecto: lo que no es conocido es falso.

---
## Instanciación, Matching y Unificación
### Instanciación
Es el proceso de asignar un valor a una variable. Si se consulta con variables, el sistema intenta instanciar esas variables con los valores disponibles en la base de conocimientos.
Ejemplo:
- `?- licencia(juan, X).` → X = omnibus
### Matching
Prolog busca una **coincidencia exacta** entre la estructura del predicado y la meta solicitada. El predicado debe **coincidir completamente** con un hecho de la base de conocimientos para que sea considerado verdadero.
Ejemplo:
- `?- utiliza(radiotaxi, auto).` → True
### Unificación
Cuando se encuentra una coincidencia entre la meta y un hecho o regla, se unifican los valores instanciados con las variables, dando una respuesta. Este proceso también ocurre cuando se instancian variables dentro de una regla para satisfacer submetas.
Ejemplo:
- `?- trabaja(juan, X).` → X = tac
## Reglas y Submetas
Para consultas que involucren reglas, el motor de inferencia debe resolver primero las submetas antes de alcanzar la meta principal.
> [!example]
> Por ejemplo, para la consulta anterior, el sistema resuelve primero las submetas: licencia(juan, V), utiliza(X, V).

![[imgs/reglas y submetas.png | center]]

### Operadores `=` y `is`
Prolog distingue entre los operadores `=` y `is` en las consultas:
- **Operador `=`**: Busca una coincidencia o ligadura para instanciar una variable, sin evaluar expresiones.
   Ejemplo: `?- X = 2 + 3.` → X = 2 + 3
- **Operador `is`**: Evalúa una expresión aritmética y asigna el resultado a la variable.
   Ejemplo: `?- X is 3 + 4.` → X = 7
### Variables Anónimas
Las variables anónimas, representadas por un guion bajo `_`, se utilizan cuando no se necesita instanciar un valor específico en una consulta. Sirven para indicar la existencia de un argumento sin interés en su valor exacto.
Ejemplo:
- `?- trabaja(juan, _).`
### Símbolo de Disponibilidad (`;`)
El uso del símbolo de disponibilidad permite al usuario indicar si espera que el MI calcule más resultados para una consulta.

---
## Inducción y Recursión
La **recursión** es un principio esencial en la programación lógica, donde un **predicado** se define en términos de sí mismo para resolver problemas complejos de manera eficiente. Este proceso se basa en el razonamiento inductivo, particularmente en el esquema lógico del **Modus Ponens**, que va de lo particular a lo general.
![[imgs/induccion y recursion.png| center]]

### Factores claves de la Recursión
1. **Base inductiva (axioma)**: Se define un caso base conocido como verdadero, lo cual establece un punto de escape para la recursión.
2. **Hipótesis inductiva (regla recursiva)**: Establece cómo se resuelve el problema en términos de una versión simplificada de sí mismo.
![[imgs/induccion y recursion 2.png| center]]

> [!example] Ejemplo: Cálculo del Factorial
> En álgebra, el factorial de un número `n` se define como:
> $$
\begin{align}n! =
\begin{cases}
1 \text{ si } n= 0 \\
n  (n-1)! \text{ si } n > 0
\end{cases}
\end{align}
> $$
> En Prolog se expresa mediante un hecho base y una regla recursiva:
> - `facto(0,1).`
> - `facto(X,N):- X>0, T is X-1, facto(T,Z), N is X*Z.`

Explicación del Proceso: Cuando el motor de inferencia de Prolog se encuentra con la consulta `facto(2,X)`, el motor evalúa los siguientes pasos:
1. **Base inductiva**: `facto(0,1)` establece que el factorial de 0 es 1.
2. **Hipótesis inductiva**: La regla recursiva aplica la fórmula del factorial para valores mayores que 0, generando nuevas submetas hasta alcanzar el caso base.
Al procesar `facto(2,X)`, Prolog resuelve las siguientes submetas:
- `facto(1,Z)`
- Luego, `facto(0,1)`, que satisface la condición base.
- A medida que el proceso vuelve a escalar, Prolog evalúa las expresiones pendientes, unificando las variables con los valores resultantes

---
## Árbol de resolución
El árbol de resolución es la representación gráfica del proceso de búsqueda de soluciones en Prolog, usando un enfoque de búsqueda en profundidad de izquierda a derecha. Cada **nodo** representa una **meta o submeta**, y el árbol se expande a medida que se unifican predicados con las metas.
> [!example] Ejemplo: Máximo Común Divisor (MCD)
> Supongamos que queremos resolver la meta mcd(63,42,R). El árbol de resolución para este ejemplo se construye de la siguiente manera:
> 1. Raíz del árbol: La meta `mcd(63,42,R)`
> 2. Submetas:
>    - `X > Y` se evalúa primero y se satisface.
>    - `T` is `X mod Y` se resuelve como `T = 21`.
>    - La siguiente meta es `mcd(21,42,R)`, y el proceso continúa.
>  
>![[imgs/arbol de derivacion.png| center]]

## Backtracking
El proceso de **backtracking** ocurre cuando una meta no puede satisfacerse por un camino específico. En este caso, el motor de inferencia retrocede al último punto de decisión y busca una alternativa.
