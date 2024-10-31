
# Programación Funcional

## Introducción

La **programación funcional** surge para resolver tipos de problemas específicos donde los paradigmas previos resultaban inadecuados. Basada en el **cálculo lambda** de Alonzo Church, la programación funcional evita efectos secundarios, asegurando coherencia y **transparencia referencial**: una expresión siempre produce el mismo resultado. Esta guía debe complementarse con la lectura de materiales adicionales y la práctica en el lenguaje **Haskell**, que utilizamos para estudiar este paradigma.

## Historia y Origen

- **1958**: En el MIT, John McCarthy y su equipo desarrollaron **LISP**, el primer lenguaje funcional, facilitando el procesamiento simbólico y siendo clave en aplicaciones de **Inteligencia Artificial**.
- **Década de 1980**: Aparecen **Scheme** y **ML**, precursores de Haskell, diseñado para integrar las mejores características de estos lenguajes.  
- **Haskell**: Introducido en 1987, Haskell es un lenguaje funcional puro con características como evaluación perezosa, polimorfismo y clases de tipos.

## Principios Fundamentales de la Programación Funcional

### Coherencia Sintáctica y Funciones Matemáticas Puras
La programación funcional sigue principios matemáticos, minimizando errores de evaluación mediante **funciones puras** que, al no depender de estado o variables mutables, garantizan resultados predecibles.

```c
// Ejemplo en C de modelo imperativo con efectos secundarios
int bandera = 1;

int f(int n) {
    bandera = !bandera;
    return bandera ? n : 2 * n;
}

void main() {
    bandera = 1;
    printf("%d", f(1));    // muestra 2
    printf("%d", f(1));    // muestra 1
    printf("%d", f(1) + f(2)); // muestra 4
    printf("%d", f(2) + f(1)); // muestra 5
}
```

**Análisis**: En este ejemplo, el valor devuelto por `f(1)` cambia en función de la secuencia de ejecución, violando el principio de coherencia. En el paradigma funcional, al no existir asignación destructiva, una función siempre produce el mismo resultado.

### Funciones y Variables en el Modelo Funcional
En programación funcional, las funciones son tratadas como **expresiones matemáticas puras**. Esto implica que:

- Las **variables** son inmutables y existen solo como parámetros, sin variables locales.
- No hay **bucles** en el sentido tradicional, en su lugar se utiliza **recursión** para repetir operaciones.

```haskell
-- Definición de una función pura en Haskell
cubo x = x * x * x
```

Esta función siempre devolverá el mismo valor para cada entrada `x`, cumpliendo el principio de transparencia referencial.

## Haskell

Haskell implementa completamente los principios de la programación funcional, prohibiendo características de los lenguajes imperativos como la asignación destructiva y efectos laterales. <mark style="background: #BBFABBA6;">Es un sistema de inferencia de tipo</mark>.

### Sistema de Tipos
Haskell es un lenguaje **fuertemente tipado** (a toda expresión se le debe poder asociar un único tipo) y **estáticamente verificado** (los tipos se verifican en tiempo de traducción). Esto previene errores de tipo en tiempo de ejecución.

```haskell
-- Ejemplo de error de tipo en Haskell
f x = 'A'
g x = x + f x  -- Error: g intenta sumar un número con un carácter
```

**Inferencia de tipos**: El compilador de Haskell puede inferir el tipo de las expresiones:
- El programador no está obligado a declarar el tipo de las expresiones.
- El compilador contiene un algoritmo que infiere el tipo de las expresiones.
- Si el programador declara el tipo de alguna expresión, el sistema chequea que el tipo declarado coincide con el tipo inferido

```haskell
-- Ejemplo de inferencia de tipos
saluda x = if x then "adios" else "hola"
-- El sistema infiere el tipo saluda :: Bool -> String
```

### Polimorfismo
El **polimorfismo** permite que las funciones acepten argumentos de diferentes tipos. Esto facilita la reutilización de código al permitir operaciones sobre múltiples tipos.

```haskell
-- Función polimórfica que devuelve el mayor de dos valores
maximo x y = if x > y then x else y
```

Este código funciona para números, caracteres y otros tipos ordenables.

### Tipos predefinidos en Haskell
- Enteros-> Int, Integer, +, \*, -, /, ^, negate, div, mod, abs, ... 
- Flotantes -> Float, Double
- Lógicos -> Bool, True, False. &&, ||, not
- Caracteres -> Char, comillas simples, isSpace, isUpper
- Cadenas -> String, comillas dobles
- Listas -> polimórficas, finitas, infinitas, :, map
- Tuplas -> `(1, [2], 3) :: (Int, [Int], Int), ('a', False)((1, 2), (3, 4))`
- Funciones -> `algo :: Int -> (Int -> Int)`
### Listas
Haskell permite listas homogéneas (elementos de un mismo tipo) y su manipulación mediante funciones de orden superior como `map` y `filter`.
Si `a` es un tipo cualquiera, entonces `[a]` denota el tipo de lista cuyos elementos son objetos del tipo `a`.
La lista `[1, 2, 3.33, 1/2]` es una lista de `[Doubles]`.

```haskell
-- Ejemplo de una lista en Haskell
listaEnteros = [1, 2, 3]
listaMixta = [1.0, 2.5, 3.3]  -- Lista de flotantes
map negate listaEnteros       -- Resultado: [-1, -2, -3]
 ```

Las listas pueden ser **finitas** o **infinitas**:
`[1, 2, 3, 4]` es una lista finita definida por extensión.
`[1..10]` es una lista finita definida por comprensión que contendrá elementos del 1 al 10.
`[1..]` es una lista infinita de enteros definida por comprensión.

### Tuplas
A diferencia de las listas, las tuplas pueden contener diferentes tipos (son heterogéneas) y tienen un tamaño fijo.

```haskell
tuplaEjemplo = (1, "texto", True)
```

### Funciones
Si `a` y `b` son dos tipos, entonces `a -> b` denota el tipo de la función que toma como argumento un elemento de tipo `a` y devuelve un valor de tipo `b`.
El prototipo de la función `algo :: Int -> (Int -> Int)` describe en Haskell una función cuyo nombre es algo, que recibe un argumento entero y devuelve otra función de enteros en enteros.

### Precedencia y Asociatividad de Operadores en Haskell
En el standard prelude se definen 9 niveles para la jerarquía de operadores predefinidos en el lenguaje. Los operadores de mayor nivel en la jerarquía tienen precedencia sobre los de menor nivel.
![[imgs/jerarquia de operadores.png| center]]
Haskell brinda a los programadores la posibilidad de definir sus propios operadores. Estos, por defecto tienen jerarquía 9 y no son asociativos. El programador, puede alterar la jerarquía predefinida para los operadores, con declaraciones del tipo
```
<calificador> [digito] <lista>
```
donde:
- `<calificador> infixl, infixr, infix` indican asociatividad a izquierda, a derecha y sin asociatividad respectivamente.
- `[digito]` valor entre `1` y `9`. Toma `9` por defecto si se omite
- `<lista>` es el conjunto de símbolos de operador que se redefinen.
- 
### Evaluación Perezosa (*lazy evaluation*)
Una de las características más importantes de Haskell es la **evaluación perezosa**: las expresiones solo se evalúan cuando se necesitan. Esto permite trabajar con estructuras infinitas o de tamaño indeterminado.

```haskell
-- Ejemplo de evaluación perezosa con lista infinita
numeros = [1..]
-- Al tomar los primeros elementos, la evaluación solo genera lo necesario
take 5 numeros  -- Resultado: [1, 2, 3, 4, 5]
```

Uno de los beneficios de la evaluación perezosa consiste en la posibilidad de manipular estructuras de datos '**potencialmente infinitas**'
### Jerarquía de Tipos Numéricos
Haskell presenta una jerarquía de clases numéricas donde cada clase representa un tipo específico, permitiendo operaciones como comparación y suma.

```haskell
-- Ejemplo de herencia múltiple en tipos numéricos
valorEntero :: Int
valorEntero = 5  -- Es comparable (Eq), ordinal (Ord), y numérico (Num)
```

![[imgs/jerarquia de tipo numerico.png]]