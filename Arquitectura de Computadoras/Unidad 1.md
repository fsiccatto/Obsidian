# Representación Numérica
## Sistemas de Numeración
Toda combinación de operaciones fundamentales efectuadas con números cualesquiera que da origen a un nuevo número, se llama **algoritmo de numeración**. Para los sistemas de numeración basados en el valor relativo (posicionales), el algoritmo de numeración consiste en un polinomio:
$$
N=a_nb^n+a_{n-1}b^{n-1}+a_{n-2}b^{n-2}+...+a_0b^0+a_{k-1}b^{k-2}+a_{k-2}b^{k-2}+...+a_{-k}b^{-k}\\
$$
Dónde: 
	N: Número 
	ai: número natural menor que b (símbolo) 
	b: base del sistema (cantidad de símbolos diferentes del sistema, es un número natural mayor que 1) 
	n + 1: cantidad de cifras enteras. 
	k: cantidad de cifras fraccionarias.

Un sistema numérico está formado por:
- Un conjunto finito y no vacío de símbolos
- Un conjunto de reglas para formar los símbolos numerales
- Un conjunto de reglas para operar entre los numerales
#### Clasificación de los sistemas numéricos
- ##### Sistemas numéricos no posicionales
	El valor está determinado po el símbolo. Ejemplo: números romanos y egipcios.
- ##### Sistemas numéricos posicionales
	Cada símbolo o dígito tiene un *peso* distinto según la posición que ocupa en la cifra.
	**Caracterísitcas**:
	- Consta de un número finito de símbolos distintos que constituyen su base
	- Cada símbolo aislado representa un número específico de unidades
	- Existe un símbolo para indicar la ausencia de elementos (como el cero)
	- Los símbolos pueden ordenarse de forma monótona creciente
	- El valor del dígito depende de la posición en la que se encuentre el número
	- La posición extrema derecha corresponde a unidades (peso 1)
###### Sistema Decimal
Sistema de numeración posicional de base 10: $`D_{10} = \{0, 1, 2, 3, ..., 9\} `$
###### Sistema Binario
Sistema de numeración posicional de base 2: $`B_{2} = \{0, 1\}`$
###### Sistema Octal
Sistema de numeración posicional de base 8: $`O_{8} = \{0, 1, 2, 3, ..., 7\} `$
###### Sistema Binario
Sistema de numeración posicional de base 16: $`H_{16} = \{0, 1, 2, 3, ..., 9, A, B, C, D, E, F\} `$
#### Conversión entre números de distintas bases
![[Conversiones entre sistemas|1200|center]]
### Sistema Binario
Es el que se utiliza en las computadoras, debido a que trabajan internamente con dos niveles de voltaje, por lo cual su sistema de numeración natural es el sistema binario.
	Un **bit** es un dígito binario. Un **nibble** es un grupo de 4 bits. Un **byte** es un grupo de 8 bits.
Los sistemas *octal* y *hexadecimal* permiten compactar bits, de modo de hacer más sencilla la tarea de reconocerlos a simple vista. Estos sistemas son utilizados para analizar los contenidos de los registros internos de la computadora.
## Punto Fijo y Punto Flotante
##### Complemento a 1 o a la base
El complemento a la base de un número `N` que posee `m` cifras enteras, se define como:
$$
C_b(N) = b^m - N
$$
Podemos observar que el complemento a 1 puede obtenerse **cambiando ceros por unos y viceversa**.
##### Complemento a 2 o a la base disminuida
El complemento a la base disminuida de un número `N` que posee `m` cifras enteras, se define como:
$$
C_{b-1}(N) = b^m - N - 2^{-k}
$$
donde `k` es la cantidad de cifras fraccionarias.
El complemento a 2 puede obtenerse **cambiando unos por ceros y viceversa, y sumando uno**.
### Punto Fijo
El punto fijo nos permite representar números con uno, dos, tres o más dígitos fraccionarios. Por ejemplo:
$$
	1101001,101
$$
En este caso disponemos de 10 bits para representar el número, de los cuales 7 son enteros y 3 decimales.
### Punto Flotante
Cuando queremos representar números muy pequeños o muy grandes utilizamos la notación de punto flotante. Es muy similar a la notación científica, divide al número en tres campos
![[Punto Flotante|800|center]]
1. Signo de la Mantisa (S)
	Es un campo de 1 bit.
	- 0 positivo (+)
	- 1 negativo (-)

2. Exponente (E)
	Es un campo de varios bits con la **Convención Exceso $`2^{n-1}`$**. Por ejemplo, el exceso 64 usa 7 bits y el exceso 128 require 8 bits

3. Mantisa (M)
	Es un campo de varios bits fraccionarios. Para que el número esté *normalizado*, el bit más significativo debe ser 1, es decir
$$
\frac{1}{b}\leq M < 1
$$
#### Operaciones Aritméticas
1. Multiplicación
	El producto de los dos números será $`S_pE_pM_p`$, donde:
	   - Signo de la mantisa
		$`S_p = 0, si \ S_1 = S_2  -- S_p = 1, si \ S_1 \neq S_2`$
	   - Exponente
		$`E_p = E_1 + E_2 - 64 - K,`$
		Donde `K` es el valor que satisface $`\frac{1}{2}\leq M_1 x M_2 x 2^K < 1`$
	   - Mantisa
		$`M_p = M_1 x M_2 x 2^K`$
2. División
	La división de los dos números será $`S_dE_dM_d`$, donde:
	   - Signo de la mantisa
		$`S_d = 0, si \ S_1 = S_2  -- S_d = 1, si \ S_1 \neq S_2`$
	   - Exponente
		$`E_d = E_1 + E_2 - 64 - K,`$
		Donde `K` es el valor que satisface $`\frac{1}{2}\leq \frac{M_1}{M_2} 2^K < 1`$
	   - Mantisa
		$`M_d = \frac{M_1}{M_2} 2^K`$
3. Suma y Resta
	Para sumar o restar los dos número deben igualar sus exponentes. Supongamos
		$`E_1 > E_2`$
	Entonces `j`, tal que
		$`j = E_1 - E_2`$
	Modificamos $`S_2E_2M_2`$ a fin de igualar los exponentes:
		$`S_2(E_2 + j)\frac{M_2}{2^j}`$
	Luego, procedemos a sumar o restar las mantisas según sea el caso. El resultado debe ser *normalizado*.
### Norma IEEE 754
- Establece tres tipos de representaciones
	![[Punto Flotante IEEE 754.png|500|center]]
- Los exponentes mínimo y máximo se utilizan para casos especiales
- Se consideran 5 clases de números
	![[Casos especiales Punto Flotante.png|center]]
## Códigos
Un #código es una representación biunívoca de algún conjunto de elementos de tal forma que, a cada uno de estos, se le asigna una combinación de símbolos dterminados y viceversa.
Para "comunicarse" hay que conocer el código utilizado.
![[Codigos|center|600]]
### Códigos Binarios
Son los códigos utilizados por sistemas decimales.
###### Códigos Binarios Continuos:
Son aquellos donde las combinaciones correspondientes a números decimales consecutivos son **adyacentes**. Se llaman combinaciones binarias adyacentes a las que difieren solamente de un bit.
###### Códigos Binarios Cíclicos
Son aquellos códigos continuos donde la última combinación es adyacente a la primera.

| Decimal | Continuo | Cíclico |
| :-------: | :--------: |:-------:|
| 0       | 0000     |  **0000**   |
| 1       | 0001     |  0001   |
| 2       | 0011     |  *0011*   |
| 3       | 0111     |  *0111*   |
| 4       | 0110     |  1111   |
| 5       | 1110     |  1110   |
| 6       | 1111     |  1100   |
| 7       | 1110     |  **1000**   |
Entre dos combinaciones seguidas cambia un solo bit. Entre la primera y la última cambia un solo bit.

El ejemplo más típico de un código continuo y cíclico es el llamado **Código de Gray**. Se utiliza en convertidores muy rápidos y en codificadores, ya que solo cambia un bit.
![[Códigos#Gray]]
Representación del Código de Gray de 2, 3 y 4 bits
Otro ejemplo de código binario continuo y cíclico es el de Johnson:
![[Códigos#Johnson]]
### Códigos BCD
La conversión de binaria a decimal es difícil. En las calculadoras, juegos digitales, instrumentos digitales; en los que es común la entrada y salida de números en notación decimal, se emplea un código *BCD decimal codificado en binario*.
Permiten la representación de números decimales (0 al 9) en bloques de **4 bits**.
Se clasifican en:
- <ins>Ponderados</ins>: adjudican cierto peso a los 1 binarios, según la posición que ocupan en el bloque, por lo que se debe verificar que la suma de los pesos de cada combinación sea igual al número decimal representado.
- <ins>Libres</ins>: no existen "pesos" ni sumas algebraicas, por ejemplo en BCD Exceso 3 parte del BCD Natural y suma 3 a cada combinación.
Esta codificación especial nos permite realizar operaciones aritméticas de números decimales sin perder la precisión como en las conversiones de decimal a binario puro y de binario a decimal. Sin embargo, los cálculos llevan más timepo y son un poco más complicados.
![[Códigos#BCD]]
La conversión se realiza expresando cada dígito mediante la combinación binaria dependiendo del código especificado.
### Códigos Alfanuméricos
Muchas aplicaciones requieren manejar datos que sean letras o caracteres. Consiste en un grupo de elementos consistente de los diez números decumales, 26 caracteres del alfabeto y de cierto símbolos especiales.
El código **ASCII** (*American Standard Code for Information Interchange* = Código normalizado americano para el intercambio de información) es el más conocido.
![[Códigos#ASCII]]
Es el estándar de 7 bits. El extendido es de 8 bits.
## Códigos Detectores y Correctores de Error
Debe existir un formato para los datos y una estrategia de sincronización de cómo se envían y reciben los mensajes, incluyendo la detección y corrección de los errores.
![[Enlace de Datos|center|500]]
- DTE: Equipo Terminal de Datos
- DCE: Equipo de Comunicación de Datos
En general, el mensaje tiene la siguiente estructura:
![[Estructura general de un mensaje de un protocolo|center|400]]
Si se detecta la presencia de errores (por ruido) en la información es necesario volver a mandarla. Para poder detectar y/o corregir errores se da el concepto de distancia entre combinaciones de un código:
	**Distancia** entre dos combinaciones binarias cualesquiera de un código es el número de bits que deben cambiarse para pasar de una combinación a la otra.
### Distancia Mínima
La distancia mínima $`D_m`$ de un código es la menor de las distancias entre dos combinaciones cualesquiera.
Para detección de errores es necesario que $`D_m > 1`$. Nos permite deducir que:
$$ 	
\begin{split}
	CantErroresDetectables + 1 &= D_m \\
	(CantErroresCorregibles * 2) + 1 &= D_m
\end{split}
$$
### Código Detectores de Error
La manera más simble de lograrlo es agregar un **bit de paridad**, puede ser par o impar. Por lo que al mensaje se le agregará un bit adicional, dejando un *código de pardidad* en el que es necesario ponerse de acuerdo en qué convención se trabaja.
Por lo tanto, la detección de errores consiste en comprobar si el número de unos de cada combinación cumple con el bit de paridad. Si existe un error, se deberá solicitar una nueva transmisión del dato.
Algunos códigos de detección de errores que encontramos son el 2 entre 5 y el biquinario.
![[Códigos#Detectores de Errores]]
Tienen dos unos en cada combinación (paridad par) y se forman de acuerdo a los pesos asignados.
### Códigos Correctores de Errores
Un código corrector detecta si la información codificada presenta o no errores, y en caso afirmativo determina la posición del bit o bits erróneos, de manera de poder corregirlos por inversión.
Los códigos con $`D_m > 2`$ son códigos detectores de error.
#### Código de Hamming
Su formación parte de un código cualquiera de `n` bits al que se le adicionan `p` bits formando un nuevo código de `n + p` bits. En este código se realizan p detecciones de paridad, obteniéndose un bit de paridad uno o cero (dependiendo si el número de bits es impar o par). El conjunto de los p bits de paridad forma un número en el sistema binario natural cuyo equivalente decimal nos indica la posición del bit erróneo. Si no hay error, el número obtenido debe ser cero.
Se debe cumplir que: 
$$
2^p \geq n + p + 1
$$
Para detectar los siete posibles errores que se pueden producir en una combinación (7 errores considerando 7 posiciones en cada combinación) y la ausencia de error, son necesarias ocho combinaciones binarias correctoras de error. Dichas combinaciones correctoras de error se obtienen mediante 3 bits (*c1*, *c2* y *c3*), y el número decimal formado por ellos indica la posición del bit erróneo.
![[Códigos#Correctores de Errores#Hamming#Tabla Correctora]]
Podemos deducir que *c1* es 1 si el número de unos en las posiciones dadas es impar, y 0 en el caso contrario. Entonces:
$$ 
	\begin{split}
	c_1 = b_1 \oplus b_3 \oplus b_5 \oplus b_7 \\
	c_2 = b_2 \oplus b_3 \oplus b_6 \oplus b_7 \\ 
	c_3 = b_4 \oplus b_5 \oplus b_6 \oplus b_7
	\end{split}
$$
Podemos sacar $`b_1, b_2 \space y \space b_4`$ ya que aparecen una sola vez y pueden generarse a partir de los otros, por ejemplo `b1` debe valer uno si el número $`b_3, b_5 \space y \space b_7`$ es impar, por lo tanto:
$$
\begin{split}
	b_1 = b_3 \oplus b_5 \oplus b_7 \\
	b_2 = b_3 \oplus b_6 \oplus b_7 \\
	b_3 = b_5 \oplus b_6 \oplus b_7 
\end{split}
$$
![[Códigos#Código Hamming]]
### Verificación de Redundancia de LRC y CRC
La utilización de códigos cíclicos, que nos aquellos que al realizar una rotación cíclica de una palabra se produce otra palabra que pertenece al mismo código.
#### Verificación de Redundancia Longitudinal (LRC)
Es un código detector de error de un bit. Utilizado en la adquisición de datos y control en la industria, para la comunicación entre dispositivos y con una PC.
El cálculo del LRC consiste en realizar la suma hexadecimal de los datos y calcular el complemento a 2.
#### Verificación de Redundancia Cíclica (CRC)
En estos códigos se agregan `k` bits a un mensaje a transmitir de `m` bits. La condición que se cumple es que `m >>> k`, de esta forma se obtiene una transmisión eficiente ya que la cantidad de bits agregados es pequeña. La utilización de estos códigos permite la detección y corrección de errores.
La forma de obtener los `k` bits es mediante una procedimiento de redundancia cíclica implementado con Registros de Desplazamientos y compuertas XOR, fundamentado en una aritmética binaria sin acarreos (no se consideran).
- M: mensaje a transmitir de `m0` bits.
- `k`: cantidad de bits a agregar (FCS - *Frame Check Security*)
El transmisor, antes de transmitir, procesa el mensaje a transmitir M:
$$
	\frac{M * 2^k}{G(x)} = C + \frac{FCS}{G(x)}
$$
- Observe que el FCS es el resto de la división y tendrá `k` bits ya que G(x) tiene `k+1` bits.
- G(x): es un patrón de k + 1 bits, obtenido a partir de un polinomio de numeración de k+1 términos enteros. Además, cumple con que el bit más significativo y el menos significativo (MSB y LSB) son uno (1). Estos G(x) están normalizados y dependiendo cuál se usa, resultan CRC que permiten corregir más o menos bits.
- El transmisor envía $`M * 2^k + FCS`$.
El receptor, recibe y procesa lo recibido:
$$
\frac{M*2^k+FCS}{G(x)} = \frac{M*2^k}{G(x)} + \frac{FCS}{G(x)} = C + \frac{FCS}{G(x)} + \frac{FCS}{G(x)}
$$
Si no hubo error FCS + FCS debería ser 0.
En caso de que no sea 0, ha habido un error en la transmisión. Para corregir el error, el receptor debe realizar un procesamiento de lo recibido. Puede ser por software o hardware.
### Códigos Bidimensionales
La utilización de estos códigos implica la transferencia de un bloque de información organizada en dos dimensiones. El transmisor organiza esta estructura bidimensional y le agrega bits adicionales. El receptor recibe la información más los bits adicionales, los procesa, detecta y corrige los errores.
![[Códigos#Correctores de Errores#Códigos Bidimensionales]]
## Encriptación o Cifrado
Es necesario la necesidad para proteger los archivos y otras informaciones almacenadas en su memoria.
El texto plano es cifrado sometiéndolo a un algoritmo de cifrado, cuyas entradas son el texto plano y la clave de cifrado, y a la salida de este algoritmo (la forma cifrada del texto plano) se le llama texto cifrado. El texto cifrado debe ser inteligible[^1] para cualquiera que posea la clave de cifrado.
Existen dos técnicas diferenciadas que pueden utilizar los algoritmos: **la sustitución** y **la permutación**. 
###### La sustitución
	Es uno de los enfoques básicos del cifrado, como se practica tradicionalmente, donde se usa una clave de cifrado para determinar, para cada caracter del texto plano, un caracter de texto cifrado que va a sustituir a ese carácter. 
###### La permutación 
	Los caracteres de texto plano son simplemente reorganizados en una secuencia diferente, bajo la influencia de la clave de cifrado.

Ninguna de las técnicas de sustitución y permutación es particularmente segura en sí misma, pero los algoritmos que combinan a las dos pueden proporcionar un alto grado de seguridad
## Otros Códigos
### Códigos de Barra
### Códigos QR

[^1]: Inteligible: Que puede ser comprendido o entendido.
