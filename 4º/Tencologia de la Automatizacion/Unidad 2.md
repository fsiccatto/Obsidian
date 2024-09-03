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
Y sea $T(t)$ una matriz no singular variante en el tiempo de dimensión $nxn$. . Entonces el vector `z(t)=T(t)x(t)` califica como un vector de estados del sistema, `x(t)` puede ser recuperado de:
$$
x(t) = T{^{-1}}z(t)
$$
La matriz T(t) es llamada como la **matriz de transformación** de estados. Entonces:
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

