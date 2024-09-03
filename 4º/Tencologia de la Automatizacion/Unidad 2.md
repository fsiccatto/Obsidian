# Representación Interna y Externa de Sistemas
## Representación interna de un sistema. Transformación de estados
> [!info] Transformación de estados
> La transformación de estados permite obtener **diferentes representaciones** equivalentes del sistema, manteniendo su comportamiento dinámico pero cambiando la forma en que se expresa matemáticamente.

$$
\begin{equation} \\
\begin{cases}
x'(t) &=& Ax(t) + Bu(t) \\
y(t) &=& Cx(t) + Du(t)
\end{cases}
\end{equation}
$$
Y sea $T(t)$ una matriz no singular variante en el tiempo de dimensión $nxn$. . Entonces el vector $z(t)=T(t)x(t)$ califica como un vector de estados del sistema, $x(t)$ puede ser recuperado de:
$$
x(t) = T{^{-1}}z(t)
$$
La matriz $T(t)$ es llamada como la **matriz de transformación** de estados. Entonces:
$$
\begin{equation} \\
\begin{cases}
z'(t) &=& \overline{A}x(t) + \overline{B}u(t) \\
y(t) &=& \overline{C}z(t) + \overline{D}u(t)
\end{cases}
\end{equation}
$$
Se tiene:
$$
z(t) = Tx(t) \implies z'(t) = Tx'(t)
$$
Se puede concluir que:
$$
\begin{align} \\
\begin{cases}
z'(t) &= Tx'(t) = T(Ax(t) + Bu(t) = TAT{^{-1}}(t)z(t)+TBu(t)) \\
y(t) &= CT{^{-1}}z(t) + Du(t) \\
\end{cases}
\end{align}
$$
$$
\begin{align} \\
\begin{cases} 
\overline{A}=TAT{^{-1}}  \\
\overline{B} = TB \\
\overline{C} = CT{^{-1}} \\
\overline{D} = D
\end{cases}
\end{align}
$$
En realidad, $T$ representa un cambio de base en el espacio de estados y la matriz $T{^{-1}}AT$ es semejante a la matriz $A$.
> Los autovalores asociados a un sistema dinámico **no varían** con el **cambio de base**

Los autovalores se calculan:
$$
|\lambda I-A| = 0
$$
## Descripción Externa. Función de Transferencia

> [!info] Función de Transferencia
> La función de trasferencia de un sistema lineal es la **razón de la transformada de Laplace** de la variable de **salida** del sistema a la **transformada de Laplace** de la variable de **entrada**, con todas las **condiciones iniciales** asumidas como **cero**.
>$$
>G(s) = \frac{Y(S)}{U(S)}
>$$
## Obtención de formas canónicas de representación interna
Las formas canónicas son representaciones específicas de sistemas en el espacio de estados que simplifican su análisis y diseño:
- <mark style="background: #BBFABBA6;">Forma Canónica de Control</mark>. Resalta la capacidad de controlar el sistema. Los coeficientes de la ecuación característica del sistema aparecen en la última fila de la matriz de estados, y la matriz de entrada tiene un vector con un único 1 en la última posición. Es útil para diseñar controladores. 
- <mark style="background: #FFB86CA6;">Forma Canónica de Observación</mark>. Enfatiza la capacidad de observar o medir el estado del sistema desde la salida. Los coeficientes de la ecuación característica están en la primera columna de la matriz de estados, y la matriz de salida tiene un vector con un único 1 en la primera posición. Es útil para diseñar observadores.
- <mark style="background: #FF5582A6;">Forma Canónica Diagonal</mark>. Simplifica el análisis al presentar la matriz de estados en una forma diagonal cuando la matriz es diagonalizable, lo que facilita el estudio de la dinámica del sistema.
- <mark style="background: #ADCCFFA6;">Forma Canónica de Jordan</mark>. Utilizada cuando la matriz de estados no es diagonalizable. Agrupa la matriz de estados en bloques de Jordan, reflejando la estructura interna y comportamientos más complejos del sistema.
### Forma canónica de control FCC
Los **estados de la FCC** se ordenan según la influencia que ejerce sobre los mismos la **entrada** de control.
Sea el sistema diferencial:
$$
\frac{d^{n}y}{dt^{n}}+a_{1}\frac{d^{n-1}y}{dt^{n-1}}+\dots+a_{n-1}\frac{dy}{dt}+a_{n}y = u
$$
Se definen:
$$
x_{i} = \frac{d^{i-1}y}{dt^{i-1}}; \space u=1,2,\dots,n
$$
La anterior ecuación diferencial de orden n se puede escribir como un sistema de n ecuaciones diferenciales de primer orden. Es decir:
$$
\begin{align}
x_{1}'&=x_{2} \\
x_{2}'&=x_{3} \\
&\dots \\
x_{n}' &= -a_{n}x_{1}-\dots-a_{1}x_{n}+u \\
y &= x_{1}
\end{align}
$$
Se puede deducir:
$$
\begin{align}
A=\begin{bmatrix}
0 & 1 & 0 & \dots & 0 \\
0 & 0 & 1 & \dots & 0  \\
\dots & \dots & \dots& \ddots & \vdots  \\
0 & 0 & 0 & \dots & 1  \\
-a_{n} & -a_{n-1} & -a_{n-2} & \dots & -a_{1} \\
\end{bmatrix}; \space
B = \begin{bmatrix}
0 \\
0 \\
0 \\
\vdots \\
1
\end{bmatrix}; \space
C=\begin{bmatrix}
1 & 0 & 0 & \dots & 0
\end{bmatrix}
\end{align}
$$
![[ecuacion diferencial general.png]]
![[FCC grafico.png]]
Se introduce la nueva variable v como salida del primer bloque y entrada al segundo bloque:
$$
\frac{v(s)}{u(s)} = \frac{1}{d(s)}
$$
O sea:
$$
\begin{align}
d(s)v(s)=u(s)  \\
n(s)v(s)=y(s)
\end{align}
$$
Por lo que:
$$
y(s)=(b_{1}s^{n-1} + b_{2}s^{n-2} + \dots + b_{n-1}s +b_{n})v(s)
$$
Aplicando distributiva y anti transformada de Laplace con condiciones iniciales nulas:
$$
y(t)=b_{1}x_{n}+b_{2}x_{n-1}+\dots+b_{n-1}x_{2}+b_{n}x_{1}
$$
entonces,
$$
C=\begin{bmatrix}
b_{n} & b_{n-1} & \dots b_{1}
\end{bmatrix}
$$
> [!info] FCC
> ![[FCC.png]]
> $$
\begin{align}
A=\begin{bmatrix}
0 & 1 & 0 & \dots & 0 \\
0 & 0 & 1 & \dots & 0  \\
\dots & \dots & \dots& \ddots & \vdots  \\
0 & 0 & 0 & \dots & 1  \\
-a_{n} & -a_{n-1} & -a_{n-2} & \dots & -a_{1} \\
\end{bmatrix}; \space
B = \begin{bmatrix}
0 \\
0 \\
0 \\
\vdots \\
1
\end{bmatrix}; \space
C=\begin{bmatrix}
b_{n} & b_{n-1} & \dots b_{1}
\end{bmatrix}
\end{align}
$$

### Forma canónica de observación FCO
Los **estados de la FCO** se ordenan según el grado de influencia de éstos sobre la **salida** del proceso.
Sea la ecuación diferencial con coeficientes constantes:
$$
y^{n}(t)+a_{1}y^{n-1}(t)+a_{2}y^{n-2}(t)+\dots+a_{n-1}y'(t)+a_{n}y(t)=b_{1}u^{n-1}(t)+b_{2}u^{n-2}(t)+\dots+b_{n-1}u'(t)+b_{n}u(t)
$$
Se aplica transformada de Laplace con condiciones iniciales nulas:
$$
s^{n}y(s)+a_{1}s^{n-1}y(s)+a_{2}s^{n-2}y(s)+\dots+a_{n-1}sy(s)+a_{n}y(s)=b_{1}s^{n-1}u(s)+b_{2}s^{n-2}u(s)+\dots+b_{n-1}su(s)+b_{n}u(s)
$$
Agrupamos términos de acuerdo a la potencia de s y se llega a:
$$
s^{n}y(s)+s^{n-1}(a_{1}y(s)-b_{1}u(s))+s^{n-2}(a_{2}y(s)-b_{2}u(s))+\dots+s(a_{n-1}y(s)-b_{n-1}u(s))+a_{n}y(s)-b_{n}u(s)=0
$$
Si se despeja el primer término $y(s)$, se pasan todos los términos al otro lado, se divide por cada término por $s^n$, esto conduce a la siguiente ecuación:
$$
y(s)=s^{-1}(b_{1}y(s)-a_{1}u(s))+s^{-2}(b_{2}y(s)-a_{2}u(s))+\dots+s^{-n+1}(b_{n-1}y(s)-a_{n-1}u(s))+s^{-n}(b_{n}y(s)-a_{n}u(s))=0
$$
Todos los términos se pueden escribir en términos de potencia $s{^{-1}}$. Se define $y(s)=x_{n}(s)$, que llevará a encontrar las ecuaciones de estado correspondiente:
![[Pasted image 20240903150715.png]]
Es una tecnica de programación anidada:
![[Pasted image 20240903150943.png]]
Al anti transformar se obtiene:
$$
\begin{align} 
\begin{cases}
x_{1}'=(-a_{n}x_{n}(t)+b_{n}u(t)) \\
x_{2}'=x_{1}(t)+(-a_{n-1}x_{n}(t)+b_{n-1}u(t)) \\
x_{3}'=x_{2}(t)+(-a_{n-2}x_{n}(t)+b_{n-2}u(t)) \\
\dots \\
x_{n}'=x_{n-1}(t)+(-a_{1}x_{n}(t)+b_{1}u(t))
\end{cases} \\
y(t)= \begin{bmatrix}
0 & 0 & \dots & 1
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix}
\end{align}
$$
> [!info] FCO
> ![[FCO.png]]
> ![[FCO2.png]]

![[FCO bloques.png]]
- La matriz A de la FCC es la matriz A transpuesta de la FCO
- La matriz B transpuesta de la FCC, es la matriz C de la FCO
- La matriz C transpuesta de la FCC, es la matriz B de la FCO
### Forma canónica diagonal
Utilizando la definición de polos de la función de transferencia, se puede obtener diferentes representaciones según la naturaleza de los polos:
- <mark style="background: #D2B3FFA6;">Forma Diagonal</mark> $\to$ Se obtiene cuando **todos los polos del sistema son distintos**.
- <mark style="background: #D2B3FFA6;">Forma de Jordan</mark> $\to$ Se obtiene cuando **hay repetición de polos**, es decir, cuando el sistema tiene polos múltiples.
Los elementos no nulos y diferentes (**los polos**) se encuentran únicamente en la diagonal principal.
Dada la función de transferencia expresada como sumas parciales con n polos diferentes $p_{1},p_{2},\dots,p_{n}$ y residuos $d_{1},d_{2},\dots,d_{n}$:
$$
\begin{align}
\frac{y(s)}{u(s)}&=\sum_{i=1}^n{\frac{d_{i}}{s-p_{i}}} \\
\frac{y(s)}{u(s)}&=\frac{d_{1}}{s-p_{1}}+\frac{d_{2}}{s-p_{2}}+\dots+\frac{d_{n}}{s-p_{n}}
\end{align}
$$
Entonces:
$$
y(s)=\frac{d_{1}}{s-p_{1}}U(s)+\frac{d_{2}}{s-p_{2}}U(s)+\dots+\frac{d_{n}}{s-p_{n}}U(s)
$$
$$
\begin{align}

x_{i}(s)&=\frac{U(s)}{s-p_{i}} \\
x_{i}(s)(s-p_{i})&=U(s) \\ 
sx_{i}(s)&=p_{i}x_{i}(t)+U(s) \\
x_{i}'(t)&=p_{i}x_{i}(t)+U(t)
\end{align}
$$
> [!info] Forma canónica diagonal
> $$
 \begin{bmatrix}
> x_{1} \\
 \vdots \\
 x_{n}
 \end{bmatrix}=
 \begin{bmatrix}
 p_{1} & 0 & \dots & 0 \\
 0 & p_{2} & \dots & 0 \\
 \vdots & \vdots & \ddots & \vdots  \\
 0 & 0 & \dots & p_{n}
 \end{bmatrix}
 \begin{bmatrix}
 x_{1}  \\
 x_{2} \\
 \vdots \\
 x_{n}
 \end{bmatrix}+
 \begin{bmatrix}
 1 \\
 1 \\
 \vdots \\
 1
 \end{bmatrix}u
> $$
> La ec de salida:
> $$
 y=\begin{bmatrix}
 d_{1} & d_{2} & \dots & d_{n}
 \end{bmatrix}
 \begin{bmatrix}
 x_{1} \\
 x_{2} \\
 \vdots \\
 x_{n}
 \end{bmatrix} = Cx
> $$

![[FCD bloques.png]]
### Forma canónica de Jordan
