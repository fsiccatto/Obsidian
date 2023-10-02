#### Ejercicio 1
Definir una función recursiva para multiplicar dos enteros m y n.
$$
\begin{equation}
     Mult(m, n) = \left\{
	       \begin{array}{ll}
		 0 & \mathrm{si\ } m = 0 \\
		 n + Mult(m, n) & \mathrm{si\ } m > 0 \\
	    \end{array}
	\right.
\end{equation}
$$
```
FUNCION Mult(m, n: ENTERO): ENTERO
INICIO
	SI (m = 0) ENTONCES
		Mult = 0
	SINO
		n * Mult(m - 1, n)
	FINSI
RETORNO
```
#### Ejercicio 2
Escribir una función recursiva que calcule potencia de enteros $`x^{n} \text{ (x: real y n: entero)}`$.
$$
\begin{equation}
     Prod(x, n) = \left\{
	       \begin{array}{ll}
		 1 & \mathrm{si\ } n = 0 \\
		 x * Prod(x, n - 1) & \mathrm{si\ } n > 0 \\
	    \end{array}
	\right.
\end{equation}
$$
```
FUNCION Prod(x: REAL, n: ENTERO): REAL
INICIO
	SI (x = 0) ENTONCES
		Prod = 0
	FINSI
	SI (n = 0) ENTONCES
		Prod = 1
	SINO
		x * Prod(x, n - 1)
	FINSI
RETORNO
```
#### Ejercicio 3
Escribir el inverso de un entero dado (por ej. el inverso de 1234 es 4321)
$$
\begin{equation}
     EscEntInv(num) = \left\{
	       \begin{array}{ll}
		 ESCRIBIR(num) & \mathrm{si\ } num < 10\\
		 ESCRIBIR(num \ MOD \ 10), \ EscEntInv(n / 10) & \mathrm{si\ } num \geqslant 10 \\
	    \end{array}
	\right.
\end{equation}
$$
```
PROCEDIMIENTO EscEntInv(num: ENTERO)
INICIO
	ESCRIBIR(num MOD 10)
	SI (num >= 10) ENTONCES
		EscEntInv(num / 10)
	FINSI
FINPROCEDIMIENTO
```
#### Ejercicio 4
Escribir un procedimiento recursivo al que se le pase como parámetro un número n en base 10 (decimal), e imprima su valor en base 2 (binario). Por ej. si n = 12 debe mostrar 1100.
$$
\begin{equation}
     DecBin(n) = \left\{
	       \begin{array}{ll}
		 ESCRIBIR(n) & \mathrm{si\ } n = 2 \\
		 DecBin(n / 2), \ ESCRIBIR(n \ MOD \ 2) & \mathrm{si\ } n \geqslant 2 \\
	    \end{array}
	\right.
\end{equation}
$$
```
PROCEDIMIENTO DecBin(n: ENTERO)
INICIO
	SI (n >= 2) ENTONCES
		DecBin(n / 2)
	FINSI
	ESCRIBIR(n MOD 2)
FINPROCEDIMIENTO
```
