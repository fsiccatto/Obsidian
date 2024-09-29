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

![[imgs/transitoriaPermanente.png]]
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
	![[imgs/LTI orden1.png]]
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
![[imgs/entrada impulso.png]]
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
![[imgs/entrada escalon.png]]
### Entrada rampa unitaria
La transformada de Laplace al aplicar rampa unitaria es:
$$U(s)=\frac{1}{s{^2}}\implies Y(s)=\frac{1}{1+Ts}{\frac{1}{s{^2}}}$$
Al antitransformar para $t>0$ se obtiene:
$$y(t)=t-T+Te{^{-t/T}}$$
![[imgs/entrada rampa.png]]
$$e(t)=T(1-e{^{-t/T}})$$
Cuando $t\to \infty$ el error tiende a $T$. 
![[imgs/error rampa.png]]
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
![[imgs/plano complejo.png]]
#### Estabilidad Relativa
La estabilidad relativa es una **medida cuantitativa de la rapidez con que la respuesta transitoria del sistema tiende a cero**. Cuanto menor sea el tiempo que tarda en estabilizarse la respuesta, es sistema es más estable relativamente.
Cuanto más alejados estén los polos del eje imaginario, menor será el tiempo de estabilización.
### Clasificación
- #### Sistema Estable
Un sistema es estable si las **raíces de la ecuación característica son reales negativas o complejas conjugadas con parte real negativa**. O dicho en forma más compacta, **si todas las raíces se encuentran en el semiplano izquierdo de la variable compleja s**.
 - #### Sistema Inestable
 Si **algún polo del sistema se encuentra ubicado en el semiplano derecho del plano s**, automáticamente el sistema es Inestable.
 ![[imgs/plano S.png]]
 - #### Sistema críticamente estable
 Un sistema es limitadamente estable, críticamente estable si **hay un polo en el origen y los demás polos en el semiplano negativo**.
 Si existen más de un polo
 ![[imgs/criticamente estable.png]]
- #### Sistema marginalmente estable
Un sistema es marginalmente estable **si existe una pareja simple** (sin multiplicidad) **de polos complejos conjugados sobre el eje imaginario** (o sea no tienen componente real), estando el r**esto de los polos en el semiplano negativo**.
Si existe más de una pareja de polos complejos, el sistema es inestable
![[imgs/marginalmente estable.png]]
