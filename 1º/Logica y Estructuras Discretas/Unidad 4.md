# Relaciones de Orden y de Equivalencias
## Relaciones Binarias
> [!info] Definición
> Sea 𝐴 un conjunto no vacío. Una **relación binaria** en 𝐴, es un subconjunto 𝑅 de 𝐴×𝐴:
> Si $(a, b) \in R$, se escribe $aRb$, y se dice que "a está relacionado con b".
> Si $(a, b) \notin R$, se denota $\neg (aRb)$ o bien $𝑎\cancel{R}𝑏$.
### Matriz de una Relación Binaria
> [!info] Definición
> Sea $A = \{ a_{1},\dots, a_{n}\}$ un conjunto finito, y sea $R$ una relación binaria en $A$. Podemso describir $R$ por medio de la matriz:
>$$
>M_{R} = \begin{bmatrix}
> r_{11} & r_{12} & \dots & r_{1n} \\
> r_{12} & r_{22} & \dots & r_{2n} \\
> \vdots & \vdots & \ddots & \vdots \\
> r_{n2} & r_{n2} & \dots & r_{nn} \\
\end{bmatrix}
>$$
>donde $r_{ij}=1 \text{ si } a_{i}Ra_{j} \text{ o } r_{ij}=0 \text{ en otro caso}$
>Se escribe $M_{R} = (r_{ij})$ y se llama la *matriz de relación R*.
### Digrafo de una Relación Binaria
> [!info] Definición
> Sea 𝐴 es un conjunto finito, y sea 𝑅 una relación binaria en 𝐴. Podemos representar gráficamente a 𝑅 por medio de un **digrafo** o grafo dirigido del siguiente modo: por cada elemento de 𝐴 se dibuja un punto, al que llamaremos *vértice* del dígrafo y se dibuja una *flecha* o arista vértice dirigida desde el vértice 𝑎 hasta el 𝑏 si (𝑎 , 𝑏) ∈ 𝑅.
### Propiedades de las Relaciones Binarias
> [!info] Definición
> Sea 𝑅 una relación binaria sobre un conjunto 𝐴.
> - R es **reflexiva** si y sólo si, $\text{para toda } x \in A,\space xRx$.
> - R es **simétrica** si y sólo si, $\text{para toda } x, y \in A, \text{ si } xRy \text{ entonces } yRx$.
> - R es **transitiva** si y sólo si, $\text{para toda } x, y, z \in A,\text{ si } xRy \text{ y } yRz \text{ entonces } xRz$.
> - R es **antisimétrica** si y sólo si, $\text{para toda } x, y \in A, \text{ si } xRy \text{ y } yRx \text{ entocnes } x=y$.
## Relación de Equivalencia
> [!info] Definición
> Una relación binaria $R$ en un conjunto $A$ es una **Relación de Equivalencia** en $A$ si es reflexiva, simétrica y transitiva.
### Clases  de Equivalencia
> [!info] Definición
> Sea 𝐴 un conjunto y 𝑅 una relación de equivalencia de 𝐴 . Para cada elemento 𝑎 en 𝐴, la clase de equivalencia de 𝒂, que se denota \[a] , es el conjunto de todos los elementos 𝑥 en 𝐴 tales que 𝑥 está relacionado con 𝑎 por 𝑅.
> $$[a] = \{ x \in A / xRa \}$$
## Relación de Congruencia
> [!info] Definición
> Sean 𝑎 y 𝑏 enteros y sea 𝑛 un entero positivo. Se dice que 𝑎 es congruente a 𝑏 módulo 𝑛 y se escribe 𝑎≡𝑏 𝑚𝑜𝑑 𝑛 si y sólo si,  𝑛| (𝑎−𝑏).

Observación: La relación de congruencia módulo 𝑛 definida en ℤ es una relación de equivalencia.