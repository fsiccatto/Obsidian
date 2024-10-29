Prototipo en linea 1 (parametros de entrada y salida)
IMPORTA EL ORDEN!!!
nombre :: (tipoDeDato) -> (tipoDeDato) -- cabecera prototipo **currificada** (que tiene espacios `par 0 = True`) patrones par
``` Haskell
par :: Int -> Bool
```

Despues vienen los hechos, que son las razones de corte de la recursión
- con **patrones**
```Haskell
par :: Int -> Bool
-- patrones
par 0 = True
par 1 = False
par n = par (n-2)
```
puede ser tambien parentizada.
```Haskell
par (0) = True
par (1) = False
par (n) = par ((n-2))
```

- con **guarda** (pipe)
```Haskell
parG :: Int -> Bool
-- guardas
parG n
	|n == 0 = True
	|n == 1 = False
	|otherwise = parG (n-2)
```

### Ejemplo
```Haskell
potencia :: Int -> Int -> Int
potencia b 0 = 1
potencia b e = (potencia b (e-1)) * b
```

```Haskell
potenciac :: (Int, Int) -> Int
potenciac (b, 0) = 1
potenciac (b, e) = potenciac (b,(e-1)) * b
```

```Haskell
potenciaG :: Int -> Int -> Int
potenciaG b e
	|e == 0 = 1
	|e == 1 = b
	|otherwise = (potenciaG b (e-1)) * b
```

## Listas
### Inductiva
```Haskell
suma :: (Num a) => [a] -> a
suma [] = 0
suma (c:q) = c + (suma q)
```
Hago referencia a un Num a y puede contener Num en la lista y puede devolver Num. Tambien se puede hacer como sigue:
```Haskell
suma :: [Int] -> Int
suma [] = 0
suma (c:q) = c + (suma q)
```
### Recursiva
```Haskell
sumaR :: (Num a) => [a] -> a
sumaR [] = 0
sumaR 1 = head 1 + sumaR(tail 1)
```

```Haskell
SumaG :: (Num a) => [a] -> a
	|lista == [] = 0
	|tail lista == [] = head lista -- si es una lista unitaria
	|otherwise = head lista + sumaG(tail lista)
```

```Haskell
ultimo :: [Maybe a] -> Maybe a
ultimo [] = Nothing
utlimo [a] = a
ultimo (c:q) = ultimo q
```

```Haskell
ultimoG :: Eq a => [a] -> a
ultimoG x
	|tail x == [] = head x
	|otherwise =  ultimoG (tail x)
```

## Clase 28/10
Concatenar dos listas
`lista1 ++ lista2` seria como el `append(A, B, C)`
`C:q == [C | Q]`
## Estructuras de Datos
### Funciones lambda
``` Haskell
(\x y -> if x > y then x else y) 5 10 -- 7) Int -> Int -> Int
(\x -> if mod x 2 == 0 then True else False) -- 8) Par impar
(\x -> parH(x)) 10 --Verficacion
```

### map
```Haskell
potencia :: (Int, Int) -> Int
potencia (b, 0) = 1
potencia (b, e) = potencia (b, (e - 1)) * b

map (potencia 2) [1, 2, 3] --consola
```

### first - second (`fst() - snd()`)
`[a]` es una lista de tipo genérico
```Haskell
parejas :: [a] -> [a] -> [(a, a)] --mismo tipo de dato generico
parejas [] [] = []
parejas (xh:xt) (yh:yt) = (xh,yh) : (parejas xh yt) --asumimos que son listas de la misma longitud
```
Si queremos usar otro tipo distinto de dato generico tendriamos que hacer
`parejas :: (Eq a) => [a] -> [b]`

### Ejercicio 24
```Haskell
data Mov = N Int | S Int | E Int | O Int
data Paseo a = Pasos Mov (Paseo a) | Descansa a

p1 = Pasos (N 20) (Pasos(E 30) (Pasos (S 10) (Pasos (O 40) (Descansa 0))))
```

### Ejercicio 27 
```Haskell
data Arbol a = Hoja a | Nodo (Arbol a) (Arbol a)

-- a1 :: Arbol
a1 = Nodo(Nodo (Hoja 45) (Hoja 78)) (Nodo (Hoja 12) (Nodo (Hoja 23) (Hoja 13)))
a2 = Nodo(NOdo (Hoja 45) (Hoja 78)) (Nodo (Hoja 12) (Nodo (Nodo (Hoja 30) (Hoja 30)) (Hoja 13)))
```

```Haskell
-- Devolver la cantidad de nodos hojas
cantidad :: Arbol a -> Int
cantidad (Hoja x) = 1
cantidad (Nodo x y) = cantidad x + cantidad y
```

```Haskell
-- Devolver una lista de los nodos hojas del arbol
barrido :: Arbol a -> [a]
barrido (Hoja x) = [x]
barrido (Nodo x y) = barrido x ++ barrido y
```
