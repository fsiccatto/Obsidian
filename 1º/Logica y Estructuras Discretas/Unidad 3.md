# Teoría de Conjuntos
> [!info] Conjunto
> Es una colección de objetos. Generalmente se los nombra con letras mayúsculas: A, B, C. A los elementos del conjunto se los designa con letra minúscula: a, b, c.
> - Por **extensión**: se enumeran o listan, en caso de ser posible, todos y cada uno de los elementos del conjunto colocándolos entre llaves $\{\}$ y separados entre sí por una coma. $A = \{4, 5, 6, 7, 8\}$
> - Por **comprensión**: enunciando una propiedad o característica que es cumplicado por todos los elementos del conjunto y sólo por ellos. $A =\{x: x \in \mathbb{N} \wedge 3 < x < 9\}$

Podemos representar un conjunto a través de un Diagrama de Venn. El diagrama de Venn es una curva cerrada en la cual en el interior se colocan los elementos del conjunto y en el exterior el nombre del mismo.

> [!tldr] Conjuntos Especiales
> - Conjunto Vacío: conjunto que no tienen ningún elemento $\{ \space \} \text{ o } \emptyset$
> - Conjunto Unitario: conjunto compuesto por un solo elemento.
> - Conjunto Referencia o Universal: conjunto formado por todos los elementos relativos al tema. Se simboliza con $U$ o $X$.
### Inclusión de Conjuntos - Subconjuntos
> [!info] Definición
> El conjunto $A$ está incluido en $B$, o $A$ es un subconjunto de $B$, si todo elemento de $A$ pertence también a $B$.
> $$A \subseteq B \text{ si } (\forall x:x \in A \implies x \in B )$$ 
> Un subconjunto se denomina propio si $A \subseteq B$ y existe al menos un elemento de $B$ que no pertence a $A$.
###### Propiedades:
- Todo conjunto está incluido en sí mismo. Es decir, cualquiera sea el conjunto 𝐴: $A \subseteq A$
- El conjunto vacío está incluido en cualquier conjunto. Es decir, cualquiera sea 𝐴: $\emptyset \subseteq A$
### Igualdad de Conjuntos
> [!info] Definición
> Dos conjuntos, $𝐴$ y $𝐵$, son iguales si todo elemento de $𝐴$ es un elemento de $𝐵$ y todo elemento de $𝐵$ es un elemento de $𝐴$
> $$A = B \text{ si } \forall x:[( x\in A \implies x \in B ) \wedge ( x\in B \implies x \in A )]$$
> $$A=B \Longleftrightarrow A \subseteq B \wedge B \subseteq A$$
### Conjuntos Potencia
> [!info] Definición
> Para cualquier conjunto $𝑋$ existe un conjunto cuyos elementos son todos los subconjuntos de $𝑋$. Dicho conjunto se denomina conjunto potencia y se denota $\wp(𝑋)$ .
- $\emptyset \in \wp(X) \text{ y } X \in \wp(X)$
- Ejemplo: Sea $X = \{a, b\}, \wp(X) = \{ \emptyset, \{ a\}, \{ b \} \}$
> [!teorema] Teorema
> Si $X$ es un conjunto finito con $n$ elementos, $|\wp(X)| = 2^n$. 
### Unión de Conjuntos
> [!info] Definición
> Sean 𝐴 y 𝐵 dos conjuntos definidos en un mismo conjunto referencial 𝑋. Se llama **unión** de 𝐴 y 𝐵 al conjunto formado por todos los elementos que pertenecen a 𝐴 o a 𝐵 (usamos el “o” en sentido incluyente). Se simboliza 𝐴 ∪ 𝐵.
> $$A \cup B = \{ x / x \in A \vee x \in B \}$$
###### Propiedades
Sean 𝐴, 𝐵 y 𝐶 conjuntos definidos en un mismo conjunto referencial 𝑋. Se verifican las siguientes propiedades: 
![[imgs/propiedades de union de conjuntos.png]]
### Intersección de Conjuntos
> [!info] Definición
> Sean 𝐴 y 𝐵 dos conjuntos definidos en un mismo conjunto referencial 𝑋 . Se llama **intersección** de 𝐴 y 𝐵 al conjunto formado por todos los elementos que pertenecen a 𝐴 y a 𝐵. Se simboliza 𝐴 ∩ 𝐵 .
> $$A \cap B = \{ x / x \in A \wedge x \in B \}$$
### Conjuntos Disjuntos
> [!info] Definición
> Dos conjuntos 𝐴 y 𝐵 son **disjuntos** (o ajenos) si no tienen elementos comunes, es decir, si la intersección de ellos es el conjunto vacío.
> $$𝐴 \text{ y } 𝐵 \text{ son disjuntos si } 𝐴 ∩ 𝐵 = ∅$$
###### Propiedades
Sean 𝐴, 𝐵 y 𝐶 conjuntos definidos en un mismo conjunto referencial 𝑋. Se verifican las siguientes propiedades:
![[imgs/propiedades de conjuntos disjuntos.png]]
### Diferencia de Conjuntos
> [!info] Definición
> Sean 𝐴 y 𝐵 dos conjuntos definidos en un mismo conjunto referencial X. Se llama **diferencia** de 𝐴 y 𝐵 (en ese orden) al conjunto formado por todos los elementos de 𝐴 que no pertenecen a 𝐵. Se simboliza 𝐴−𝐵.
> $$𝐴 - 𝐵  = \{x/x \in A \wedge x \notin B \}$$
### Complemento de un Conjunto
> [!info] Definición
> Sea 𝐴 un conjunto definido en un conjunto referencial X. Se llama **complemento** de 𝐴 (con respecto a X) al conjunto formado por todos los elementos de X que no pertenecen a 𝐴. Se simboliza $𝐴^c$.
> $$𝐴^c  = \{x/x \in X \wedge x \notin A \}$$
###### Propiedades
Sea 𝐴 un conjunto definido en un conjunto referencial 𝑋 . Se verifican las propiedades:
![[propiedades complemento de un conjunto.png]]
### Leyes de Morgan
Sean 𝐴 y 𝐵 conjuntos definidos en un mismo conjunto referencial 𝑋. Se verifican las siguientes propiedades:
$$ i. (A \cup B)^C = A^C \cap B^C$$
$$ ii. (A \cap B)^C = A^C \cup B^C $$
> [!tldr] Demostración propiedad $i$
> Sean 𝐴 y 𝐵 conjuntos definidos en un mismo conjunto referencial X:
> ![[demostracion de morgan.png]]
### Diferencia Simétrica de Conjuntos
> [!info] Definición
> Sean 𝐴 y 𝐵 dos conjuntos definidos en un mismo conjunto referencial X. Se llama **diferencia simétrica** de 𝐴 y 𝐵 (en ese orden) al conjunto formado por todos los elementos de 𝐴 y 𝐵 que no pertenecen a su intersección. Se simboliza 𝐴⨁𝐵.
> $$𝐴 \oplus B  = \{x/x \in A \cup B \wedge x \notin A \cap B\}$$

Observación: $A \oplus B = A \cup B - A \cap B$
###### Propiedades
Sean 𝐴 y 𝐵 conjuntos definidos en un mismo conjunto referencial 𝑋. Se verifican las siguientes propiedades:
![[propiedades diferencia simetrica de conjuntos.png]]

---
## Conjunto Finito - Cardinal de un Conjunto
> [!info] Definición
> El conjunto 𝐴 es **finito** si 𝐴 es vacío o bien existe una función biyectiva entre el conjunto {1, 2,3,…,𝑛} y 𝐴.

> [!info] Definición
> El número de elementos del conjunto finito se llama número **cardinal** del conjunto. 
> Lo simbolizaremos:
> $$\text{card}(A) \text{ o tambien como } |A|$$
> Si 𝐴 es vacío, |𝐴|  = 0.

## Principio de Inclusión - Exclusión
> [!teorema] Teorema
> Sean 𝐴, 𝐵 y 𝐶, conjuntos finitos, entonces
> $$|A \cup B| = |A| + |B| - |A \cap B|$$
> $$|A \cup B \cup C| = |A| + |B| + |C| - |A \cap B| - |A \cap C| - |C \cap C| + |A \cap B \cap C|$$
## Conjuntos Numéricos
![[Conjunto numericos.png]]
$N \subseteq Z \subseteq Q \subseteq R$ y $R = Q \cup I$
## Partición de un Conjunto
> [!info] Definición
> Una colección finita de conjuntos no vacíos $𝐴_{1}, 𝐴_{2},.., 𝐴_{n}$ es una **partición** de un conjunto 𝐴 si y sólo si, 
> 1. 𝐴 es la unión de $𝐴_{i}$, para todo 𝑖, (𝑖 = 1..𝑛). 
> 2. Los conjuntos $𝐴_{1}, 𝐴_{2},.., 𝐴_{n}$ son mutuamente disjuntos ($𝐴_{i} \cap 𝐴_{j} = ∅, 𝑖 \neq 𝑗$).
## Par ordenado
> [!info] Definición
> Dados dos objetos 𝒂 y 𝒃, se llama **par ordenado** (𝒂,𝒃) al objeto en el cual 𝒂 es el primer elemento (primera componente) y 𝒃 es el segundo elemento (segunda componente). Es decir que $(𝒂,𝒃) \neq (𝒃, 𝒂)$ , para $𝒂 \neq 𝒃$.
### Producto Cartesiano
> [!info] Definición
> Sean 𝐴 y 𝐵 conjuntos, se lama **producto cartesiano** de 𝐴 y 𝐵 (en ese orden) al conjunto formado por todos los pares ordenados (𝑎,𝑏) tales que la primera componente es un elemento de 𝐴 y la segunda componente es un elemento de 𝐵. Se Lo simboliza 𝐴 x 𝐵.
> $$\text{A x B} = \{ (a, b)/ a \in A \wedge b \in B \}$$
# Combinatoria
La combinatoria estudia las diferentes formas en que podemos ordenar o agrupar elementos siguiendo determinadas reglas establecidas. Nos proporciona *algoritmos* para determinar la cantida de agrupaciones que se pueden formar con los elementos del conjunto.
## Regla de Multiplicación
> [!teorema] Teorema
> 