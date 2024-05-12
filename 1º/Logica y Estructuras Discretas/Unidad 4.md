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
## Relación de Orden
> [!info] Definición
> Sea 𝑅 una relación definida sobre un conjunto 𝐴. 𝑅 es una **relación de orden parcial** si y sólo si, 𝑅 es reflexiva, antisimétrica y transitiva. El conjunto 𝐴 se dirá parcialmente ordenado respecto a 𝑅.
> Si 𝑅 es una relación de orden parcial sobre un conjunto 𝐴 tal que, para todo $𝑎,𝑏 \in 𝐴, 𝑎𝑅𝑏 ∨ 𝑏𝑅𝑎$, entonces 𝑅 es una **relación de orden total** sobre 𝐴. El conjunto 𝐴 se dirá totalmente ordenado respecto a 𝑅.

## Diagrama de Hasse
> [!info] Definición
> Sea 𝐴 un conjunto finito y sea ⪯ un orden parcial en 𝑅. Se dice que el elemento 𝑎 cubre al elemento 𝑏 si 𝑏 ⪯ 𝑎 y no existe 𝑥 ∈ 𝐴 tal que 𝑏⪯𝑥⪯𝑎.

Podemos representar geométricamente a (𝐴, ⪯), asignando a cada elemento de 𝐴 un punto en el plano, de modo que si 𝑎 cubre a 𝑏 entonces el punto que representa a 𝑎 está arriba del punto que representa a 𝑏.
En este caso dibujamos también una línea uniendo esos puntos. Tal represntación es el **Diagrama de Hasse**.
![[Diagrama de Hasse ejemplo.png]]
## Cadenas
Sea 𝐴 un conjunto finito con al menos un elemento. Una **cadena sobre** 𝐴 es una sucesión finita de elementos de 𝐴 . Los elementos de 𝐴 se llaman caracteres de la cadena y la longitud de una cadena es el número de caracteres que contiene.
La **cadena nula sobre 𝐴** se define como la “cadena” sin caracteres. Por lo general se denota con 𝝐 y se dice que tiene una longitud 0.
# Orden Lexicográfico
Engeneral, si A es cualquier conjunto con una relación de orden parcial, entonces un *diccionario* u **orden lexicográfico** se puede definir sobre un conjunto de cadenas sobre 𝐴.
> [!teorema] Teorema
> Sea 𝐴 un conjunto con una relación de orden parcial 𝑅 y sea 𝑆un conjunto de cadenas sobre 𝐴. Se define una relación $\leq$ sobre 𝑆 como sigue:
> Para cualesquiera dos cadenas en 𝑆, $𝑎_{1}𝑎_{2}…𝑎_{m} \text{ y }𝑏_{1}𝑏_{2} …𝑏_{n}$ donde 𝑚 y 𝑛 son enteros positivos,
> 1. Si $𝑚\leq𝑛$ y $𝑎_{i} =𝑏_{i}$ para toda 𝑖=1...𝑚, entonces $𝑎_{1}𝑎_{2}…𝑎_{m} \leq 𝑏_{1}𝑏_{2} …𝑏_{n}$. 
> 2. Si para algún enero 𝑘 con 𝑘 ≤ 𝑚, 𝑘 ≤𝑛 y 𝑘 ≥1, $𝑎_{i} =𝑏_{i}$ para toda 𝑖 =1…𝑘−1 y $𝑎_{k} \neq b_{k}$ pero $a_{k}Rb_{k}$ entonces $𝑎_{1}𝑎_{2}…𝑎_{m} \leq 𝑏_{1}𝑏_{2} …𝑏_{n}$. 
> 3. Si 𝜖 es la cadena nula y 𝑠 cualquier cadena, entonces 𝜖 ≼ 𝑠.
> Si ninguna cadena está relacionada con otras por estas tres condiciones, entonces $\leq$ es un orden parcial.

> A esta relación de orden parcial se le llama el **orden lexicográfico para S** que corresponde al orden parcial 𝑅 sobre 𝐴.

