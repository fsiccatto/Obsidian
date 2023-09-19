# Álgebra de Boole
Un sistema es un conjunto de elementos que guardan relación entre sí.
Un sistema digital es aquel cuyos elementos son digitales (solo pueden adoptar valores discretos).
### Postulados y Teoremas
Es útil definir la bivalencia, está compuesta por sólo dos elementos. El álgebra de Bool es un conjunto de elementos binarios relacionados entre sí mediante operaciones lógicas de producto y de suma, que cumplen con los postulados de Boole.

##### Identidad
$$
\begin{split}
    a + 0 &= a \\
	a.1 &= a
\end{split}
$$
##### Propiedad Conmutativa
$$
\begin{split}
    a + b &= b + a \\
	a.b &= b.a
\end{split}
$$
##### Propiedad Distribuitva
$$
\begin{split}
    a.(b + c) &= (a.b) + (b.c) \\
	a + (b.c) &= (a+b).(a+c)
\end{split}
$$
##### Complementación
$$
\begin{split}
    a + \overline{a} &= 1 \\
	a.\overline{a} &= 0
\end{split}
$$

#### Teoremas
##### 1- Dualidad
Toda igualdad lógica sigue siendo válida si se intercambian los operadores `+ y .` y los elementos de identidad `1 y 0`. La simetría de estos postulados demuestra este teorema.
##### 2- El álgebra es un conjunto cerrado
Los resultados de aplicar las operaciones lógicas a las variables, pertenecen al álgebra
##### 3- En el álgebra se cumple:
$$
\begin{split}
    a + 1 &= a \\
	a.0 &= 0
\end{split}
$$
##### 4- Ley de Idempotencia
$$
\begin{split}
    a + a &= a \\
	a.a &= a
\end{split}
$$
##### 5- Ley de Involución
$$
    a + \overline{\overline{a}} = a
$$
##### 6- Las operaciones lógicas son asociativas
$$
\begin{split}
    a + (b+c) &= (a+b)+c \\
	a.(b.c) &= (a.b).c
\end{split}
$$
##### 7- Absorción
$$
\begin{split}
    a &= a + (a.b) \\
	a &= a.(a+b)
\end{split}
$$
##### 8- Leyes de De Morgan
$$
\begin{split}
    \overline{a+b+c+\dots+n} = \overline{a}.\overline{b}.\overline{c}\dots\overline{n} \\
	\overline{a.b.c\dots n} = \overline{a}+\overline{b}+\overline{c}+\dots+\overline{n}
\end{split}
$$
### Compuertas Lógicas
![[Compuertas digitales.png|500|center]]
Existen compuertas de más de dos entradas. En función de la cantidad de compuertas por chip, se suele clasificar a los CI en escalas de integración:
- **SSI**, escala de integración pequeña, hasta 10 compuertas por CI.
- **MSI**, escala de integración media, de 10 a 100 compuertas por CI.
- **LSI**, escala de integración grande, de 100 a 1000 compuertas por CI.
- **VLSI**, escala de integración muy grande, más de 1000 compuertas por CI.
### Funciones Lógicas
Una función lógica es una variable binaria que depende de otras variables binarias relacionadas entre sí por las operaciones lógicas. Una función lógica se nota de la siguiente manera:
```
f(a, b, c, ..., n) = {expresión lógica que involucra a las variables a, b, c, ..., n}
```
La función adoptará el valor 0 o 1 de acuerdo a la expresión y al valor determinado de las variables.
#### Teoremas de Funciones Lógicas
En el álgebra de Boole se cumple:
$$
\begin{split}
    f(a, b, c, \dots, n) &= af(a, b, c, \dots, n) + \overline{a}f(a, b, c, \dots, n) \\
	f(a, b, c, \dots, n) &= [a+f(a, b, c, \dots, n)]\space[\overline{a}+f(a, b, c, \dots, n)]
\end{split}
$$
Este teorema posee corolarios útiles a la hora de simplificar funciones lógicas.
	[[Corolarios y Demostraciones#Corolarios de Teoremas de Funciones Lógicas]].
##### 9- Toda función lógica puede expresarse en forma canónica
- Como una **sumatoria** de términos en los cuales aparecen todas sus variables en forma de producto lógico (estos términos se llaman *MINTERMS*).
- Como una **productoria** de términos en los cuales aparecen todas sus variables en forma de suma lógica (estos términos se llaman *MAXTERMS*).
	[[Corolarios y Demostraciones#Demostación teorema 9]].
El covenio mencionado permite una tercer forma, llamada compacta:
$$
f(a, b,c, \dots, n) = \sum_{i=0}^{2^n-1} i f(i) = \prod_{i=0}^{2^n-1}(2^n-1-i)+f(i)
$$
Se deduce una regla para pasar de una función canónica en minterms a una en maxterms y viceversa: se buscan los términos canónicos que no están en la expresión de la función, y se los complementa a $`2^n-1`$. Estos son los términos de la función buscada.
### Minimización de Funciones Lógicas
La mínima expresión posible es la que tiene menor cantidad de términos y de variables por términos.
Es necesario que la función esté expresada en forma canónica. Toda función lógica es expresable en forma canónica, ya sea en minterms o maxterms.
#### Método de Simplificación de Karnaugh
Consiste en mapas aplicables a funciones de dos, tres, cuatro y cinco variables. Este método ==no resulta práctico para funciones de más de 5 variables==.
Los dos números binarios en las columnas y las filas, que siguen un código Gray de dos variables, se corresponden con las variables directas o negadas de cada cuadro, y los números decimales son los asignados a cada término canónico según la convención indicada con anterioridad.
![[Metodo Karnaugh.png|center]]
Formar un grupo entre dos unos colindantes en el mapa se corresponde con sacar factor común y perder la variable que cambia.
De lo visto, pueden enunciarse la siguiente regla de formación de grupos: 
1. Se agrupan la mayor cantidad de unos posible, siempre que sean una potencia de dos y el grupo resultante pueda subdividirse en grupos menores.
2. Se agrupan los unos restantes siguiendo la regla `1.` , pudiendo usar (si es conveniente) un uno ya agrupado anteriormente 
3. Se repite `2` hasta realizar todos los unos.
# Sistemas Digitales Combinacionales