# Operaciones Binarias, Semigrupos y Grupos
## Operación Binaria
> [!info] Definición
> Una **operación binaria** $\ast$ en un conjunto no vacío 𝐴 es una función $\ast$∶ 𝐴 x 𝐴 → 𝐴. Se escribe 𝑎 $\ast$ 𝑏.
> Una operación binaria $\ast$ en un conjunto vacío $A$ es:
> - *asociativa*: si $(a \ast b) \ast  c = a \ast (b \ast c) \space \forall a, b, c \in A$
> - *conmutativa*: si $a \ast b = b \ast a \space \forall a, b \in A$
### Semigrupos
> [!info] Definición
> Sea $S$ un conjunto no vacío y sea $\ast$ una operación binaria sobre $S$. Si $\ast$ es *asociativo*, entonces la dupla ($S, \ast$) se denomina **semigrupo**. En otras palabras:
> $$(a \ast b) \ast c = a \ast (b \ast c)$$
> para todo $a, b, c \text{ en } S$.

Ejemplos:
- La suma en el conjunto de los números enteros positivos.
- La multiplicación en el conjunto de los números enteros postivos.
- La multiplicación en el conjunto de los números racioneles.
### Monoides
> [!info] Definición
> Sea $M$ un conjunto no vacío y sea $\ast$ una operación binaria sobre $M$. Si ($M, \ast$) es un semigrupo que tiene elemento identidad, entonces la dupla ($M, \ast$) se denomina **monoide**. En otras palabras:
> - $(a \ast b) \ast c = a \ast (b \ast c)$, y
> - existe $e \in M$ tal que
> $$e \ast a = a = a \ast e$$
> para todo $a, b, c \text{ en } M$.

Ejemplos:
- La multiplicación en el conjunto de los números enteros postivos.
- La multipliación en el conjunto de los números racionales.
### Grupos
> [!info] Definición
> Sea $G$ un conjunto no vacío y sea $\ast$ una operación binaria sobre $G$. Si ($G, \ast$) es un monoide que todo elemento tiene inverso, entonces la dupla ($G, \ast$) se denomina **grupo**. En otras palabras:
> - $(a \ast b) \ast c = a \ast (b \ast c)$, y
> - existe $e \in G$ tal que $e \ast a = a = a \ast e$
> - para todo $a \in G$ existe $a^{-1} \in G$ tal que
> $$a \ast a^{-1} = e = a^{-1} \ast a$$
> para todo $a, b, c \text{ en } G$.

Ejemplos:
- La multiplicación en el conjunto de los números racionales sin el cero.
- El producto matricial en el conjunto de las matrices reales 2x2 invertibles.
### Semigrupos-Monoides-Grupos
> [!info] Definición
> Si $(G, \ast)$ es un grupo (monoide o semigrupo) y la operación binara $\ast$ es conmutativa, $(G, \ast)$ se denomina *abeliano* o *conmutativo*.
> 
> Un grupo $(G, \ast)$ se dice que es finito, si $G$ lo es. En este caso, el número de elementos de $G$ es llamado el *orden* del grupo
#### Propiedades
- El elemento identidad de un grupo o monoide es único.
- El elemento inverso de cada elemento en un grupo es único.

Si $(G, \ast)$ es un grupo y $a,b,c$ son elementos cualesquiera de $G$ entonces:
1. $(a^{-1})^{-1}=a$
2. $(a*b)^{-1} = b^{-1} \ast a^{-1}$
3. $a \ast b = a \ast c$ implica que $b=c$
4. $b \ast a = c \ast a$ implica que $b=c$
#### Potencias
- Sea (𝑆, ∗) un semigrupo. Para cualquier 𝑎 ∈ S se define:
$$𝑎{^{1}} = 𝑎$$
$$𝑎{^{n}} = 𝑎 ∗ 𝑎{^{n-1}} \text{   ,   } 𝑛 = 2, 3 . ., 𝑛 ∈ ℕ$$
Cualesquiera sean 𝑎 ∈ 𝑆 y 𝑛, 𝑚 ∈ ℕ, se verifica que:
$$i. \space 𝑎{^{n}}∗ 𝑎{^{m}} = 𝑎{^{n+m}}$$
$$ii. \space (𝑎{^{n}} ){^{m}} = 𝑎{^{n.m}}$$
- Sea (𝐺, ∗) un grupo. Para cualquier 𝑎 𝜖 𝐺 se define:
$$𝑎 {^{0}} = 𝑒 $$
$$𝑎{^{-n}} = (𝑎{^{-1}}){^{n}} \space ∀𝑛 ∈ ℕ$$
Por lo que en un grupo 𝐺, $a{^{n}}$ está definido para cualquier entero 𝑛