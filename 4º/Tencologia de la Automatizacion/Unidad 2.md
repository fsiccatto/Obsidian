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
Y sea $T(t)$ una matriz no singular variante en el tiempo de dimensión $nxn$. Entonces el vector $z(t)=T(t)x(t)$ califica como un vector de estados del sistema, $x(t)$ puede ser recuperado de:
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
z'(t) &= Tx'(t) = T(Ax(t) + Bu(t)) = TAT{^{-1}}(t)z(t)+TBu(t) \\
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
>G(s) = \frac{Y(s)}{U(s)}
>$$
## Obtención de formas canónicas de representación interna
Las formas canónicas son representaciones específicas de sistemas en el espacio de estados que simplifican su análisis y diseño:
- <mark style="background: #BBFABBA6;">Forma Canónica de Control</mark>. Resalta la capacidad de controlar el sistema. Los coeficientes de la ecuación característica del sistema aparecen en la última fila de la matriz de estados, y la matriz de entrada tiene un vector con un único 1 en la última posición. Es útil para diseñar controladores. 
- <mark style="background: #FFB86CA6;">Forma Canónica de Observación</mark>. Enfatiza la capacidad de observar o medir el estado del sistema desde la salida. Los coeficientes de la ecuación característica están en la primera columna de la matriz de estados, y la matriz de salida tiene un vector con un único 1 en la primera posición. Es útil para diseñar observadores.
- <mark style="background: #FF5582A6;">Forma Canónica Diagonal</mark>. Simplifica el análisis al presentar la matriz de estados en una forma diagonal cuando la matriz es diagonalizable, lo que facilita el estudio de la dinámica del sistema.
- <mark style="background: #ADCCFFA6;">Forma Canónica de Jordan</mark>. Utilizada cuando la matriz de estados no es diagonalizable. Agrupa la matriz de estados en bloques de Jordan, reflejando la estructura interna y comportamientos más complejos del sistema.
### Forma canónica de control FCC
Los **estados de la FCC** se ordenan según la influencia que ejerce sobre los mismos la **entrada** de control. Este sistema me permite controlar el estado (por ejemplo un vector de temperaturas).
Sea el sistema diferencial:
$$
\frac{d^{n}y}{dt^{n}}+a_{1}\frac{d^{n-1}y}{dt^{n-1}}+\dots+a_{n-1}\frac{dy}{dt}+a_{n}y = u
$$
Se definen:
$$
x_{i} = \frac{d^{i-1}y}{dt^{i-1}}; \space i=1,2,\dots,n
$$
La anterior ecuación diferencial de orden $n$ se puede escribir como un sistema de $n$ ecuaciones diferenciales de primer orden. Es decir:
$$
\begin{align}
\begin{cases}
x_{1}'&=x_{2} \\
x_{2}'&=x_{3} \\
&\dots \\
x_{n}' &= -a_{n}x_{1}-\dots-a_{1}x_{n}+u \\
y &= x_{1}
\end{cases}
\end{align}
$$
Se puede deducir:
$$
\begin{align}
A=\begin{bmatrix}
0 & 1 & 0 & \dots & 0 \\
0 & 0 & 1 & \dots & 0  \\
\vdots & \vdots & \vdots& \ddots & \vdots  \\
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
$$-$$
![[imgs/ecuacion diferencial general.png | center]]
![[FCC grafico.png | center]]
Se introduce la nueva variable $v$ como salida del primer bloque y entrada al segundo bloque:
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
> ![[FCC.png | center]]
> $$
> \begin{align}
> A=\begin{bmatrix}
> 0 & 1 & 0 & \dots & 0 \\
> 0 & 0 & 1 & \dots & 0  \\
> \dots & \dots & \dots& \ddots & \vdots  \\
> 0 & 0 & 0 & \dots & 1  \\
> -a_{n} & -a_{n-1} & -a_{n-2} & \dots & -a_{1} \\
> \end{bmatrix}; \space
> B = \begin{bmatrix}
> 0 \\
> 0 \\
> 0 \\
> \vdots \\
> 1
> \end{bmatrix}; \space
> C=\begin{bmatrix}
> b_{n} & b_{n-1} & \dots b_{1}
> \end{bmatrix}
> \end{align}
> $$

$$-$$
### Forma canónica de observación FCO
Los **estados de la FCO** se ordenan según el grado de influencia de éstos sobre la **salida** del proceso. Garantiza que el sistema sea observable.
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
![[FCO ec.png | center]]
Es una tecnica de programación anidada:
![[FCO ec2.png | center]]
Al anti transformar se obtiene:
$$
\begin{align} 
\begin{cases}
x_{1}'=(-a_{n}x_{n}(t)+b_{n}u(t)) \\
x_{2}'=x_{1}(t)+(-a_{n-1}x_{n}(t)+b_{n-1}u(t)) \\
x_{3}'=x_{2}(t)+(-a_{n-2}x_{n}(t)+b_{n-2}u(t)) \\
\dots \\
x_{n}'=x_{n-1}(t)+(-a_{1}x_{n}(t)+b_{1}u(t))
\end{cases} \\ \\

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
> ![[FCO.png | center]]
> ![[FCO2.png | center]]

![[FCO bloques.png | center]]
- La matriz A de la FCC es la matriz A traspuesta de la FCO
- La matriz B traspuesta de la FCC, es la matriz C de la FCO
- La matriz C traspuesta de la FCC, es la matriz B de la FCO
### Forma canónica diagonal
Utilizando la definición de polos de la función de transferencia, se puede obtener diferentes representaciones según la naturaleza de los polos:
- <mark style="background: #D2B3FFA6;">Forma Diagonal</mark> $\to$ Se obtiene cuando **todos los polos del sistema son distintos**.
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
x_{i}(s) &=\frac{U(s)}{s-p_{i}} \\
x_{i}(s)(s-p_{i}) &=U(s) \\ 
sx_{i}(s) &=p_{i}x_{i}(t)+U(s) \\
x_{i}'(t) &=p_{i}x_{i}(t)+U(t)
\end{align}
$$
$$-$$
> [!info] Forma canónica diagonal
>
> $$
> \begin{bmatrix}
> x_{1} \\
> \vdots \\
> x_{n}
> \end{bmatrix}=
> \begin{bmatrix}
> p_{1} & 0 & \dots & 0 \\
> 0 & p_{2} & \dots & 0 \\ \\
> \vdots & \vdots & \ddots & \vdots  \\
> 0 & 0 & \dots & p_{n}
> \end{bmatrix}
> \begin{bmatrix}
> x_{1}  \\
> x_{2} \\
> \vdots \\
> x_{n}
> \end{bmatrix}+
> \begin{bmatrix}
> 1 \\
> 1 \\
> \vdots \\
> 1
> \end{bmatrix}u
> $$
> La ec de salida:
> $$
> y=\begin{bmatrix}
> d_{1} & d_{2} & \dots & d_{n}
> \end{bmatrix}
> \begin{bmatrix}
> x_{1} \\
> x_{2} \\
> \vdots \\
> x_{n}
> \end{bmatrix} = Cx
> $$

![[FCD bloques.png | center]]
### Forma canónica de Jordan
La matriz de estado no puede estar completamente diagonalizada. 
- <mark style="background: #D2B3FFA6;">Forma de Jordan</mark> $\to$ Se obtiene cuando **hay repetición de polos**, es decir, cuando el sistema tiene polos múltiples.
$$
\begin{align}
\frac{y(s)}{u(s)} &= \sum_{i=1}^n{\frac{d_{i}}{(s-p)^r}} \\
\frac{y(s)}{u(s)}&=\frac{d_{1}}{(s-p)^r}+\frac{d_{2}}{(s-p)^{r-1}}+\dots+\frac{d_{r-1}}{(s-p)^{2}}+\frac{d_{r}}{(s-p)}
\end{align}
$$
Para obtener las ecuaciones de estado, considerando la forma general de un polo $p$ de multiplicidad $r$, un polo $p_{j}$ diferente y otro polo $p_{n}$ diferente
$$
\frac{y(s)}{u(s)}=\frac{d_{1}}{(s-p)^r}+\frac{d_{2}}{(s-p)^{r-1}}+\dots+\frac{d_{r-1}}{(s-p)^{2}}+\frac{d_{r}}{(s-p)}+\frac{d_{n-1}}{(s-p_{j})}+\frac{d_{n}}{(s-p_{n})}
$$
Se define
$$
\begin{align}
\begin{cases}
x_{1}&=\frac{U(s)}{(s-p)^r} &\to &x_{1}'(t)&=px_{1}(t)+x_{2}(t) \\
x_{2}&=\frac{U(s)}{(s-p)^r-1} &\to &x_{2}'(t)&=px_{2}(t)+x_{3}(t) \\
\vdots \\
x_{r-1}&=\frac{U(s)}{(s-p)^2} &\to &x_{r-1}'(t)&=px_{r-1}(t)+x_{r}(t) \\
x_{r}&=\frac{U(s)}{(s-p)} &\to &x_{r}'(t)&=px_{r}(t)+u(t)\\
x_{j}&=\frac{U(s)}{(s-p_{j})} &\to &x_{j}'(t)&=p_{j}x_{j}(t)+u(t)\\
x_{n}&=\frac{U(s)}{(s-p_{n})} &\to &x_{n}'(t)&=p_{n}x_{n}(t)+u(t)
\end{cases}
\end{align}
$$
> [!info] Jordan
> La estructura matricial considerando la forma general de un polo p de multiplicidad r (bloque de Jordan) y dos polos $p_{j}$ y $p_{n}$ diferentes es:
>$$
A=\begin{bmatrix}
p & 1 & 0 & \dots & 0 & 0 \\
0 & p & 1 & \dots & 0 & 0\\
0 & 0 & p & \dots & 0  & 0\\
\vdots & \vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \dots & p_{j} & 0 \\
0 & 0 & 0 & \dots & 0 & p_{n}
\end{bmatrix} \space
B=\begin{bmatrix}
0 \\ 0 \\ 1 \\ 1 \\ \vdots \\ 1
\end{bmatrix} \space C=\begin{bmatrix}
d_{1} & d_{2} & d_{3} & \dots & d_{j} & d_{n} 
\end{bmatrix}
>$$
>Sistemas de ecuaciones:
>$$
\begin{align} \\
&\begin{cases}
x_{1}'(t)&=px_{1}(t)+x_{2}(t) \\
x_{2}'(t)&=px_{2}(t)+x_{3}(t)  \\
\vdots \\
x_{r-1}'(t)&=px_{r-1}(t)+x_{r}(t) \\
x_{r}'(t)&=px_{r}(t)+u(t)\\
x_{j}'(t)&=p_{j}x_{j}(t)+u(t)\\
x_{n}'(t)&=p_{n}x_{n}(t)+u(t)
\end{cases} \\ \\
&y(t)=d_{1}x_{1}+d_{2}x_{2}+\dots+d_{j}x_{j}+d_{n}x_{n}
\end{align}
>$$
Si algunas de las raíces del denominador son complejas, las matrices A y C tendrán coeficientes complejos.
## Unicidad de función de transferencia
Partimos de un LTI, representado por:
$$
\begin{equation} \\
\begin{cases}
x'(t) &=& Ax(t) + Bu(t) \\
y(t) &=& Cx(t) + Du(t)
\end{cases}
\end{equation}
$$
Por lo que:
$$
G(s)=\frac{y(s)}{u(s)}=\frac{{Cx(s)+Du(s)}}{u(s)}, \text{ donde } x(s)=(sI-A)^{-1}Bu(s)
$$
Reemplazando
$$
\begin{align}
G(s)&=\frac{y(s)}{u(s)}=\frac{{C((sI-A)^{-1}Bu(s))+Du(s)}}{u(s)} \\ \\
\Aboxed{G(s)&=\frac{y(s)}{u(s)}=C(sI-A)^{-1}B+D}
\end{align}
$$
$G(s)$ es la **función de transferencia** asociada a un sistema LTI.
La función de transferencia es invariante ante transformaciones de estado. No existe otra función de transferencia para un dado sistema. <mark style="background: #ABF7F7A6;">La función de transferencia es única</mark>.
## Relación entre representación interna y externa
> [!info] LTI
> Es posible transformar la representación interna de un sistema lineal invariante en el tiempo (LTI) a su representación externa y viceversa.

Es posible reconstruir las ecuaciones de estado, y por tanto la representación interna, a partir de una función de transferencia dada, identificando las matrices de estado que conforman el sistema.
### Pasaje de la representación Interna a la representación Externa
Visto en [[UTN-repo/4º/Tencologia de la Automatizacion/Unidad 2#Unicidad de función de transferencia]].
Es válida tanto para los sistemas SISO como MIMO, la salvedad es que en MIMO obtendríamos una matriz $G(s)$ de funciones de transferencia $pxm$ ($p$ dimensión del vector de salida y $m$ la dimensión del vector de entrada), donde cada elemento $G_{ij}(s)$ corresponde a la función de transferencia desde la entrada j-ésima $u_{j}$ a la salida i-ésima $y_{i}$.
### Pasaje de la representación Externa a la representación Interna
Este pasaje recibe el nombre de **realización**.
La realización de un sistema no es única, tenemos un LTI:
$$
\begin{equation} \\
\begin{cases}
x'(t) &=& Ax(t) + Bu(t) \\
y(t) &=& Cx(t) + Du(t)
\end{cases}
\end{equation}
$$
Se propone $T$ una matriz de transformación de estados, no singular con dimensión $nxn$. El vector $z(t)=Tx(t)$ que es como un vector de estados del sistema:
$$x(t) = T^{-1}z(t)$$
Lo que nos lleva al sistema:
$$
\begin{equation} \\
\begin{cases}
z'(t) &=& \overline{A}z(t) + \overline{B}u(t) \\
y(t) &=& \overline{C}z(t) + \overline{D}u(t)
\end{cases}
\end{equation}
$$
Estas representaciones internas diferentes tienen la misma función de transferencia que es única:
$$C(sI-A)^{-1}B+D=\overline{C}(sI-\overline{A})^{-1}\overline{B}+\overline{D}$$
Se dice que una **realización es mínima** si no existe otra realización con un vector de estado de menor dimensión. Esta dimensión coincide con el orden del sistema.

> [!info]
> Una realización es mínima si y solo si es completamente **controlable** y completamente **observable**.

Dada una función de transferencia $G(s)$ de la forma: la condición necesaria y suficiente para que sea realizable mediante una terna $[A, B, C]$ es que el grado del numerador debe ser menor o igual que el del denominador.
## Código MATLAB
``` matlab
A = [0 1; -0.4 -1.3];
B = [0; 1];
C = [0.8 1];
D = 0;
I = eye(2);

% Autovalores %
autovalores = eig(A);
syms s
G=inv(s*I - A);

% RESIDUE calcula las fracciones parciales

% LAPLACE calcula la transformada de laplace

% ILPLACE calcula la anti transformada de laplace

% pretty(G);

%-------------------------------%

sys = ss(A, B, C, D); % Sistema

Gs = tf(sys); %Funcion de transferencia
u = [1 1.3 0.4]; %Vector de entradas de la FT
y = [0 1 0.8]; %Vector de salida de la FT

sys2 = ss2tf(A, B, C, D); %Nos da el vector de salida de la funcion de transferencia

[A,B,C,D] = tf2ss(y,u); %Nos da A, B, C y D

fprintf('La funcion de tranferencia es:');
Gs
%% Podemos simplificar Gs a Gs=1/s+0.5
```