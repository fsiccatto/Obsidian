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
- La multiplicación en el conjunto de los números racionales.
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
Por lo que en un grupo 𝐺, $a{^{n}}$ está definido para cualquier entero 𝑛.

| +   | 0   | 1     |
| :-- | :-- | :---- |
| 0   | 0   | 1<br> |
| 1   | 1   | 0     |

| x   |  0  |  1  |
| :-- | :-: | :-: |
| 0   |  0  |  0  |
| 1   |  0  |  1  |
## Grupo Producto
> [!teorema] Teorema
> Si $(𝐺_{1}, ∗_{1}) , (𝐺_{2}, ∗_{2}) , … , (𝐺_{m}, ∗_{m})$ son grupos, entonces el conjunto $𝐺 = 𝐺_{1} × · · · × 𝐺_{m}$ es un grupo, con la operación ∗ definida por:
> $$(a_{1}, a_{2}, \dots, a_{m})\ast(b_{1}, b_{2},\dots, b_{m}) = (a_{1}\ast_{1}b_{1}, a_{2}\ast_{2}b_{2},\dots,a_{m}\ast_{m}b_{m})$$
## Aritmética Modular
Recordando la definición de congruencia de la U3 ![[UTN-repo/1º/Logica y Estructuras Discretas/Unidad 4#Relación de Congruencia|Unidad 4]]
El conjunto de las clases de equivalencia distintas, que constituyen una partición de $\mathbb{Z}$, se denota $\mathbb{Z_{n}}$ y se le llama el **Conjunto de Enteros Módulo $n$**
$$\mathbb{Z} = \{ [0], [1], \dots, [n-1] \}$$
> [!teorema] Teorema
> Sean 𝑎 y 𝑏 elementos de $\mathbb{Z_{n}}$, se define una **suma** y un **producto** en $\mathbb{Z_{n}}$ como:
> $$[a]+[b]=[a+b] \text{ y } [a].[b]=[a.b]$$

Observaciones:
1. Si $𝑎´∈ [𝑎] \text{ y } 𝑏´∈ [b]$ , entonces 𝑎´ ≡ 𝑎 (𝑚𝑜𝑑 𝑛) y 𝑏´ ≡ 𝑏 (𝑚𝑜𝑑 𝑛). Por lo que, 𝑎´ + 𝑏´ ≡ 𝑎 + 𝑏 (𝑚𝑜𝑑 𝑛) y 𝑎´. 𝑏´ ≡ 𝑎. 𝑏 (𝑚𝑜𝑑 𝑛). Luego
$$[𝑎´ + 𝑏´] = [𝑎 + 𝑏] \text{ y } [𝑎´. 𝑏´] = [𝑎.𝑏] \text{, }$$
es decir, las operaciones están *bien definidas*, pues no dependen de la elección de los representantes en las clases de equivalencia.
2. Las operaciones suma y producto en $\mathbb{Z_{n}}$ son *operaciones binarias asociativas*.

> [!teorema] Teorema
>  $(\mathbb{Z_{n}}, +)$ es un grupo abeliano de orden $n$:
![[Demostración grupos.png]]
## Subgrupo
> [!info] Definición
> Sea $(G, \ast)$ un grupo y H un subconjunto de G $(H \subseteq G)$, se dice que **H es un subgrupo de G**, si satisface las siguientes propiedades:
> 1. $e \in H$
> 2. Si $a, b \in H$ entonces $a \ast b \in H$
> 3. Si $a \in H$ entonces $a^{-1} \in H$

Otros subgrupos:
- Sea $m\in \mathbb{Z}$ y considerando $m\mathbb{Z} =\left\{  m.p:p \in \mathbb{Z}  \right\}$conjunto de los enteros múltiplos de $m$
- Sea (𝐺, ∗) un grupo, 𝑎 ∈ 𝐺, y sea 𝐻 = {𝑎 𝑘 : 𝑘 ∈ ℤ}. Veremos que, (𝐻, ∗) es un subgrupo de (𝐺, ∗) ya que, 𝐻 ⊆ 𝐺, y
	- Este grupo se denomina *Subgrupo Cíclico Generado por 𝑎 y se denota $𝐻 = <𝑎>$* .

> [!info] Definición
> Sea (𝐻, ∗) un subgrupo de (𝐺, ∗) , entonces 𝐻 se dirá:
> - **subgrupo impropio** de $G$, si $H=G$
> - **subgrupo trivial** de $G$ si $H={e}$
> - **subgrupo propio** de $G$ si $H$ no es impropio ni trivial
###### Propiedades
1. Si $H_{1}$ y $H_{2}$ son subgrupos de 𝐺 entonces $H_{1} \cap H_{2}$ es subgrupo de 𝐺 y también de $H_{1}$ y $H_{2}$.
2. Sea 𝐺 un grupo y sea 𝐻 un subconjunto finito no vacío de 𝐺. Si 𝐻 es cerrado con respecto a la operación en 𝐺, entonces 𝐻 es un subgrupo de 𝐺.
## Teorema de Lagrange
> [!teorema] Teorema
> Si 𝐺 es un grupo finito y 𝐻 es un subgrupo de 𝐺, entonces |𝐻| es un divisor de |𝐺|.

VER EJEMPLOS.
# Álgebra de Boole
> [!info] Definición
> Un álgebra booleana es un conjunto B, con dos operaciones binarias ∨ y ∧, una operación unaria ' y dos elementos distintos 0 y 1 que satisfacen las siguientes propiedades, para cualesquier a, b, c en B:
> 1. **Leyes asociativas**
> 	$$a \vee (b \vee c) = (a \vee b) \vee c$$
> 	$$a \wedge (b \wedge c) = (a \wedge b) \wedge c$$
> 2. **Leyes conmutativas**
> 	$$a \vee b = b \vee a$$
> 	$$a \wedge b = b \wedge a$$
> 3. **Leyes distributivas**
> 	   $$a \vee (b \wedge c) = (a \vee b) \wedge (a \vee c)$$
> 	   $$a \wedge (b \vee c) = (a \wedge b) \vee (a \wedge c)$$
> 4. **Leyes de identidad** 
> 	$$a \vee 0 = a$$
> 	$$a \wedge 1 = a$$
> 5. **Leyes de complementos**
> 	$$a \vee a' = 1$$
> 	$$a \wedge a' = 0$$

Las operaciones $\vee, \wedge \text{  y } \\'$ son llamadas unión (suma booleana), interesección (producto booleano) y complemento, respectivamente.
## Propiedades
Sea B un álgebra booleana, entonces para cualesquiera a, b ∈ B se cumple:
- Leyes de idempotencia $a \vee a = a \text{ y } a \wedge a = a$
- Leyes de acotación $a \vee 1 = 1 \text{ y } a \wedge 0 = 0$
- Leyes de absorción $a \vee(a\wedge b)=a \text{ y } a\wedge(a\vee b = a)$
- Unicidad del complemento $\text{Si } a\vee x=1 \text{ y } a\wedge x = 0, \text{ entonces } x=a'$
- Involución $a \in B, (a')' = a$
- Leyes de De Morgan $(a\vee b)' = a'\wedge b' \text{ y } (a\wedge b)' = a'\vee b'$
> [!teorema] Teorema
> Si B es un álgebra de boole finita, entonces $|B| = 2^n, n \text{ natural}$.

**Observación**: Para que un conjunto finito B sea un álgebra de boole es **condición necesaria** que tenga $2^n, n \text{ natural}$ elementos.
## Orden en Álgebra de Boole
En toda Álgebra de Boole (B, ∨, ∧, ’, 0, 1) es posible definir un **orden parcial**, **≼** , es decir una relación binaria que cumpla las propiedades reflexiva, antisimétrica y transitiva.
Sean a y b elementos de B, se define la relación **≼** como:
$$a \preccurlyeq b \iff a \wedge b = a$$
Recordemos que un orden parcial R definido en un conjunto A es una relación que cumple: 
- Reflexiva $\forall a \in A: aRa$
- Antisimétrica $\forall a,b \in A: aRb \wedge bRa \implies a = b$
- Transitiva $\forall a, b, c \in A: aRb \wedge bRc \implies aRc$
## Átomos en un Álgebra de Boole
> [!info] Definición
> Sea (B, ∨, ∧, ’, 0, 1) un Álgebra de Boole, un elemento $a \in B$ se dice que es un **átomo** de B si:
> - $0\prec a, \text{ y }$
> - no eixste $x \in B$ tal que $0 \prec x \prec a$