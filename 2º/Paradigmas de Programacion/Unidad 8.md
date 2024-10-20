# Programación Lógica
## Listas
Las listas en Prolog son una estructura de datos fundamental que permite almacenar secuencias de elementos, ya sean números, átomos, variables u otras listas, lo que facilita la creación de listas anidadas. Algunas características clave son:
- **Listas unitarias y vacías**:
  - `[x]`: Lista con un solo elemento.
  - `[]`: Lista vacía.
  
- **Listas heterogéneas**: Prolog acepta listas con elementos de diferentes tipos.
> [!example] Ejemplo
> `[1, a, [b, c], foo(3)]`.

- **Cabeza y cola de una lista**:  
  El operador `|` divide la lista en cabeza y cola: `[C|L]`. La cabeza (C) es el primer elemento y la cola (L) es el resto de la lista.
> [!example] Ejemplo
> En `[[1,2], [a,b,c], [4,5,6], [d,e,f]] == [C|Q]`, la cabeza C es `[1,2]` y la cola Q es `[[a,b,c], [4,5,6], [d,e,f]]`.
![[imgs/listas.png]]
### Unificación de Listas
La unificación de listas sigue las mismas reglas que la de otros términos en Prolog, pero teniendo en cuenta la estructura de cabeza y cola.
## Ejemplos

### CASO 1: Búsqueda de una lista
- **Predicado**: `buscar/3` que busca el elemento en una posición específica de la lista.
```prolog
buscar(1, [E|_], E).
buscar(P, [_|L], E) :- P1 is P - 1, buscar(P1, L, E).
```
Este predicado busca recursivamente el elemento en la posición indicada, restando uno en cada paso hasta llegar a la cabeza de la lista.
![[imgs/caso1.png]]
### CASO 2: Concatenación de listas
- **Predicado**: `unir/3` que concatena dos listas en una tercera.
```prolog
unir([], L2, L2).
unir([C|L1], L2, [C|L3]) :- unir(L1, L2, L3).
```
La idea es agregar la cabeza de la primera lista (L1) a la nueva lista y seguir concatenando el resto de la cola.
![[imgs/caso2.png]]
### CASO 3: Variaciones sin repetición
- **Predicado**: `variar/3` que genera variaciones sin repetición de N elementos de una lista.
```prolog
remover(A, [A|B], B).
remover(A, [B|D], [B|E]) :- remover(A, D, E).

variar(0, _, []).
variar(N, L, [X|Q]) :- P is N - 1, remover(X, L, R), variar(P, R, Q).
```
Aquí, se genera una variación seleccionando un elemento, eliminándolo de la lista, y aplicando recursivamente el proceso hasta que se obtienen las variaciones deseadas.
### CASO 4: Remover extremos de una lista
- **Predicado**: `extremos/2` que elimina el primer y último elemento de una lista.
```prolog
ultimo([], _) :- fail.
ultimo([X], X).
ultimo([_|Q], Y) :- ultimo(Q, Y).

extremos([_|Q], D) :- ultimo(Q, Y), remover(Y, Q, D).
```
Se obtiene el último elemento con el predicado auxiliar `ultimo/2` y luego se remueve de la cola para obtener la lista sin extremos.
![[imgs/caso4.png]]

---
## Términos Compuestos y Predicados Anidados
Prolog permite anidar predicados en tantos niveles como se necesite, lo que permite trabajar con predicados como si fueran estructuras de datos.
> [!example]
> Un ejemplo es manejar a las personas y sus características en una empresa:
> ```prolog
>persona(juan, perez, 123, m).
>empleado(persona(juan, perez, 123, m)).
>gerente(persona(ana, gomez, 456, f)).
>responsable(persona(juan, perez, 123, m), persona(ana, gomez, 456, f)).
> ```

La consulta `?- responsable(X, Y).` generará todas las personas responsables (X) de cualquier otra persona (Y), mientras que la consulta `?- empleado(persona(X,Y,Z,m)).` generará todas las personas masculinas (m) junto con su nombre, apellido y legajo.
## Backtracking (Regresión)
El *backtracking* en Prolog es un mecanismo que explora todas las posibilidades de satisfacción de una meta, retrocediendo cuando una solución falla y buscando caminos alternativos. Por ejemplo, si una consulta tiene varias soluciones posibles, Prolog intentará encontrar todas las que cumplan la condición.
```prolog
cliente(persona(alejandro, _, _, _), banco(nacion)).
```
Prolog retrocede para verificar todas las instancias de `persona` y sus relaciones hasta encontrar todas las soluciones posibles que satisfacen la consulta.
![[imgs/backtracking.png]]
## Operador de "corte" u **cut (!)**
El operador de corte se utiliza para evitar el backtracking en ciertos puntos de un programa. Este operador permite "podar" el árbol de búsqueda y evitar la exploración de ramas innecesarias, optimizando el proceso.
```prolog
padre(X) :- progenitor(X), !, varon(X).
```
Aquí, una vez que se encuentra un progenitor varón, se evita seguir buscando más progenitores en caso de que ya no tenga sentido.
![[imgs/operador de corte.png]]