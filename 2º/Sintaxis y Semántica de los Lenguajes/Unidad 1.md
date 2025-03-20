## Jerarquía de Chomsky
![[imgs/jerarquia de chomsky.png| center]]
### Gramáticas de Tipo 0
También llamadas **gramáticas no restringidas**. Las reglas de derivación son de la forma:
$$\alpha \to \beta $$
siendo $\alpha \in (V_{N} \cup V_{T}){^+}$ y $\beta \in (V_{N} \cup V_{T}){^*}$, es decir la única restricción es que no puede haber reglas de la forma $\lambda \to \beta$ donde $\lambda$ es la cadena vacía. En la parte izquierda de cada producción, tiene que haber al menos un ***símbolo no Terminal***.
> [!example] Ejemplo
> $$\begin{align*}
> S &\to 0A \\
> 0A &\to B1 \\
> B &\to \lambda
> \end{align*}$$

### Gramática de Tipo 1
También llamadas **gramáticas sensibles al contexto**. En ellas las reglas de producción son de la forma:
$$\alpha S \beta \to \alpha \gamma \beta $$
siendo$S \in V_{N}$, $\alpha, \beta \in (V_{N} \cup V_{T}){^*}$ y $\gamma \in (V_{N} \cup V_{T}){^+}$.
Estas gramáticas se llaman sensibles al contexto, pues se puede reemplazar $S$ por $\gamma$ siempre que estén en el contexto $\alpha \dots \beta$.

La parte izquierda debe tener un símbolo no terminal, que puede estar acompañado por un contexto de símbolos terminales y no terminales. Si este contexto aparece, debe estar presente también en la parte derecha. Sólo se admite como regla compresora la regla $S \to \lambda$ (parte derecha tiene menos símbolos que la parte izquierda).
> [!important] Importante
> Si se admite otra regla compresora (por ej.: la regla nula) que no sea el axioma se dice que la gramática no es estricta.

Otra forma de definir las gramáticas sensibles al contexto, es aquella gramática formal con la única restricción que todas las producciones α -> β en P cumplan que |α| ≤ |β| donde |α| es la longitud de α. Se las llama ***gramáticas de longitud no decreciente***.
> [!example] Ejemplo
> $$\begin{align*}
> S &\to abc | aSBc \\
> cB &\to Bc \\
> bB &\to bb
> \end{align*}$$
> Genera el lenguaje: $\{ a{^n}b{^n}c{^n} : n \geq 1 \}$ que es dependiente del contexto
### Gramáticas de Tipo 2
Las gramáticas de tipo 2 también se denominan **gramáticas libres de contexto**. Sus reglas de producción tan sólo admiten tener un símbolo no terminal en su parte izquierda, es decir:
$$S \to \alpha$$
Siendo $S \in V_{N}$ y $\alpha \in (V_{N} \cup V_{T}){^+}$.
Se llama de contexto libre porque se puede cambiar $S$ por $\alpha$, independientemente del contexto que aparezca $S$. Es decir, a la hora de transformar una palabra en otra, el símbolo no terminal que se transforma no depende de los que estén a la izquierda o derecha de él.
Se dice que una G2 es ***Estricta***, si cumple estrictamente con la restricción de que la única regla compresora sea el axioma $S\to \lambda$. Si no cumple esta condición, se dice que la G2 es ***No Estricta***.
> [!example] Ejemplo
> $$\begin{align*}
> S &\to aSc | B \\
> B &\to bBc | \varepsilon  \\
> \end{align*}$$
> Genera el lenguaje: $\{ a{^n}b{^m}c{^{m+n}} : n \geq 0, m \geq 0 \}$.
### Gramáticas de Tipo 3
Las gramáticas del tipo 3 también denominadas regulares, lineales o normales comienzan sus reglas de producción por un símbolo terminal, que puede ser seguido o no por un símbolo no terminal, es decir son de la forma:
$$\begin{align*}
 S &\to \alpha B \\
 S &\to \alpha \\
 \end{align*}$$
 donde $S, A \in V_{N}$ y $\alpha \in V_{T}$.
 - Regulares por derecha: \<No Terminal> := \<Terminal>|\<Terminal>\<No Terminal>|$\lambda$
 - Regulares por izquierda: \<No Terminal> := \<Terminal>|\<No Terminal>\<Terminal>|$\lambda$
 > [!example] Ejemplo
> ![[imgs/ejemplo g3.png | center | 300]]

#### Recursividad por izquierda