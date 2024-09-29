# Diagrama de Bloques
Un diagrama de bloques es una representación gráfica de las funciones que lleva a cabo cada componente y el flujo de señales.
Un diagrama de bloques representa la estructura de un sistema. Esto es, **las partes que lo forman** y el **modo en que se relacionan entre sí**.
Un diagrama de bloques no representa la forma ni el aspecto físico ni su funcionamiento.

| Descripcion                                                                                                                                                                                        | Imagen                               |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| Los bloques representan las partes del sistema. a. Las funciones de transferencia se introducen en los bloques. A los bloques también se les llama ganancia                                        | ![[imgs/bloque.png]]                      |
| Las flechas indican variables o señales de entrada o salida. Cada flecha representa una y sólo una variable y la punta de la flecha indica el sentido.                                             | ![[imgs/flecha.png]]                      |
| Un punto de suma es un círculo cuyo símbolo indica la operación suma (o resta). Es un elemento que sirve para combinar dos o más señales de entrada generando una salida que es su suma (o resta). | ![[imgs/punto suma.png]]                  |
| Un punto de ramificación es aquél a partir del cual la señal de un bloque va de modo concurrente a otros bloques o a puntos de suma                                                                | ![[imgs/punto de ramificacion.png]] |
## Lazo abierto
![[imgs/lazo abierto1.png]]
$$Y(s) = G(s)U(s)$$
## Lazo cerrado
![[imgs/lazo cerrado0.png]]
$$\begin{align}
Y(s) &= G(s)E(s) \\
E(s) &= U(s) - B(s) \\
B(s) &= H(s)Y(s)
\end{align}$$
$$\begin{align}
 Y(s)&=G(s)(U(s)-B(s)) \\
Y(s) &= G(s)U(s)-G(s)H(s)Y(s) \\
Y(s)(1+G(s)H(s)) &= G(s)H(s) \\
\frac{Y(s)}{U(s)} &= \frac{{G(s)}}{1+G(s)H(s)}
\end{align}$$
![[imgs/lazo cerrado2.png]]
Con **realimentación directa unitaria**:
$$\frac{Y(s)}{U(s)}=\frac{G(s)}{1+G(s)}$$
## Reglas del álgebra de bloques
Las reglas del álgebra de bloques se obtienen escribiendo la misma ecuación en formas distintas.
Las reglas del álgebra de bloques permiten hacer transformaciones de bloques en **serie, paralelo, lazos cerrados, movimientos de puntos de bifurcación, puntos suma, reduciendo** las mallas internas de realimentación sin alterar las señales involucradas en el movimiento, compensando con las funciones que sean necesarias.
### Elementos en serie
Los bloques en serie en un diagrama de bloques representan la multiplicación de sus respectivas funciones de transferencia. La multiplicación de funciones de transferencia es conmutativa, es independiente del orden de los bloques.
![[imgs/elementos en serie.png]]
### Elementos en paralelo
Los bloques en paralelo cumplen con la propiedad conmutativa cuando se aplican las reglas del álgebra de bloques. Esto significa que, si dos bloques están en paralelo, la suma de sus funciones de transferencia no se ve afectada por el orden en el que se suman.
![[imgs/elementos en paralelo.png]]
$$\frac{Y(s)}{U(s)}=G_{1}(s)+G_{2}(s)$$
## Simplificación de diagramas de bloques
Los diagramas de bloques de sistemas de control complicados se pueden simplificar usando una serie de **teoremas de transformación**, las cuales se obtienen fácilmente por deducción del significado de los elementos.
> Cualquier diagrama de bloques puede ser manipulado algebraicamente siguiendo unas reglas básicas para simplificar el diagrama hasta una sola función de transferencia.

Se avanza de adentro hacia afuera. Algunas consideraciones:
- Reducir los bloques complejos agrupando los elementos que están directamente conectados, como por ejemplo bloques en paralelo y en serie.
- Mover puntos de suma o puntos de ramificación según sea necesario antes o después de los bloques para facilitar la combinación y la reducción. Esto puede implicar desplazar estos puntos para ajustar las conexiones y reducir la representación del sistema.
- Identificar lazos de retroalimentación si están presentes y aplicar la transformación. 
- Trabajar hacia el exterior del diagrama, avanzando en la reducción paso a paso una vez que los bloques internos se han simplificado.
- Continuar el proceso de simplificación hasta que se obtenga una única función de transferencia que represente el sistema completo, es decir, llegar a un único bloque o proceso.
![[imgs/simplificacion1.png]]
![[imgs/simplificacion2.png]]
![[imgs/simplificacion3.png]]
![[imgs/simplificacion4.png]]