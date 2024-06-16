[](matriz%20de%20adyacencia.png)[](matriz%20de%20incidencia.png)# Grafos y Árboles
## Grafos
> [!info] Definición
>  Un grafo 𝐺 es una pareja ordenada $𝐺 = (𝑉 (𝐺) , 𝐸 (𝐺))$ , donde $𝑉 (G)$ es un conjunto finito no vacío cuyos elementos son llamados **vértices** y $𝐸 (G)$ es un conjunto cuyos elementos son subconjuntos de cardinalidad dos de $𝑉 (𝐺)$ , llamados **aristas**.

- Si 𝑒 = {𝑢, 𝑣} es una arista, entonces se dice que 𝑒 une a 𝑢 con 𝑣, también se dice que 𝑢 y 𝑣 son los **extremos** de 𝑒.
- Dos vértices son **adyacentes** si existe una arista que los une, se suele denotar una arista {𝑢, 𝑣} como 𝑢𝑣 o 𝑣𝑢.  Se dice que una arista **incide sobre** cada uno de sus puntos extremos. Un vértice en el que no incide arista alguna se llama **aislado**.
- El número de vértices de un grafo 𝐺 es llamado el **orden** de 𝐺 y el número de aristas de 𝐺 es llamado **tamaño** de 𝐺. Un grafo de orden 1 es llamado *trivial*.
- El número de aristas que inciden en un vértice 𝑣 se denomina **grado** del vértice 𝑣, y se denota 𝑑𝐺(𝑣) o simplemente 𝑑(𝑣).
### Matrices de un Grafo
> [!info] Definición
>  Sea 𝐺 un grafo con un conjunto de vértices $V=\{ v_{1}, \dots, v_{n} \}$ y un conjunto de aristas $𝐸 = \{ e_{1}, \dots, e_{m} \}$. La **matriz de incidencia** de 𝐺 es la matriz $𝑀 = (m_{ik})$ de tamaño 𝑛 × 𝑚, donde:
>  $$m_{ik} = 1 \text{ si } e_{k} \text{ incide en } v_{i},  m_{ik} = 0 \text{ en otro caso}$$

> [!info] Definición
>  Sea 𝐺 un grafo con conjunto de vértices $V=\{ v_{1}, \dots, v_{n} \}. La **matriz de adyacencia** de 𝐺 es la matriz $A=(a_{ij})$ de tamaño 𝑛 × 𝑛, donde:
>  $$a_{jk} = 1 \text{ si } v_{i} \text{ es adyacente a } v_{j},  m_{ik} = 0 \text{ en otro caso}$$
###### Propiedad
Si $G=(V(G), E(G))$ es un grafo, entonces
$$\sum_{v_{i} \in V(G)}d(v_{i}) =2|E(G)|$$
> [!caution] Demostración
> Sea M la matriz de incidencia, cada vértice $i$ tenemos que
> $$d(v_{i}) = \sum_{k=1}^mm_{ik}$$
>$$\sum_{i=1}^nd(v_{i})=\sum_{i=1}^n(\sum_{k=1}^mm_{ik})\sum_{k=1}^m(\sum_{i=1}^nm_{ik})$$
> Como cada arista $e_{k}$ incide en exactamente dos vértices (cada columna de $M$ tiende dos unos).
> $$\sum_{k=1}^m2=2m=2|E(G)|$$

> [!important] Corolario
> En cualquier grafo el número de vértices de grado impar es par.

> [!caution] Demostración
> Sean V1 y V2 los subconjuntos de vértices de grado impar y grado par, respectivamente. Entonces
> $$\sum_{v \in V_{1}}d(v)+\sum_{v \in V_{2}}d(v) = \sum_{v \in V}d(v)$$
> es par, por teorema anterior. Como tambien $\sum_{v \in V_{2}}d(v)$ es par, se sigue que $\sum_{v \in V_{1}}d(v)$ es par, y por lo tanto $|V_{1}|$ es par.
### Grafos Destacados
> [!note] Definición
>  Sea $n$ un entero positivo. Un **grafo completo de 𝑛 vértices**, que se denota por $K_{n}$, es un grafo con 𝑛 vértices y exactamente una arista conectando a cada par de vértices distintos.

> [!note] Definición
>  Un grafo 𝐺 es **𝑘-regular** si $𝑑(v)= 𝑘$ para todo 𝑣 ∈ 𝑉(𝐺); un grafo 𝐺 es **regular**, si es 𝑘-regular para algún 𝑘.

> [!note] Definición
>  Se dice que un grafo es **bipartito** si su conjunto de vértices puede ser partido en dos subconjuntos disjuntos 𝑋 y 𝑌, (no vacíos), tales que cualquier arista tiene un extremo en 𝑋 y un extremo en 𝑌; tal partición (𝑋, 𝑌) es llamada una **bipartición** del grafo.

> [!teorema] Teorema
> Un grafo es bipartito si y solo si no contiene ciclos de longitud impar.

> [!note] Definición
>  Sean 𝑚 y 𝑛 enteros positivos. Un **grafo completo bipartito de vértices (𝑚, 𝑛)**, que se denota por $K_{m,n}$, , es un grafo bipartito tal que $𝑋 = v_{1}, v_{2}, \dots , 𝑣_{m}$ , $𝑌 = w_{1}, w_{2}, \dots , w_{n}$ , y existe una arista de cada vértice $v_{i}$ a cada vértice $w_{j}$.
#### Subgrafo
> [!info] Definición
>  Se dice que un grafo 𝐻 es un **subgrafo** de un grafo 𝐺 si y sólo si, cada vértice en 𝐻 es también un vértice en 𝐺, cada arista en 𝐻 es también una arista en 𝐺 y cada arista en 𝐻 tiene los mismos vértices extremos de 𝐺.

- Si además 𝐻 ≠ 𝐺, entonces se dice que 𝐻 es un **subgrafo propio** de 𝐺.
- Un **subgrafo de recubrimiento** es un subgrafo 𝐻 de 𝐺 tal que 𝑉(𝐻) = 𝑉(𝐺).
- Sea 𝐺 un grafo y sea 𝑉′ un subconjunto no vacío de 𝑉. Sea 𝐸′ el subconjunto de aristas de 𝐺 que tienen ambos extremos en 𝑉′ . El grafo (𝑉′ , 𝐸′) es llamado el **subgrafo inducido** por 𝑉′ , y se denota 𝐺\[𝑉′].
- Un subgrafo 𝐻 de 𝐺 es **maximal** con respecto a una propiedad, si 𝐻 cumple la propiedad, y 𝐻 no es subgrafo propio de otro grafo que cumpla la propiedad. Análogamente, 𝐻 es **minimal** con respecto a una propiedad si 𝐻 cumple la propiedad y no existe un subgrafo propio de 𝐻 que cumpla la propiedad.
#### Caminos de un Grafo
> [!info] Definición
> Un camino en un grafo 𝐺 es una sucesión finita no vacía
>  $$W=\{ v_{1}, e_{1}, v_{2}, e_{2}, \dots, v_{k-1}, e_{k-1}, v_{k} \}$$
>  cuyos términos son alternadamente vértices y aristas, tales que los extremos de $e_{j}$ son $v_{j}$ y $v_{j+1}$. Decimos que 𝑊 es un camino de $v_{1}$ a $v_{k}$, o un $(v_{1}, v_{k}) \text{-camino}$. Los vértices $v_{1}$ y $v_{k}$ son el **origen** y el **destino** del camino, respectivamente, y $v_{2}, v_{3},…, v_{k-1}$ son los **vértices internos**. El entero 𝑘 − 1 es la **longitud** del camino. Un **camino trivial** es un camino de longitud cero. Un **camino cerrado** es un camino que comienza y termina en el mismo vértice.

- Un **paseo** es un camino donde todas las aristas son distintas.
- Una **trayectoria** es un paseo donde todos los vértices son distintos.
- Un **ciclo** es un paseo cerrado no trivial cuyo origen y vértices internos son distintos.
- Un grafo 𝐺 se dice que es **acíclico** si no contiene ciclos.
### Grafo Conexo
> [!info] Definción
>  Un grafo 𝐺 es **conexo**, si para cualesquiera dos vértices 𝑢 y 𝑣 de 𝐺 existe una (𝑢, 𝑣)−𝑡𝑟𝑎𝑦𝑒𝑐𝑡𝑜𝑟𝑖𝑎 en 𝐺.
>  Una **componente conexa** de un grafo 𝐺 es un subgrafo conexo maximal. De modo que un grafo es conexo si tiene exactamente una componente. Un grafo con más de una componente es **disconexo**.
### Grafo Isoformo
> [!info] Definción
>  Un grafo 𝐺 es **isomorfo** a un grafo 𝐻, si existe una función biyectiva 𝜑: 𝑉(𝐺) → 𝑉(𝐻) tal que, cualesquiera sean los vértices 𝑢 y 𝑣 en 𝐺:
>  $$\{ u,v \} \in E(G) \iff \{ 𝜑(u), 𝜑(v) \} \in E(H)$$
>  La función 𝜑 es un **isomorfismo** de 𝐺 en 𝐻. Si 𝐺 es isomorfo a 𝐻, escribiremos 𝐺 ≅ 𝐻.

Es decir que dos grafos pueden tener la misma estructura, difieriendo solo de los nombres de los vértices.
### Multigrafo
> [!info] Definción
>  Un **multigrafo** 𝐺 consiste de dos conjuntos finitos: un conjunto no vacío 𝑉(𝐺) de vértices y un conjunto de aristas 𝐸(𝐺) , donde cada arista está asociada a un conjunto compuesto por uno o dos vértices. Una arista con un solo punto extremo se llama un **bucle** o lazo y dos o más aristas distintas con el mismo conjunto de puntos extremos se dicen que son **paralelas**.
## Paseos Eulerianos
Un **paseo euleriano** es un paseo que recorre todas las aristas de un grafo 𝐺. **Un circuito euleriano** es un paseo euleriano cerrado. Un grafo es euleriano si contiene un circuito euleriano.
> [!teorema] Teorema
> Un grafo conexo es euleriano si y sólo si no contiene vértices de grado impar.
## Ciclo Hamiltoniano
Una trayectoria que pasa por cada vértice de un grafo exactamente una vez es llamada una **trayectoria hamiltoniana**. Un **ciclo hamiltoniano** es un ciclo que contiene todos los vértices del grafo. Un grafo es hamiltoniano si contiene un ciclo hamiltoniano.
Propiedad: Todo grafo completo con al menos tres vértices es hamiltoniano.
## Árboles
Un árbol es un grafo acíclico y conexo.
> [!teorema] Teorema
> - Si T es un árbol, entonces para cualesquiera dos vértices 𝑢 y 𝑣 existe una única (𝑢, 𝑣)-trayectoria.
> - Si T es un árbol no trivial, entonces existen al menos dos vértices distintos de grado uno.
> - Si T es un árbol con 𝑛 vértices, entonces el número de aristas es igual a 𝑛 − 1.

Un **árbol con raíz** es un árbol T que tiene un vértice particular $r$ designado como raíz.
### Árboles con raíz
Si T es árbol con raíz y $(v_{1}, v_{2}, … , v_{k})$ es una trayectoria con origen $r=v_{1}$, entonces para toda i = 1, 2, … , k−1 se dice que: 
- $v_{i}$ es el padre de $v_{i+1}$; 
- $v_{i+1}$ es hijo de $v_{i}$; 
- $v_{1}, v_{2}, … , v_{k}$ son los ancestros de $v_{i+1}$; 
- $v_{i+1}, v_{i+2}, … , v_{k}$ son los descendientes de $v_{i}$.
- El subgrafo de $T$, que consiste en $w$ y todos sus descendientes, con $w$ como raíz, es llamado el **subárbol de $T$ con raíz $w$**. 
- Un **árbol binario** es un árbol con raíz en el que cada vértice tiene a lo más dos hijos (uno a la izquierda y otro a la derecha). Un árbol **binario completo o lleno** es un árbol binario en el que todos los vértices internos tienen dos hijos.
### Recorriendo un árbol
Un **recorrido** en un árbol binario $T$ con raíz $r$ es un procedimiento para visitar todos los vértices de $T$. Los recorridos más comunes son el recorrido con orden inicial o preorden, y el recorrido con orden final o postorden. Las siguientes son las definiciones recursivas de esos recorridos.

| Recorrido preorden                                                                                                             | Recorrido postorden                                                                                                              |
| :----------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- |
| 1. Procesar el vértice raíz.<br>2. Recorrer el subárbol izquierdo en preorden.<br>3. Recorrer el subárbol derecho en preorden. | 1. Recorrer el subárbol izquierdo en postorden.<br>2. Recorrer el subárbol derecho en postorden.<br>3. Procesar el vértice raíz. |
| Notación Polaca                                                                                                                | Notación Polaca Inversa                                                                                                          |
## Digrafo
> [!info] Definción
>  Un **grafo dirigido** $D$ o **dígrafo** es una pareja ordenada $D = (V(D), A(D))$, donde V(D) es un conjunto finito no vacío cuyos elementos son llamados vértices y A(D) es un subconjunto de parejas ordenadas de vértices distintos, cuyos elementos son llamados arcos. Si $a = (u, v) ∈ A(D)$, se dice que $u$ es el extremo inicial y $v$ es el extremo terminal de $a$.
### Matrices de un Digrafo
> [!info] Definción
>  Sea $D$ un dígrafo con conjunto de vértices $V = {v_{1},…,v_{n}}y$ conjunto de arcos $E= {e_{1}, …,e_{m}}$ ,
>  La matriz de incidencia de $D$ es la matriz donde:
>  ![[matriz de incidencia.png]]
>  La matriz de adyacencia de D es la matriz $A=(a_{ij})$ de tamaño $nxn$ donde:
>  ![[matriz de adyacencia.png]]

