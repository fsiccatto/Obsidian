# Definiciones Funcionales y Recursión
## Definición de Funciones en Haskell

### Formas de Definir Funciones
En Haskell, una función puede ser nombrada mediante un identificador (como `suma`) o un operador (`+`). Existen tres estructuras sintácticas principales:

1. **Patentizada o por Patrones**
La función recibe los argumentos en una sola expresión.
   
   ```haskell
   suma :: (Int, Int) -> Int
   suma (x, y) = x + y
   ```

   ```haskell
   mayor :: Ord a => (a, a) -> a
   mayor (x, y) = if x > y then x else y
   ```

2. **Currificación**
Utiliza la aplicación parcial de funciones, eliminando la necesidad de paréntesis.
   
   ```haskell
   suma :: Int -> Int -> Int
   suma x y = x + y
   ```

   ```haskell
   potencia :: Integer -> Integer -> Integer
   potencia b 0 = 1
   potencia b e = b * potencia b (e - 1)
   ```

3. **Expresiones Lambda**
Define funciones anónimas que se evalúan en el momento.

   ```haskell
   (\x y -> x + y) 4 3  -- Resultado: 7
   (\x -> x * x) 5      -- Resultado: 25
   ```

## Definiciones funcionales

- Sintaxis de definición
```Haskell
<nombre> :: [<tipo-arg1> {-> <tipo-argn>} ->]<tipo-devol>
{<nombre> {<blanco><arg>} = <expresion>}+
```
- Sintaxis de llamada
```Haskell
<nombre>{<blanco><arg>}
```
- Formato de código
	- tabular (alineación por columnas)
	- diferencia mayúsculas/minúsculas

Para definir una función debemos determinar:
✔ **Prototipo**: nombre de la función, seguido opcionalmente por una lista de uno o más parámetros formale sseguidos por el tipo de valor que devulve.
✔ **Expresiones funcionales**: una o más declaraciones que permiten el *patter-matching* con el prototipo y determinan la expresión que evalúa la función.
### Composición de Funciones
La composición funcional se expresa como `(f . g) x = f (g x)`, permitiendo aplicar funciones de manera eficiente.

```haskell
cuadrado :: Integer -> Integer
cuadrado x = x * x

bicuadrado :: Integer -> Integer
bicuadrado x = cuadrado (cuadrado x)  -- Más eficiente que x*x*x*x
```

## Guardas y Patrones
Las **ecuaciones con guardas** permiten definir condiciones sobre los argumentos de las funciones, proporcionando flexibilidad.

```haskell
-- Versión con guardas
fib :: Integer -> Integer
fib n
  | n == 0 = 0
  | n == 1 = 1
  | n > 1 = fib(n - 1) + fib(n - 2)
```

Alternativamente, el **encaje de patrones** se usa para definir casos específicos de la entrada.

```haskell
-- Versión con patrones
fib :: Integer -> Integer
fib 0 = 0
fib 1 = 1
fib n = fib(n - 1) + fib(n - 2)
```

![[imgs/algunas definiciones.png]]
Las restricciones de tipo son declaraciones de la forma `Tipo a` donde `Tipo` es el nombre de una clase (`Eq, Num, Ord`, etc) y `a` es una variable de tipo. Podemos definir un tipo de datos recibido o devuelto por una función que sea de más de una clase a la vez.
## Declaraciones Locales
En los lenguajes funcionales no existe el concepto de variable local como espacio de memoria definido al interior de una función. Sin embargo, Haskell permite declaraciones locales mediante las cláusulas `where` y `let-in`.
### Cláusula `where`
Define variables locales al final de una expresión.

```haskell
f :: (Float, Float) -> Float
f (x, y) = (a + 1) * (b + 2)
  where
    a = (x + y) / 2
    b = (x + y) / 3
```

### Cláusula `let-in`
Define variables dentro de cualquier expresión.

```haskell
l :: (Float, Float) -> Float
l (x, y) = let c = 2 * x; m = 2 * y in c * m + y + log c
```

## Condicionales e Iteraciones
### Condicionales `if` y `case`
La estructura `if` es similar a otros lenguajes, mientras que `case` evalúa la expresión y selecciona un resultado.

`if <expre bool> then <expre> else <expre>`
```haskell
compara :: Ord a => (a -> a -> Bool) -> a -> a -> Bool
compara f a b = if f a b then True else False
```

`case <expre> of [<expre> -> <expre>]+`
```haskell
-- Función map utilizando case y expresiones lambda
map = \f xs -> case xs of
                  []     -> []
                  (y:ys) -> f y : map f ys
```

### Iteración con `until`
La función `until` aplica una expresión hasta que se cumpla una condición.
`until :: (a -> Bool) -> (a -> a) -> a -> a`
donde: 
- `(a->Bool)` representa la condición a evaluar en cada iteración, que aplica sobre un objeto de algún tipo `a` y devuelve un valor booleano.
- `(a->a)` representa la expresión que se evalúa en cada iteración. Es una función de algún tipo `a` que aplica sobre un argumento del mismo tipo. 
- `a` representa el valor inicial desde el cuál se comienza a iterar. Debe ser del mismo tipo `a`.
- `a` representa el tipo de valor devuelto para la función.
```haskell
-- Duplicar el valor inicial hasta superar el límite
duplicar :: (Integer, Integer) -> Integer
duplicar (x, l) = until (> l) (* 2) x
```

## Conversiones de Tipo y Entrada/Salida
Para manejar caracteres y conversiones de tipo, se usa el módulo `Char`.

```haskell
import Char
digitToInt 'A'   -- Resultado: 10
read :: Read a => String -> a
```

## Coincidencia de Patrones (Pattern Matching)
El **encaje de patrones** es fundamental para definir funciones que procesan listas, tuplas, y expresiones complejas.

```haskell
f1 :: Int -> Int -> Int
f1 x y = if x == y then 1 else 0
```

## Recursión
La **recursión** es clave en la programación funcional para reemplazar estructuras iterativas. Al definir una función recursiva, se establece un caso base y una llamada recursiva.

### Ejemplos

1. **Producto mediante sumas**
   
   ```haskell
   producto :: Int -> Int -> Int
   producto x y = if x == 0 then 0 else y + producto (x - 1) y
   ```

2. **Paridad de un número sin `mod`**

   ```haskell
   impar :: Int -> Bool
   impar x
     | abs x == 0 = False
     | abs x == 1 = True
     | otherwise = impar (abs x - 2)
   ```

3. **Conversión a binario**

   ```haskell
   binario :: Int -> String
   binario x
     | x == 0 = "0"
     | x == 1 = "1"
     | otherwise = if even x
                   then binario (x `div` 2) ++ "0"
                   else binario (x `div` 2) ++ "1"
   ```
