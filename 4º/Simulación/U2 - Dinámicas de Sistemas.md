# Dinámicas de Sistemas
## Introducción
> [!summary] Dinámica de Sistemas
> La **DINÁMICA DE SISTEMAS** se basa en la teoría de sistemas y utiliza conceptos de *retroalimentación* y *causalidad* para entender cómo interactúan las variables de un sistema y cómo estas interacciones afectan su comportamiento global.

Ofrece un enfoque estructurado y poderoso para modelar, analizar y comprender sistemas complejos en diversas áreas, desde la ingeniería hasta la gestión empresarial. <mark style="background: #BBFABBA6;">Cuando se aplica a la simulación de sistemas, la dinámica de sistemas proporciona herramientas y técnicas para desarrollar modelos computacionales que representan el comportamiento dinámico de sistemas complejos a lo largo del tiempo</mark>.
## Definición de Sistemas Continuos
Los sistemas continuos son sistemas cuyas variables evolucionan de forma continua en el tiempo. Incluye sistemas físicos (mecánicos, eléctricos, hidráulicos), procesos químicos, dinámica de poblaciones, modelos económicos, etc.
Una variable es continua si está definida para todo tiempo $t$.
Se describen mediante ecuaciones diferenciales ordinales. Se escriben como **ecuaciones de estado**:
$$
\begin{align}
\begin{cases}
x_{1}' & =f_{1}(x_{1},x_{2},\dots x_{n-1},x_{n}t) \\
x_{2}' & =f_{2}(x_{1},x_{2},\dots x_{n-1},x_{n}t) \\
\vdots  & \vdots \\
x_{n-1}' & =f_{n-1}(x_{1},x_{2},\dots x_{n-1},x_{n}t) \\
x_{n}' & =f_{n}(x_{1},x_{2},\dots x_{n-1},x_{n}t)
\end{cases} \\
x_{1},x_{2},\dots, x_{n-1}, x_{n}: \text{ variables de estado}
\end{align}
$$
Estos sistemas pueden en general modelarse mediante **Ecuaciones Diferenciales**. Utilizaremos $x'$ para referirnos a la derivada temporal $\frac{dx}{dt}$.
## Solución analítica de sistemas continuos
En la solución analítica destacan el método **autovalores** y **transformada de Laplace**.
- En el método de **autovalores** se diagonaliza la matriz de coeficientes para encontrar los valores propios y los vectores propios asociados, lo que permite escribir la solución general de las ecuaciones diferenciales en términos de estas variables.
	Sea $\lambda$ un valor propio (o autovalor) de la matriz $A$ del sistema lineal de primer orden si y solo si $(A-\lambda I).v=0$, si $v$ es un vector propio asociado con $\lambda$ y $v\neq 0 \implies |A-\lambda I|=0$.
	Para cada autovalor, se sustituye el mismo en $|A-\lambda I|$ para el vector propio asociado a 
	$$
	v = \begin{bmatrix}
	a \\
	b \\
	c \\
	\end{bmatrix}
	$$
	La solución general es 
$$x(t)=c_{1}v_{1}ve^{\lambda_{1}}+c_{2}v_{2}ve^{\lambda_{2}}+\dots+c_{n}v_{n}ve^{\lambda_{n}}$$
- La **transformada de Laplace** herramienta para resolver EDL con condiciones inciales, convirtiendo el problema en la resolución de una ecuación algebraica
	Para un sistema lineal continuo de la forma $x'(t)=Ax(t)$, donde $x(t)$ es el vector de estado, formando variables de estado y A es la matriz dinámica de sistema, de orden $nxn$, se aplica T de Laplace, para encontrar la solución del sistema.
	Se aplica TL en cada miembro de la ecuación:
	 $$
	sx(s)-x(0)=Ax(s)
	$$
	Se agrupa por factor común $x(s)$: $x(s)(sI-A)=x(0)$
	Se anti transforma y se despeja para indicar la solución $x(t)$: $x(t)=L^{-1}[(sI-A)^{-1}x(0)]$
## Definición de dinámica de sistemas
La dinámica de sistemas se refiere al estudio de la estructura de sistemas complejos y cómo cambian a lo largo del tiempo.
> [!todo] Definición
> La dinámica de sistemas implica el análisis detallado de las **relaciones** e **influencias** entre las variables dentro de un sistema, así como el estudio de su **comportamiento** o dinámica en conjunto.
> La dinámica de sistemas alude a un método para el estudio del comportamiento de sistemas mediante la construcción de un modelo de simulación informático que ponga de manifiesto las relaciones entra la **estructura** del sistema y su **comportamiento**.

Para su estudio se realizan los siguientes pasos:
1. Se observan los modos de comportamiento del sistema real para tratar de identificar los elementos fundamentales del mismo. 
2. Se buscan las estructuras de realimentación que puedan producir el comportamiento observado. 
3. A partir de la estructura identificada se construye el modelo matemático del comportamiento del sistema.
4. El Modelo se emplea para simular como un laboratorio.
5. La estructura se modifica hasta que sus componentes y el comportamiento resultante coincidan con el comportamiento observado.
6. Se modifican las decisiones que puedan ser introducidas en el modelo de simulación hasta encontrar decisiones aceptables.

Este enfoque, comparado con otros, es el **análisis de los efectos de los bucles o ciclos de retroalimentación**.
> [!attention] Dinámica de Sistemas
> Se destacan dos herramientas:
> - Diagrama Causal o de Influencias
> - Diagrama de Forreseter o Simulación
## Diagrama Causal o de Influencia
> [!todo] Definición
> El **DIAGRAMA CAUSAL** o **INFLUENCIA** representa las relaciones de influencia que se dan entre los elementos de un sistema y por lo tanto permite conocer la **estructura** del mismo.
> Permite visualizar cómo diferentes variables influencian unas a otras dentro del sistema, destacando las relaciones de causalidad entre ellas.

En el DIAGRAMA CAUSAL o INFLUENCIA se indican los elementos más importantes que intervienen en el proceso. Estos elementos básicos del proceso están unidos entre sí mediante flechas que indican las influencias que se establecen entre ellos. La influencia, en esta descripción, se mantiene a un nivel cualitativo, en el sentido de que únicamente se dice si se produce o no influencia, pero no la forma o **magnitud** que tenga.
Si A y B son dos partes de un sistema, el hecho de que A influya sobre B se representa mediante una flecha de la forma $A → B$ e indica que B es una función de A, es decir $B = f(A)$. Se representa mediante un **grafo orientado**, a las flechas se les asocia un signo que indica si las variaciones del antecedente y consecuente son, o no, del mismo signo.
$$
\begin{align}
A  & \to ^{+}B \text{ Signo positivo: las variaciones de A y B son del mismo sentido}\\
A  & \to ^{-}B \text{ Signo negativo: las variaciones de A y B son de sentido contrario}
\end{align}
$$
### Clasificación según estructura
- **Diagramas abiertos, de estructura simple**
	Representaciones gráfica en las cuales no se forman lazos cerrados o retroalimentaciones entre los elementos del sistema. El sistema tiene <mark style="background: #BBFABBA6;">comportamientos lineales</mark>.
	![[img/diagrama causal abierto.png| center ]]
- **Diagramas cerrados, de estructura compleja o bucles de realimentación**
	Contienen bucles de retroalimentación donde una variable afecta a otra, que a su vez retroalimenta a la primera, creando un ciclo de interacciones. El sistema puede exhibir <mark style="background: #BBFABBA6;">comportamientos no lineales, como oscilaciones, amplificación o amortiguamiento</mark>, dependiendo de la configuración de los lazos de realimentación (afectan a la estabilidad del sistema).
	![[img/diagrama causal cerrado.png| center]]
### Bucles de realimentación
> [!abstract] Bucles de realimentación
> - Un ciclo es **positivo** ($+$ entre paréntesis) si todas las relaciones tienen signo $+$ o existe un número par de relaciones $-$.
> - Un ciclo es **negativo** ($-$ entre paréntesis) si existe un número impar de relaciones $-$.

Si existen diversos bucles combinados, es imposible predecir a partir solamente de argumentos cualitativos el comportamiento del sistema.
- **Bucles de realimentación positivo**
	El comportamiento que resulta de un bucle de esta naturaleza consiste en acelerar o bien el crecimiento, o el declive; hacen inestable el sistema.
	![[img/bucles positivos.png| center]]
- **Bucles de realimentación negativo**
	El comportamiento que resulta de un bucle de esta naturaleza contribuye a la estabilidad del sistema al contrarrestar los cambios que podrían llevarlo fuera de equilibrio.
	![[img/bucle negativo.png| center | 250]]
- **Bucles de realimentación combinados**
	Los bucles combinados pueden amplificar o atenuar la salida de un sistema, dependiendo de cómo se combinan los efectos de la realimentación positiva y negativa. Estos bucles permiten que el sistema se adapte a cambios externos al mismo tiempo que mantiene su estabilidad interna mediante la retroalimentación negativa y la capacidad de amplificación mediante la retroalimentación positiva.
	![[img/bucles combinados.png| center | 250]]
### Interpretación de influencias
El sentido de la flecha y el signo asociado (+ o -) revelan la dirección y la naturaleza de la influencia. Un **signo positivo (+)** indica una relación de aumento, donde un aumento en la variable de origen conlleva un aumento en la variable de destino. Por el contrario, un **signo negativo (-)** señala una relación de disminución, donde un aumento en la variable de origen resulta en una disminución en la variable de destino.
$$
\begin{align}
A  & \to ^{+}B \text{ Se lee: a mas A mas B}\\
C  & \to ^{-}D \text{ Se lee: a mas C menos D}
\end{align}
$$
### Consideraciones importantes
Reglas a tener en cuenta:
- Evitar bucles ficticios (no válidos).
- Emplear elementos caracterizables por números (no abstracciones). No emplear dos veces la misma relación.
- Evitar bucles redundantes.
- No emplear el tiempo como factor causal.
- Los elementos deben ser variables cuyo valor puede variar con el tiempo. 
- Evitar el uso de verbos en los elementos. Por ejemplo, Presas es correcto. Aumento de presas es incorrecto.
- Especificar claramente el signo de la variable en su nombre.
- El nombre debe especificar un signo. 
- Temperatura es mejor que FRIO.
- Si la cadena entre dos elementos consecutivos es muy compleja y requiere explicaciones orales o escritas detalladas, es necesario incluirlas de forma explícita en el diagrama.
- Limitar el diagrama causal a la estructura más simple posible
## Diagrama de Forrester o de Simulación

> [!info] Diagrama de Forrester
> Es una representación simbólica de las **variables de nivel, variables de flujo y variables auxiliares** de un diagrama causal o influencias. Constituye un paso intermedio entre el diagrama Causal y el sistema de ecuaciones diferenciales que le corresponde.

### Símbolos utilizados en la construcción del diagrama
Entre los distintos elementos que aparecen en los nodos de un diagrama de influencias, algunos tienen variaciones con respecto al tiempo de otras magnitudes. Podemos expresarlas:
$$
\frac{dX}{dt} \to ^{+}x
$$
$\frac{dX}{dt}$ denota la variación con respecto al tiempo de $X$. Se establece una relación de influencia, causa efecto.
> [!hint]
> - La variable $X$ se denomina **variable de nivel** o **variables de estado**
> - La variable $\frac{dX}{dt}$ se denomina **variable de flujo**

#### Variable de Nivel
Se denomina bloque integrador y corresponde a las variables principales. Cada bloque es una ecuación diferencial.
![[img/variable de nivel.png]]
Son aquellas variables cuya evolución es significativa para el estudio del sistema y son equivalentes a las variables de estado de un sistema en descripción interna. Una característica común a las variables de nivel es que <mark style="background: #BBFABBA6;">cambian lentamente en respuesta a las variaciones de otras variables</mark>, en concreto de las variables de flujo.
**Una variable de nivel no puede influir directamente en otra variable de nivel, sino es a través de un flujo.**
Características:
- Acumulador
- Tangible e intangible
- Cambio relativamente lento
- Unidades sin tiempo
- Se puede contar en cualquier momento

#### Variable de Flujo
Es aquella variable que determina las variaciones en las variables de nivel del sistema y caracterizan las acciones que se toman en el sistema las cuales quedan acumuladas en los niveles correspondientes.
![[img/variables de flujo.png]]
A todo nivel se le asocia al menos una variable de flujo. Físicamente expresan como se convierte la información disponible del sistema en una acción.
$$
unidadesDeFlujo=\frac{unidadDeNivel}{tiempo}
$$
Características:
- Regula las entradas y salidas de los niveles
- Siempre unidades/tiempo
- Flujos tangibles e intangibles
- Flujo = única forma de cambiar los niveles

#### Variable Auxiliar
Es aquella variable que representa pasos en los que se descompone el cálculo de una variable de flujo a partir de los valores tomados por los niveles. El propósito del uso de las variables auxiliares está en facilitar la comprensión y definición de las variables de flujo ya que las variables auxiliares suelen representar en sí mismas conceptos individuales.
Características: 
- Convertidores de información
- Parte de una “red de decisión”
- Cálculos auxiliares

#### Fuente
Un nivel puede alimentarse, a través de un flujo desde otro nivel o bien desde una fuente exterior al sistema. Esta fuente se supone de capacidad infinita y se representa mediante una nube.
![[img/fuente.png]]

#### Sumidero
Un nivel puede vaciarse, a través de un flujo sobre otro nivel o sobre un sumidero exterior al sistema. De la misma forma, el sumidero se supone de capacidad infinita y se representa mediante una nube.
![[img/sumidero.png]]

#### Conector
Muestra los flujos de información. Alimenta las variables auxiliares y los flujos con información. Representan las relaciones entre los elementos.
![[img/conector.png]]

---
Los niveles acumulan flujos materiales que llegarán mediante **canales de material** y las variables de flujo y auxiliares se alimentan a partir de **canales de información**.
![[img/asociacion de diagramas.png]]
