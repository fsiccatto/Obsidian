# Grafos y Árboles
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
> Sea M la matriz de incidencia
> $$d(v_{i}) = \sum_{j=1}^km_{ij} \to d(v_{i})=m_{12} + m_{13} + \dots + m_{1k}$$
> $$\sum_{i=j}^nd(v_{i})=\sum_{i=1}^n(\sum_{j=1}^km_{ij})=\sum_{j=1}^k(\sum_{i=1}^nm_{ij})=\sum_{j=1}^k2=2k=2|E(G)|$$
$$$$

> [!important] Corolario
>  En cualquier grafo el número de vértices de grado impar es par.

### Grafos Destacados
> [!note] Definición
>  Sea $n$ un entero positivo. Un **grafo completo de $n$ vértices**, que se denota por $K_{n}$, es un grafo con 𝑛 vértices y exactamente una arista conectando a cada par de vértices distintos.
>  Un grafo 𝐺 es **𝑘-regular** si $𝑑(v)= 𝑘$ para todo 𝑣 ∈ 𝑉(𝐺); un grafo 𝐺 es **regular**, si es 𝑘-regular para algún 𝑘.