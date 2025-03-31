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
	Para cada autovalor, se sustituye el mismo en $|A-\lambda I|$ para el vector propio asociado a $$
v = \begin{bmatrix}
a \\
b \\
c \\
\end{bmatrix}
$$
	La solucipon general es $$x(t)=c_{1}v_{1}ve^{\lambda_{1}}+c_{2}v_{2}ve^{\lambda_{2}}+\dots+c_{n}v_{n}ve^{\lambda_{n}}$$
- La **transformada de Laplace** herramienta para resolver EDL con condiciones inciales, convirtiendo el problema en la resolución de una ecuación algebraica
	Para un sistema lineal continuo de la forma $x'(t)=Ax(t)$, donde $x(t)$ es el vector de estado, formando variables de estado y A es la matriz dinámica de sistema, de orden $nxn$, se aplica T de Laplace, para encontrar la solución del sistema.
	Se aplica TL en cada miembro de la ecuación: $$
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
