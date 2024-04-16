# Lógica Proposicional y de Primer Orden
## Lógica y Proposiciones
> [!kanban] Lógica
> La lógica es la disciplina que trata los métodos del razonamiento, con el propósito de proporcionar reglas para determinar si un argumento es verdadero o falso.

> [!kanban] Proposición
> Una proposición es todo enunciado del cual tiene sentido que es verdadero o falso.

Las oraciones interrogativas, exclamativas, las órdenes y las expresiones de deseo o indeterminadas **no son proposiciones**.
Las proposiciones simples pueden combinarse por medio de operaciones lógicas y forman proposiciones compuestas.

> [!done] Negación, Conjunción, Disyunción, Implicación, Doble Implicación
> ![[imgs/Tablas de verdad.png]]
### Implicación
Si p y q son proposiciones, entonces p implica q
$$ 
p \to q
$$
- **Directa** $p \to q$
- **Recíproca** $q \to p$
- **Contraria** $-p \to -q$
- **Contrarecíproca** $-q \to -p$
### Doble Implicación
Si p y q son proposiciones, p si y solo si q
$$ p \leftrightarrow q$$

---

>[!attention] Prioridades de Conectivos Lógicos
Se usan para indicar el orden en que se realizan las operaciones lógicas
> 
> 0. Paréntesis
> 1. Negación
> 2. Conjunción
> 3. Disyunción
> 4. Implicación
> 5. Doble Implicación

> [!kanban] Tautología, contradicción y contenigencia
> ➢ Una proposición compuesta es una *tautología* si su valor de verdad es verdadero independientemente del valor de verdad de las proposiciones simples que la componen.
> ➢ Una proposición compuesta es una *contradicción* si su valor de verdad es falso independientemente del valor de verdad de las proposiciones simples que la componen.
> ➢ Una proposición compuesta es una *contingencia* si no es tautología ni contradicción.

## Relaciones Lógicas 
- Dos proposiciones son **lógicamente equivalentes** si la doble implicación entre ellas es una *tautología*. Si p es lógicamente equivalente a q, se anota $p\Leftrightarrow q$ o $p\equiv q$.
$$p\Leftrightarrow \text{q si y solo si }p\leftrightarrow q \text{ es una tautología}$$
- Una proposición p **implica lógicamente** una proposición q si la proposición $p → q$ es un *tautología*. Se anota $p\implies q$.
$$p\implies q \text{ si y solo si }p\to q \text{ es una tautología}$$
## Leyes Lógicas
Ciertas tautologías son muy útiles y originan las denominadas leyes lógicas. Algunas leyes lógicas son:
![[imgs/leyes logicas.png]]
## Razonamiento
Un **razonamiento** es una proposición compuesta con la siguiente forma:
$$P_{1}\wedge P_{2} \wedge \dots \wedge P_{n} \to Q \text{ con n entero positivo}$$
A las proposiciones $P_{1}, P_{2}, \dots, P_{n}$ se las llama *premisas* y a la preposición $Q$, *conclusión*.
Un razonamiento es válido si la conclusión $Q$ es verdadera cada vez que todas las premisas $P_{1}, P_{2}, \dots, P_{n}$ lo son.
### Reglas de Inferencia
Las reglas de Inferencia son formas de razonamiento válidas y garantizan que dado un conjunto de premisas (hipótesis) verdaderas la conclusión obtenida de ellas también lo es.
$$H_{1}\wedge H_{2} \wedge \dots \wedge H_{n} \to C \text{ es una tautología}$$
- *Modus Ponens* $(p\to q) \wedge p \implies q$
- *Silogismo Hipotético* $(p\to q) \wedge (q\to r) \implies (p\to r)$
## Proposiciones Generales
Sea $P(x)$ una expresión que incluye a la variable $x$ y sea $U$ un conjunto. $P$ se llama **Función Proposicional o Predicado** (respecto de $U$) si para cada $x$ en $U$, $P(x)$ es una proposición. El conjunto $U$ recibe el nombre de **Universo de Discurso**.
Podemos obtener una proposición:
1. Reemplazando la variable x por un elemento de U
2. Cuantificando universal y existencialmente el predicado
En símbolos:
- $\forall x:P(x)$, Cuantificador Universal
- $\exists x:P(x)$, Cuantificador Existencial
>[!warning] Una PROPOSICIÓN GENERAL es un predicado cuantificado en un universo de discurso
### Negación de proposiciones generales
La negación de una proposición general es también una proposición general:
- $\neg(\forall x:P(x)) \Leftrightarrow \exists: \neg P(x)$
- $\neg(\exists x:P(x)) \Leftrightarrow \forall: \neg P(x)$
### Cuantificadores Anidados
En las proposiciones generales pueden aparecer más de una variable, en tal caso debe tenerse en cuenta que todas las variables estén cuantificadas y bajo el alcance de un cuantificador como así también es importante considerar el orden en que aparecen los *cuantificadores anidados*.