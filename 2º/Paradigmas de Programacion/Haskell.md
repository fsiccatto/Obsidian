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

