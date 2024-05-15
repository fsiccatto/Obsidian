# Relaciones Binarias, Semigrupos y Grupos
## Semigrupos
> [!info] Definición
> Se $S$ un conjunto no vacío y sea $\ast$ una operación binaria sobre $S$. Si $\ast$ es *asociativo*, entonces la dupla ($S, \ast$) se denomina **semigrupo**. En otras palabras:
> $$(a \ast b) \ast c = a \ast (b \ast c)$$
> para todo $a, b, c \text{ en } S$.

Ejemplos:
- La suma en el conjunto de los números enteros positivos.
- La multiplicación en el conjunto de los números enteros postivos.
- La multiplicación en el conjunto de los números racioneles.
### Monoides
> [!info] Definición
> Se $M$ un conjunto no vacío y sea $\ast$ una operación binaria sobre $M$. Si ($M, \ast$) es un semigrupo que tiene elemento identidad, entonces la dupla ($M, \ast$) se denomina **monoide**. En otras palabras:
> - $(a \ast b) \ast c = a \ast (b \ast c)$, y
> - existe $e \in M$ tal que
> $$e \ast a = a = a \ast e$$
> para todo $a, b, c \text{ en } M$.

Ejemplos:
- La multiplicación en el conjunto de los números enteros postivos.
- La multipliación en el conjunto de los números racionales.
#### Grupos
> [!info] Definición
> Se $G$ un conjunto no vacío y sea $\ast$ una operación binaria sobre $G$. Si ($M, \ast$) es un monoide que todo elemento tiene inverso, entonces la dupla ($G, \ast$) se denomina **grupo**. En otras palabras:
> - $(a \ast b) \ast c = a \ast (b \ast c)$, y
> - existe $e \in G$ tal que $e \ast a = a = a \ast e$
> - para todo $a \in G$ existe $a^{-1} \in G$ tal que
> $$a \ast a^{-1} = e = a^{-1} \ast a$$
> para todo $a, b, c \text{ en } G$.

Ejemplos:
- La multiplicación en el conjunto de los números racionales sin el cero.
- El producto matricial en el conjunto de las matrices reales 2x2 invertibles.