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
    a.(b + c) &= (a.b) + (a.c) \\
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
![[Metodo Karnaugh.png|center|300]]
Formar un grupo entre dos unos colindantes en el mapa se corresponde con sacar factor común y perder la variable que cambia.
De lo visto, pueden enunciarse la siguiente regla de formación de grupos: 
1. Se agrupan la mayor cantidad de unos posible, siempre que sean una potencia de dos y el grupo resultante pueda subdividirse en grupos menores.
2. Se agrupan los unos restantes siguiendo la regla `1.` , pudiendo usar (si es conveniente) un uno ya agrupado anteriormente 
3. Se repite `2` hasta realizar todos los unos.
# Sistemas Combinacionales
## Sistemas Digitales
Un sistema digital es un conjunto de elementos binarios (compuertas digitales) relacionados entre sí.
Existen dos tipos de variables en un sistema digital:
- Variables de entrada:
	- Variables de proceso
	- Variables de control
- Variables de salida que dependen de las de entrada.
### Clasificación de Sistemas Digitales
Un sistema digital es *combinacional* cuando a cada combinación de las variables de entrada le corresponde **UNA Y SÓLO UNA** combinación de las variables de salida. Siempre que se repita un conjunto de valores de las variables de entrada, se repetirá la salida.
![[Sistemas combinacionales.png|center|300]]

Un sistema digital es *secuencial* cuando a un mismo vector de entrada le puede corresponder más de uno de salida. Estos sistemas deben poseer memoria interna, ya que sus salidas son consecuencias de la evolución anterior de sus entradas.
![[remote-repo/Arquitectura de Computadoras/imagenes/Sistemas secuenciales.png|center|300]]
## Sistemas Combinacionales
En un sistema combinacional las salidas no son otra cosa que funciones lógicas de las entradas. Se puede escribir que:
$$
z_{i} =f_{i}({x_{1}, x_{2}, \dots, x_{n}})
$$
![[Circuito Combinacional.png|center|300]]
### Circuitos Combinacionales MSI
Las técnicas de integración han permitido CI más complejos. Las ventajas son varias: disminución de los CI necesarios, del tiempo de diseño, del número de conexiones externas, y la facilidad de mantenimiento.
#### Codificadores
Permiten codificar las líneas de entrada. Generalmente lo hacen en binario o BCD. Tiene $`2^n`$ entradas y `n` salidas.
- Codificador sin prioridad: la salida debe calcularse como la función OR bit a bit de las salidas correspondientes a las entradas activadas
- Codificador con prioridad: la entrada de mayor prioridad es la que define la salida. Son para evitar errores.
Si ninguna entrada está activada las salidas son todas cero ($`D_{0}`$ está activada).
También cuentan con una entrada de habilitación.
![[Codificador.png|center|400]]
<small>Codificador binario de 8 entradas y 3 salidas</small>
#### Decodificadores
Poseen `n` entradas y `m` salidas que realizan lo opuesto a un codificador. Generalmente, son binarios o BCD. En el caso de un binario, si posee `n` entradas poseerá $`m = 2^n`$ salidas.
Los decodificadores, además de usarse para decodificar, son útiles para implementar funciones lógicas. Cada una de sus salidas es un minterm de una función de n variables.
![[Decodificador.png|400]]
#### Multiplexores
Disponen de $`m = 2^n`$ líneas de entradas (canales), una línea de salida y `n` líneas de selección. En función de las líneas de selección, se determina qué entrada aparece en la salida.
![[Multiplexor.png|200]]
#### Demultiplexores
Cumplen la función opuesta a los multiplexores. Tienen una entrada y `m` salidas, y `n` entradas de selección. La salida seleccionada tendrá el valor de la entrada.
El circuito de un demultiplexor es coincidente con un decodificador que posea entrada de habilitación. Por esta razón no se encuentran demultiplexores específicos.
![[Demultiplexor.png|center|400]]
#### Comparadores
Realizan la comparación entre dos números binarios de n bits. Poseen entradas por =, < y >. Permite realizar comparadores de elevado número de bits, partiendo de comparadores menores.
![[Comparador.png|400|center]]
#### Detectores/Generadores de paridad
Son CI capaces de generar/detectar la paridad de un conjunto de bits. Las señales de control TO (paridad impar) y TE (paridad par) permiten seleccionar la paridad.
![[Detector-Generador de paridad.png|400|center]]
#### Sumadores
Son CI que realizan la suma aritmética de dos números de n bits. Antes se debe estudiar la suma y resta binaria.
##### Semisumador
La idea es sumar números binarios, por lo que la mecánica es la suma y el excedente se acarrea.
![[Semisumador.png|center|300]]
##### Sumador Total
Se desea sumar dos números binarios A y B de 4 bits:
$$
\begin{split}
&-c_{4}c_{3}c_{2}c_{1}c_{0} \\
A&=a_{3}a_{2}a_{1}a_{0} \\
+ \\
B&=b_{3}b_{2}b_{1}b_{0} \\
--&----- \\
S&=s_{3}s_{2}s_{1}s_{0}
\end{split}
$$
Podemos observar que son necesario cuatro circuitos, uno para cada columna, y cada uno debe ser capaz de sumar tres bits: $`a_{i},\ b_{i} \ y \ c_{i}`$. Se implementa el circuito llamado sumador total.
La idea es:
![[Sumador.png|300]]

| Ci  | Bi  | Ai  | **Si** | Ci+1 |
|:---:|:---:|:---:|:------:|:----:|
|  0  |  0  |  0  | **0**  |  0   |
|  0  |  0  |  1  | **1**  |  0   |
|  0  |  1  |  0  | **1**  |  0   |
|  0  |  1  |  1  | **0**  |  1   |
|  1  |  0  |  0  | **1**  |  0   |
|  1  |  0  |  1  | **0**  |  1   |
|  1  |  1  |  0  | **0**  |  1   |
|  1  |  1  |  1  | **1**  |  1   |

![[Sumador Total.png|center|500]]
1. **Sumador con acarreo en serie**
	La salida de acarreo del sumador total correspondiente a los bits menos significativos (LSBs) puede conectarse a la entrada de acarreo del sumador total siguiente, y así sucesivamente.
	Tiene un tiempo de suma
	- TS = 4t aproximadamente.
	- t es el tiempo de suma de un sumador total.
2. **Sumador con acarreo en paralelo**
$$
	\begin{split}
C_{i+1}&=a_{i}b_{i} + (a_{i} + b_{i})c_{i} \\
G_{i} &= a_{i}b_{i} \rightarrow \text{Generador de acarreo} \\
P_{i} &= a_{i} + b_{i} \rightarrow \text{Propagador de acarreo}
\end{split}
$$
	En general cualquier acarreo puede expresarse $`C_{i+1} = f(G_{i}, P_{i}, c_{0})`$.
	Los acarreos dependen de los bits de entrada (ai y bi) y c0, y no de los acarreos anteriores
##### Resta Binaria
Se pueden restar dos números realizando la suma de uno de ellos más el complemento del otro.
Sean `A` y `B` dos números binarios signados en convenio de complemento a dos:
	$`A - B = A + C_{2}(B) = A + 2^n - B = 2^n + (A - B) `$ 
	Se observa que el resultado obtenido difiere del buscado en el valor $`2^n`$.
	Por lo que se debe interpretar:
	- Si (A - B) es positivo, el complemento debe despreciarse.
	- Si (A - B) es negativo, el resultado estará expresado en complemento a dos.
	![[Restador complemento a dos.png|center|500]]

Sean `A` y `B` dos números binarios signados en convenio de complemento a uno:
	$`A - B = A + C_{1}(B) = A + 2^n - 1 - B = 2^n + (A - B) - 1`$.
	Por lo que se debe interpretar:
	- Si (A - B) es positivo, el complemento debe despreciarse.
	- Si (A - B) es negativo, el resultado estará expresado en complemento a uno.
	![[Restador complemento a uno.png|center|500]]
##### ALU (Unidad Aritmética Lógica)
Permiten realizar operaciones lógicas y aritméticas sobre números binarios (generalmente de 4 bits). La operación a realizar se selecciona colocando los valores adecuados en las líneas de selección.
Estos bloques funcionales pueden conectarse en cascada para realizar operaciones sobre números de mayor número de bits.
- Las salidas P y G son las funciones Propagadora y Generadora de acarreos. Se usan para mejorar el tiempo de procesamiento.
![[ALU.png|center|500]]
# Sistemas Secuenciales
Son aquellos sistemas digitales cuyas salidas no sólo dependen de sus entradas en un momento dado, sino también de cómo han evolucionado estas anteriormente.
El sistema secuencial tiene que ser capaz de memorizar la mencionada evolución, es decir, que las salidas dependen de las entradas y de ellas mismas.
==Un Sistema Secuencial parte de un Sistema Combinacional REALIMENTADO.==
![[Sistemas Secuenciales|center|700]]
Se observa un nuevo tipo de variables llamadas **variables internas**. El bloque M es un circuito capaz de mantener el estado de sus entradas en su valor, por un tiempo. 
Para un valor dado de las variables de entrada, se inicia un proceso, llamado evolución automática del sistema, hasta que se alcanza un estado estable.
Si las variables internas se las deja pasar de izquierda a derecha sólo en ciertos momentos, se obtienen un Sistema Secuencial Síncrono.
### Biestables
Poseen dos estados estables, es decir, que las variables internas pueden adoptar en este caso dos estados en los cuales permancerán indefinidamente a menos que cambien las variables de entrada. Los Biestables representan los circuitos base para la construcción de secuenciales más complejos.
![[Biestables|center|400]]
#### Biestables Asíncronos
Son aquellos en los cuales las entradas actúan directamente sobre el biestable. Biestables SR.
![[Secuenciales#Asíncronos#Biestable Asíncrono SR]]
#### Biestables Síncronos
Estos biestables cuentan con una entrada adicional: la entrada del reloj (sincronismo).
![[Secuenciales#Síncronos]]
### Aplicaciones de los Biestables
Los biestables son capaces de memorizar un bit. Existen para:
- Memorias electrónicas
- Registros
- Contadores
#### Registros de desplazamiento
Es un sistema secuencial síncrono que almacena varios bits de información. El formato de la información puede ser de dos tipos: **serie** o **paralelo**. Se pueden clasificar en:
1. Registros de Desplazamiento
	- Entrada serie, salida serie
	- Entrada serie, salida paralela
	- Entrada paralela, salida serie
2. Registros propiamente dichos
	- Entrada paralela, salida paralela
##### Registros de desplazamiento
| serie - serie | paralelo - serie |
| ------------- | ------------------ |
|    ![[Registro serie-serie.png]]           |      ![[Registro paralelo-serie.png]]              |
##### Registros propiamente dichos
Consisten en un conjunto de biestables sincronizados por nivel o por flancos, cuyas entradas de sincronismo se encuentran unidas (paralelo). Uso extensivo en cualquier sistema digital.
Se presenta una forma de interconexión entre registros llamada BUS COMÚN. Se trata de tres registros de dos bits cada uno.
![[Interconexion de registros por BUS.png|300|center]]
### Contadores
Es un sistema secuencial formado por biestables y lógica combinacional, capaz de almacenar en binario u otro código, la cantidad de impulsos recibidos por su entrada de cuenta. Puede aplicarse como divisor de frecuencia, control de tiempos, generador de direcciones en sistemas de memoria, secuenciador en unidades de control, etc.

|                                                                                                                           Contadores Asíncronos                                                                                                                            |                                                                       Contadores Síncronos                                                                        |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Son secuenciales **síncronos** formados por un conjunto de biestables síncronos por flancos. Asíncrono se refiere a que las entradas de sincronimos de sus biestables no están unidas entre sí. La salida de un biestable sirve como entrada de sincronismo del siguiente. | Son similares a los anteriores, sólo que comparten la misma señal de reloj. Son más rápidos y complejos que los asíncronos. Tiene más compuertas que el anterior. |
| ![[Contador Asíncrono.png]]                                                                                                                                                                                                                                                                          |                                                                                                                                                                   ![[Contador Síncrono.png]]|
El diseño de contadores se realiza planteando una tabla de verdad temporal, y luego de obtener las funciones correspondientes, se minimizan teniendo en cuenta el biestable elegido. Los biestables utilizados en los contadores, como así también en los registros de desplazamiento, son biestables síncrono maestro – esclavo o activados por flancos.