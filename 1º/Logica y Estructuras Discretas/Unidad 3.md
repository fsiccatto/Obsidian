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

## Inclusión de Conjuntos - Subconjuntos
> [!info] Definición
> El conjunto $A$ está incluido en $B$, o $A$ es un subconjunto de $B$, si todo elemento de $A$ pertence también a $B$.
> $$A \subseteq B \text{ si } (\forall x:x \in A \implies x \in B )$$ 
> Un subconjunto se denomina propio si $A \subseteq B$ y existe al menos un elemento de $B$ que no pertence a $A$.

###### Propiedades:
- Todo conjunto está incluido en sí mismo. Es decir, cualquiera sea el conjunto 𝐴: $A \subseteq A$
- El conjunto vacío está incluido en cualquier conjunto. Es decir, cualquiera sea 𝐴: $\emptyset \subseteq A$
## Igualdad de Conjuntos
> [!info] Definición
> Dos conjuntos, $𝐴$ y $𝐵$, son iguales si todo elemento de $𝐴$ es un elemento de $𝐵$ y todo elemento de $𝐵$ es un elemento de $𝐴$
> $$A = B \text{ si } \forall x:[( x\in A \implies x \in B ) \wedge ( x\in B \implies x \in A )]$$
> $$A=B \Longleftrightarrow A \subseteq B \wedge B \subseteq A$$

## Conjuntos Potencia
> [!info] Definición
> Para cualquier conjunto $𝑋$ existe un conjunto cuyos elementos son todos los subconjuntos de $𝑋$. Dicho conjunto se denomina conjunto potencia y se denota $\rho(𝑋)$ .

- $\emptyset \in \rho(X) \text{ y } X \in \rho(X)$
- Ejemplo: Sea $X = \{a, b\}, \rho(X) = \{ \emptyset, \{ a\}, \{ b \} \}$
> [!teorema] Teorema
> Si $X$ es un conjunto finito con $n$ elementos, $|\rho(X)| = 2^n$. 

## Unión de Conjuntos
> [!info] Definición
> Sean 𝐴 y 𝐵 dos conjuntos definidos en un mismo conjunto referencial 𝑋. Se llama **unión** de 𝐴 y 𝐵 al conjunto formado por todos los elementos que pertenecen a 𝐴 o a 𝐵 (usamos el “o” en sentido incluyente). Se simboliza 𝐴 ∪ 𝐵.
> $$A \cup B = \{ x / x \in A \vee x \in B \}$$

###### Propiedades
Sean 𝐴, 𝐵 y 𝐶 conjuntos definidos en un mismo conjunto referencial 𝑋. Se verifican las siguientes propiedades: 
![[imgs/propiedades de union de conjuntos.png]]
## Intersección de Conjuntos
> [!info] Definición
> Sean 𝐴 y 𝐵 dos conjuntos definidos en un mismo conjunto referencial 𝑋 . Se llama **intersección** de 𝐴 y 𝐵 al conjunto formado por todos los elementos que pertenecen a 𝐴 y a 𝐵. Se simboliza 𝐴 ∩ 𝐵 .
> $$A \cap B = \{ x / x \in A \wedge x \in B \}$$

## Conjuntos Disjuntos
> [!info] Definición
> Dos conjuntos 𝐴 y 𝐵 son **disjuntos** (o ajenos) si no tienen elementos comunes, es decir, si la intersección de ellos es el conjunto vacío.
> $$𝐴 \text{ y } 𝐵 \text{ son disjuntos si } 𝐴 ∩ 𝐵 = ∅$$

###### Propiedades
Sean 𝐴, 𝐵 y 𝐶 conjuntos definidos en un mismo conjunto referencial 𝑋. Se verifican las siguientes propiedades:
![[imgs/propiedades de conjuntos disjuntos.png]]

## Diferencia de Conjuntos
