# Análisis de Salida. Estabilidad
Un sistema **estable** es aquel que, pese a las perturbaciones o cambios en las entradas, puede mantener un comportamiento controlado y predecible. La estabilidad es crucial para garantizar que el sistema funcione de manera confiable y segura, incluso frente a variaciones externas.
En las representaciones internas, la estabilidad se evaluará mediante el análisis de los **autovalores de la matriz del sistema** y el **diagrama de fase**.
Por otro lado, en las representaciones externas, la estabilidad del sistema se examinará a través del estudio de los **polos de la función de transferencia**, ya que su ubicación en el plano complejo determina la respuesta del sistema.

> [!info] Error
> La señal de error $E(s)$ resulta de la diferencia entre la entrada $U(s)$ y la salida medida $Y(s)$.

Las señales de prueva son:
- Delta Dirac $\to$ $u(t)=1 \text{ para } t\geq 0$
- Función Rampa $\to$ $f(t)=t \text{ para } t\geq 0$
- Función parabólica$\to$ $f(t)=t{^2} \text{ para } t\geq 0$
## Régimen transitorio y permanente
El régimen transitorio se refiere a la respuesta del sistema que se produce después de una perturbación inicial y antes de alcanzar un estado estable. <mark style="background: #BBFABBA6;">Capacidad del sistema para adaptarse</mark>.
El régimen transitorio se describe a través de la **solución homogénea** de la ecuación diferencial lineal, que representa la respuesta del sistema sin considerar la entrada externa

> [!info] Transitorio
> El régimen transitorio es aquella respuesta que se extingue en el tiempo.

Por otro lado, el régimen permanente es la parte de la respuesta del sistema que se manifiesta una vez que el régimen transitorio ha desaparecido y el sistema ha alcanzado un estado estable. <mark style="background: #FF5582A6;">Comportamiento del sistema en condiciones de operación normal</mark>.
El régimen permanente se obtiene a partir de la **solución particular** de la ecuación diferencial, que representa la respuesta del sistema a la entrada específica

> [!info] Permanente
> El régimen permanente es la respuesta que permance constante hasta que ser varíe la entrada.

![[imgs/transitoriaPermanente.png | center]]
El **amortiguamiento** indica la evolución del transitorio, que se puede aproximar monótonamente o no, al régimen permanente.
### Error
El error es la diferencia entre el valor real y el valor deseado para cada una de las variables de salida del sistema de control ha de ser la menor posible.
> [!info] Error
> $E(s)=U(s)-Y(s)$
## Clasificación de los sistemas de control
El sistema se representa por:
- Tipo
- Orden
- Polos
- Ceros
## Sistema de primer orden
Sistema LTI en régimen dinámico definido por una ecuación diferencial lineal de coeficientes constantes de orden uno
$$y'(t)+a_{1}y(t)=b_{1}u(t)$$
Aplicando transforamda de Laplace:
$$\begin{align}
sY(s)+a_{1}Y(s)&=b_{1}U(s) \\
Y(s)(s+a_{1})&=b_{1}U(s) \\
\frac{Y(s)}{U(s)}&=\frac{b_{1}}{s+a_{1}}
\end{align}$$
- Ejemplo:
	![[imgs/LTI orden1.png | center]]
	con $G(s)=\frac{1}{1+Ts}$
### Entrada de tipo impulso
$$\begin{align}
u(t)=\begin{cases}
0, t<0 \\
\infty, t=0 \\
0, t>0
\end{cases}
\end{align}$$
Por lo que $U(s)=1$, entonces $Y(s)=G(s)$
Para el sistema del ejemplo:
$$
\begin{align}
G(s)&=\frac{1}{1+Ts} \\
Y(s)&=\frac{1}{1+Ts}*1, \text{ con }U(s)=1 \\
y(t)&=\frac{1}{T}e{^{-t/T}}
\end{align}
$$
La señal de error disminuye con el tiempo como una exponencial. Al igual que en los casos anteriores, cuanto menor es el tiempo $T$ más se parece la respuesta al estímulo.
La salida es:
![[imgs/entrada impulso.png | center]]
### Entrada tipo escalón
Permite conocer la respuesta del sistema frente a cambios abruptos en su entrada, se expresa como $u(t)=Au(t), \text{A constante}$
$$\begin{align}
u(t)=\begin{cases}
0, t<0 \\
1, t\geq0
\end{cases}
\end{align}$$
Entonces si A=1:
$$U(s)=\frac{1}{s} \implies Y(s)={\frac{1}{1+Ts}}{\frac{1}{s}}$$
Al antitransformar para $t>0$
$$y(t)=1-e^{-t/T}$$
![[imgs/entrada escalon.png | center]]
### Entrada rampa unitaria
La transformada de Laplace al aplicar rampa unitaria es:
$$U(s)=\frac{1}{s{^2}}\implies Y(s)=\frac{1}{1+Ts}{\frac{1}{s{^2}}}$$
Al antitransformar para $t>0$ se obtiene:
$$y(t)=t-T+Te{^{-t/T}}$$
![[imgs/entrada rampa.png | center]]
$$e(t)=T(1-e{^{-t/T}})$$
Cuando $t\to \infty$ el error tiende a $T$. 
![[imgs/error rampa.png | center]]
## Sistema de segundo orden
La ecuación diferencial de segundo orden con coeficientes constatntes queda definida como:
$$y''(t)+a_{1}y'(t)+a_{2}y(t)=b_{0}u''(t)+b_{1}u'(t)+b_{2}u(t)$$
Aplicando transformada de Laplace:
$$
\begin{align}
s{^2}Y(s)+a_{1}sY(s)+a_{2}Y(s)&=b_{0}s{^2}U(s)+b_{1}sU(s)+b_{2}U(s) \\
Y(s)(s{^2}+a_{1}s+a_{2})&=U(s)(b_{0}s{^2}+b_{1}s+b_{2}) \\
\frac{Y(s)}{U(s)}&=\frac{b_{0}s{^2}+b_{1}s+b_{2}}{s{^2}+a_{1}s+a_{2}}
\end{align}
$$
En términos generales:
$$\frac{k\omega_{n}{^2}}{s{^2}+2\xi \omega_{n}s+\omega_{n}{^2}}$$
donde $\omega_{n}$ es la frecuencia natural de oscilación, $\xi$ es el coeficiente de amortiguamiento y $k$ es la ganancia de estado estacionario.
### Comportamiento según polos
Los polos están dados por:
$$
s_{1,2}=\frac{{-2\xi \omega_{n}\pm \sqrt{4\xi{^2}\omega_{n}{^2}-4\omega_{n}{^2}}}}{2} = -\omega_{n}\xi\pm\omega_{n}\sqrt{ \xi{^2}-1 }=\omega_{n}(-\xi\pm \sqrt{ \xi{^2} -1})
$$
A partir de 
$$s_{1,2}=\omega_{n}(-\xi\pm \sqrt{ \xi{^2} -1})$$
Se analizan distintos valores para $\xi$:

| Valor de $\xi$   | Descripción                                                                                                                                                                                                                                                                                                                                                                               |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $$\xi > 1$$      | Las raíces son **reales diferentes y negativas**. <br>La respuesta del sistema es una suma de términos exponenciales con signos negativos.<br>Esto se define como un Comportamiento monotónico <mark style="background: #BBFABBA6;">estable o Sobreamortiguado</mark>.                                                                                                                    |
| $$\xi = 1$$      | Las raíces son **reales iguales y negativas**.<br>La respuesta del sistema es una expresión exponencial con signo negativo. <br>Esto muestra un Comportamiento monotónico <mark style="background: #FFB86CA6;">estable crítico o amortiguado crítico</mark>. Si se disminuye el coeficiente de amortiguamiento, la respuesta es subamortiguada, y si se aumenta, es más sobreamortiguada. |
| $$0 < \xi < 1$$  | Las raíces son **complejas conjugadas con parte real negativa**.<br>La respuesta del sistema es una expresión exponencial sinusoidal decreciente.<br>Esto muestra un Comportamiento <mark style="background: #FF5582A6;">oscilatorio estable o subamortiguado estable</mark>.                                                                                                             |
| $$\xi = 0$$      | Las raíces son cantidades **imaginarias iguales de signo contrario**.<br>La respuesta del sistema es una expresión sinusoidal.<br>Esto muestra un Comportamiento <mark style="background: #ADCCFFA6;">oscilatorio sostenido</mark>.                                                                                                                                                       |
| $$-1 < \xi < 0$$ | Las raíces son **complejas conjugadas con parte real positiva**.<br>La respuesta del sistema es una expresión exponencial sinusoidal creciente.<br>Esto muestra un Comportamiento <mark style="background: #FFB8EBA6;">oscilatorio inestable o subamortiguado inestable</mark>, es decir, con oscilaciones de amplitud creciente.                                                         |
| $$\xi \leq -1$$  | Las raíces son **reales positivas**.<br>La respuesta del sistema es una expresión exponencial con signos positivos.<br>Esto muestra un Comportamiento <mark style="background: #ABF7F7A6;">monotónico inestable o Sobreamortiguado inestable</mark>.                                                                                                                                      |
## Estabilidad
Cuando se plantea un sistema de control, la propiedad más importante que lo caracteriza es su estabilidad.

> Desde el punto de vista de la **representación externa**, se dice que un LTI  es estable, si en condiciones iniciales nulas, ante una **entrada acotada** se produce una **salida también acotada**.

Para analizar la estabilidad:
- Análisis de polos: ubicación de los polos en el plano complejo
- Criterio Routh-Huewitz: analiza la ecuación característica del sistema
- Criterios de Nyquist y diagramas de Bode, utilizados en el análisis en el dominio de la frecuencia y el lugar de las raíces en el plano s.

> Desde el punto de vista de la **representación interna**, un sistema estable está relacionado con el comportamiento de las soluciones de la ecuación de estado que describe su dinámica. Si todas las s**oluciones de la ecuación convergen a un punto de equilibrio el sistema es estable**.

Para analizar la estabilidad:
- Análisis de autovalores: . si todos los autovalores tienen parte real negativa, el sistema es estable, ya que las soluciones tienden al equilibrio cuando t→∞.
- Plano fase: representa gráficamente la evolución de las variables de estado del sistema.
### Estabilidad absoluta y relativa
#### Estabilidad Absoluta
Si un sistema lineal invariante en el tiempo es estable volverá a su condición de equilibrio después ser sometido a una perturbación en una de sus entradas.
Un sistema continuo es **estable** cuando **todas las raíces de su ecuación característica se encuentran localizadas en el semiplano izquierdo del plano s**.
![[imgs/plano complejo.png | center]]
#### Estabilidad Relativa
La estabilidad relativa es una **medida cuantitativa de la rapidez con que la respuesta transitoria del sistema tiende a cero**. Cuanto menor sea el tiempo que tarda en estabilizarse la respuesta, es sistema es más estable relativamente.
Cuanto más alejados estén los polos del eje imaginario, menor será el tiempo de estabilización.
### Clasificación
- #### Sistema Estable
Un sistema es estable si las **raíces de la ecuación característica son reales negativas o complejas conjugadas con parte real negativa**. O dicho en forma más compacta, **si todas las raíces se encuentran en el semiplano izquierdo de la variable compleja s**.
 - #### Sistema Inestable
 Si **algún polo del sistema se encuentra ubicado en el semiplano derecho del plano s**, automáticamente el sistema es Inestable.
 ![[imgs/plano S.png | center]]
 - #### Sistema críticamente estable
 Un sistema es limitadamente estable, críticamente estable si **hay un polo en el origen y los demás polos en el semiplano negativo**.
 Si existen más de un polo
 ![[imgs/criticamente estable.png | center]]
- #### Sistema marginalmente estable
Un sistema es marginalmente estable **si existe una pareja simple** (sin multiplicidad) **de polos complejos conjugados sobre el eje imaginario** (o sea no tienen componente real), estando el r**esto de los polos en el semiplano negativo**.
Si existe más de una pareja de polos complejos, el sistema es inestable.
![[imgs/marginalmente estable.png | center]]
> [!todo]
> - **Convergencia**
> 	- Polos con parte real negativa
> 	- Polos simples con parte real nula dan lugar a términos que ni crecen ni desaparecen en l tiempo
> - **Rapidez**
> 	- Cuanto más negativa sea la parte real, más rápido decrece la exponencial
> 	- Cuanto más grande sea la parte imaginaria, mayor es la frecuencia de las oscilaciones
> - **Amortiguamiento**
> 	- Si los polos son complejos con parte real negativa, un cociente pequeño a/b de los valores absolutos de la parte real y la imaginaria, indica que serán aparentes varias oscilaciones antes que la exponencial las anule. Se habla entonces de polos pocos amortiguados

### Criterio de Routh-Hurwitz
> [!info] Método Routh-Hurwitz
>Es un criterio matemático utilizado para determinar la estabilidad de un sistema lineal a partir de su ecuación característica. Esta ecuación característica *se obtiene a partir del denominador de la función de transferencia* de un sistema. El criterio **permite verificar si las raíces (o polos) de dicha ecuación tienen partes reales negativas**, lo que indica que el sistema es **estable**.

Nos dice cuantos polos están del lado derecho y cuantos del lado izquierdo.
Tenemos una función de transferencia:
$$
\frac{Y(s)}{U(s)} = \frac{b_{0}s^m+b_{1}s^{m-1}+b_{2}s^{m-2}+\dots+b_{m-1}s+b_{m}}{a_{0}s^n+a_{1}s^{n-1}+a_{2}s^{n-2}+\dots+a_{n-1}s+a_{n}}
$$
Debemos analizar los ceros del denominador:
$$a_{0}s^n+a_{1}s^{n-1}+a_{2}s^{n-2}+\dots+a_{n-1}s+a_{n}=0, \text{ donde }a_{n}\neq 0$$
$a_{n}\neq 0$ para cumplir condición de Cardano y para eliminar la posibilidad de raíz nula.
Necesitamos que todos los coeficientes resulten positivos (o negativos), sino podemos decir que es inestable. Ordenamos los coeficientes del poliniomio en renglones y columnas:
$$
\begin{matrix}
s^n & a_0 & a_2 & a_4 & a_6 & \cdots \\
s^{n-1} & a_1 & a_3 & a_5 & a_7 & \cdots \\
s^{n-2} & b_1 & b_2 & b_3 & b_4 & \cdots \\
s^{n-3} & c_1 & c_2 & c_3 & c_4 & \cdots \\
s^{n-4} & d_1 & d_2 & d_3 & d_4 & \cdots \\
\vdots & \vdots & \vdots & \vdots & \vdots \\
s^2 & e_1 & e_2 &  &  & \\
s^1 & f_1 &  &  &  & \\
s^0 & g_1 &  &  &  & \\
\end{matrix}
$$
Los coeficientes $b_{n}, c_{n}, d_{n}, \dots$ se evalúan como sigue:
$$
\begin{aligned}
b_1 &= \frac{a_3 - a_1}{a_2}, \quad b_2 = \frac{a_1 - a_3}{a_2}, \quad b_3 = \frac{a_4 - a_{n-1}}{a_n}, \\
c_1 &= \frac{b_{n-2} - a_{n-3}}{b_n}, \quad c_2 = \frac{b_{n-4} - a_{n-5}}{b_n}, \quad c_3 = \frac{b_{n-6} - a_{n-7}}{b_n}, \\
d_n &= \frac{{c_b}_3 - {b_c}_2}{c_t}, \quad d_m = \frac{{c_b}_5 - {b_c}_4}{c_t} \\
\vdots
\end{aligned}
$$
La evaluación continua hasta que todas las restantes son cero.

El criterio de estabilidad de Routh- Hurwitz plantea que el **número de raíces de la ecuación con partes reales positivas es igual al número de cambios de signo de los coeficientes de la *primera* columna del arreglo**.

La *condición necesaria y suficiente* para que **todas las raíces de la ecuación se encuentren en el semiplano izquierdo del plano s es que todos los coeficientes de la ecuación sean positivos y que todos los términos de la primera columna del arreglo tengan signo positivo**.
### Plano de fase. Autovalores del sistema
> [!info] Plano de fase
> La trayectoria en el plano de fase del sistema permite determinar gráficamente si el sistema es o no estable. Una familia de trayectorias de evolución del sistema se denomina Diagrama de Plano de Fase. La trayectoria en el plano de fase del sistema permite determinar gráficamente si el sistema es o no estable. Si las **trayectorias convergen al punto de equilibrio** el sistema es *estable*.

 - Ejemplos de puntos de equilibrio
	![[imgs/ejemplos punto de equilibrio.png]]
Para determinar la **estabilidad** de un sistema, <mark style="background: #CACFD9A6;">se observan las trayectorias en torno a puntos de equilibrio. Si las trayectorias convergen hacia el punto de equilibrio, el sistema es estable, caso contrario es inestable</mark>.
Para desarrollar el diagrama de plano de fase y determinar la estabilidad:
1. Definir el conjunto de ecuaciones del sistema. El conjunto de ecuaciones diferenciales describen el comportamiento dinámico del sistema. Las mismas se expresan en términos de las variables de estado.
2. Identificar puntos críticos o de equilibrio. Resolver las ecuaciones del sistema de ecuaciones diferenciales igualando las derivadas a cero, lo que dará el/los punto/s donde el sistema no cambia con el tiempo.
3. Resolver el sistema de ecuaciones. Encontrar las soluciones del sistema de ecuaciones diferenciales, que describen cómo evolucionan las variables de estado en el tiempo.
4. Trazar las trayectorias en el plano de fase. Utilizar las soluciones de las ecuaciones diferenciales para dibujar las trayectorias. Estas representarán cómo cambian las variables de estado a lo largo del tiempo.
5. Analizar y determinar la estabilidad. Observar las trayectorias resultantes respecto de la cercanías al/los punto/s de equilibrio. Si converge/n hacia el mismo/s, el sistema es estable, caso contrario es inestable .
VER EJEMPLO 
### Clasificación de puntos críticos o de equilibrio
Podemos clasificar el sistema en función de los autovalores de A:

| Clasificación                                                                                                                                                                              | Imagen                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------- |
| **Autovalores reales y distintos menores a 0**. Todas las soluciones tienden a 0 y las órbitas o trayectorias tienden al origen. El punto crítico o de equilibrio es un nodo estable.      | ![[imgs/clasificacion1.png\| center]] |
| **Autovalores reales y distintos mayores a 0**. Todas las soluciones tienden a ∞ y las órbitas o trayectorias se alejan del origen. El punto crítico o de equilibrio es un nodo inestable. | ![[imgs/clasificacion2.png\| center]]   |
| **Autovalores dobles negativos y A diagonal**. El punto es un nodo estelar estable.                                                                                                        | ![[imgs/clasificacion3.png\| center]]  |
| **Autovalores dobles positivos y A diagonal**. El punto es un nodo estelar inestable.                                                                                                      | ![[imgs/clasificacion4.png\| center]] |
| **Autovalores dobles negativos y A no diagonal**. El punto es un nodo tangente estable.                                                                                                    | ![[imgs/clasificacion5.png\| center]] |
| **Autovalores dobles positivos y A no diagonal**. El punto es un nodo tangente inestable.                                                                                                  | ![[imgs/clasificacion6.png\| center]] |
| **Autovalores complejos con s = 0**. Todas las soluciones son periódicas y las órbitas son curvas cerradas rodeando el origen. El nodo se llama centro.                                    | ![[imgs/clasificacion7.png\| center]] |
| **Autovalores complejos con s < 0**. La exponencial decreciente obliga a las órbitas a cerrarse en espiral cuando t→∞ hacia el origen. El nodo se llama foco estable.                      | ![[imgs/clasificacion8.png\| center]] |
| **Autovalores complejos con s > 0**. Las espirales corresponden a soluciones que se alejan del punto crítico. El nodo se llama foco inestable.                                             | ![[imgs/clasificacion9.png\| center]] |
### Error en estado estacionario o permanente
> [!error] Error estado estacionario o permanente
> El error en un sistema de control es la diferencia entre el valor deseado o de entrada $u(t)$ y el valor actual de salida $y(t)$, de la variable controlada.
> ![[imgs/error estado estable.png| center]]

![[imgs/error dependiendo entrada.png]]
![[imgs/tipo error.png]]