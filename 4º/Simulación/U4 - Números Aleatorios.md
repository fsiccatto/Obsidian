# Generación de Números pseudoaleatorios
## Introducción

> [!info] Número aleatorio
> Un número aleatorio es un número obtenido al azar. Tiene la misma probabilidad de ser elegido y la elección de un número no depende de la elección de otro.

Los números aleatorios permiten a los modelos matemáticos representar la realidad.
En general cuando se requiere que determinados datos sean impredecibles se utilizan números aleatorios.

> [!abstract]  Números aleatorios
> Los números aleatorios son la base esencial de la simulación, ya que proporcionan la **variabilidad** necesaria para modelar situaciones reales y generar resultados diversos.
> La **calidad de los resultados** de una simulación depende en gran medida de la calidad de los números aleatorios generados. La precisión y la fiabilidad de los modelos simulados se ven afectadas por la aleatoriedad introducida mediante estos números.

## Definición de números pseudoaleatorios
Los **números pseudoaleatorios** son generados por medio de una **función determinista**, no aleatoria y aparentan ser aleatorios. Estos números pseudoaleatorios se generan a partir de un valor inicial aplicando iterativamente la función.

Tienen que tener las siguientes características:
- Que sean uniformemente distribuidos
- Estadísticamente independientes
- Reproducibles
- Periodo largo
- Generados de manera rápida
- Que no requiera gran capacidad de almacenamiento

## Usos y aplicaciones de números aleatorios
Se puede sintetizar alguna de las aplicaciones de números pseudoaleatorios para:
- Simular las entradas de aquellas variables aleatorias (no determinísticas).
- Juegos o teoría de decisiones.
- Cálculo numérico (por ejemplo en la resolución de integrales).
- Teoría del muestreo (aquellos casos en los que sea demasiado costoso realizar la muestra).
- Programación (generación de entradas para realizar las pruebas de los algoritmos y programas).
- Generadores de números aleatorios en lenguaje C, C++, Delphi o Java, utilizan métodos congruenciales. lineales (como se verá a continuación).
- Muestreo: con el fin de seleccionar una submuestra de una población.
- Programación: la generación de valores aleatorios puede ser útil para poner a prueba la efectividad de un algoritmo. También son útiles en criptología.

## Generación de números pseudoaleatorios
Para realizar una simulación se requieren números aleatorios en el intervalo (0,1), a los cuales se hará referencia como:
$$
r_{i}=\{ r_{1},r_{2},r_{3},\dots,r_{n} \}
$$
Consideramos los $r_{i}$ como números pseudoaleatorios generados por medio de algortimos determinísticos que requieren parámetros de arranque.

En principio consideraremos métodos para generar números con **distribución uniforme** en el intervalo $(0,1)$.  Podemos lograrlo generando enteros $x_{n}$ entre 0 y un número natural $m$ y luego tomando la fracción:
$$
r_{n}=\frac{x_{n}}{m}
$$
Para comprender porque un generador puede ser considerado mejor que otro es necesario saber cómo operan los mismos. El método más común es generar el siguiente número a partir de los últimos números generados:
$$
x_{n}=f(x_{n-1},x_{n-2},x_{n-3},\dots,x_{2},x_{1})
$$
> [!example] Ejemplo
> Podemos usar la función $x_{n}=(5x_{n-1}+1) mod 16$
> Se comienza con $x_{0} = 5$; los primeros 16 números diferentes generados a partir de esta semilla son: $10, 3, 0, 1, 6, 15, 12, 13, 2, 11, 8, 9, 14,7, 4, 5$. Si se continúa con el proceso de generación de números, se repite la secuencia.
> Las $x$ son enteros entre 0 y 15. Si se calcula $\frac{x}{16}$ se obtiene una secuencia de números aleatorios entre 0 y 1: $0.6250; 0.1875; 0,...$

Si se conoce la función f se puede generar la secuencia en cualquier momento a partir de un valor $x_{0}$ conocido.

> [!tip]
> El valor $x_{0}$ usado para comenzar la secuencia de números pseudoaletorios se llama **SEMILLA**.
> f es **DETERMINÍSTICA**.
> Dada la semilla se puede predecir con probabilidad 1 los números de la secuencia.

<mark style="background: #ADCCFFA6;">Sin embargo, los números son aleatorios en el sentido de que pasan pruebas estadísticas de aleatoriedad y por esto son llamados pseudoaleatorios.</mark>

## Generador Congruencia Lineal
El **generador congruencial lineal** genera una secuencia de números pseudo aleatorios en la cual el próximo número pseudo aleatorio es calculado a partir del último numero pseudoaleatorio generado. Es decir $x_{n+1}$ se deriva del numero $x_{n}$. 

Opera a través de una fórmula recursiva que produce secuencias de enteros que parecen ser aleatorias. El proceso implica multiplicar el número generado anteriormente por una constante $a$, sumarle otra constante $b$, y luego tomar el resto de la división de este resultado por un módulo $m$.

$$
x_{n+1}=(ax_{n}+b) \text{ mod } m, \qquad 0 \leq x_{n}<m \quad \forall n
$$
Se distinguen cuatro elementos
- $x_{0}$ valor semilla o inicial ($x_{0}>0$)
- $a$ elemento multiplicador ($0<a<m$)
- $b$ incremento o constante aditiva ($0\leq b<m$)
- $m$ módulo
![[img/congruencial lineal.png| center]]
Los generadores congruenciales lineales más populares son el **congruencial mixto** y el **congruencial multiplicativo**.

El número aleatorio $\mu_{i}$ para cada valor de $n$ es: $\mu_{i}=\frac{x_{i}}{m}$

> [!info]
> El **PERÍODO** es la subcadena de números $x_{i}$, dentro de la serie generada, en la que no hay repeticiones de números.
> La **LONGITUD DEL PERÍODO** es el número de elementos distintos en la subcadena.
> Cuando la longitud del período coincide con el módulo, se dice que el generador es de **CICLO COMPLETO**.

### Generador Congruencial Lineal Mixto
El incremento o constante aditiva $b\neq 0$.
$$
x_{n+1}=(ax_{n}+b) \text{ mod } m
$$
Ejemplo:
![[img/ejemplo congruencial mixto.png | center]]

Una cuestión de interés es cómo elegir los parámetros del generador de forma que este tenga ciclo completo. Para que el computo de $m$ sea eficiente, $m$ debe ser una potencia de $p{^d}$, $p$ es la base del sistema (decimal, binario, hexadecimal).

> [!important] Teorema de Hull y Dobell
> Un generador congruencial mixto tiene periodo completo si y sólo si se cumplen las siguientes condiciones:
> - $m \text{ y }b$ son primos entre sí
> - Si $q$ es un número primo que divide a $m$, entonces $q$ divide a $(a-1)$.
> - Si $4$ divide a $m$, entonces $4$ divide a $(a-1)$.
>   
> El teorema es fundamental para garantizar la aleatoriedad y la eficacia de los generadores congruenciales en la generación de números pseudoaleatorios.
> Ejemplo: ![[img/ejemplo 2 congruencial mixto.png| center]]

### Generador Congruencial Multiplicativo
$$
x_{n+1}=(ax_{n}) \text{ mod } m
$$
El incremento o constante aditiva $b = 0$.

Estos generadores presentan la ventaja de ser más rápidos al tener que realizar menos operaciones en el cálculo de los elementos. Sin embargo, la longitud de periodo que se alcanza son menores.

> [!info]
> Los generadores congruenciales multiplicativos **NO** producen secuencias de **CICLO COMPLETO**.

> [!important] Teorema de Hutchinson-Lehmer
> Sea t la longitud de un ciclo maximal igual a (m-1) de un generador congruencial multiplicativo, con módulo m primo. Se verifica:
> - $t=m-1$
> - $t$ es de longitud maximal si y sólo si $a$ es una raíz primitiva de $m$ si:
> 	- $a\neq 0$
> 	- No existe ningún factor primo $p$ de $(m-1)$ tal que: $1=a^{\frac{(m-1)}{p}} \text{ mod }m$

### Generador por Método Cuadrado Medio
El procedimiento consiste en que cada número de una sucesión es producido tomando los dígitos medios de un número obtenido mediante la elevación al cuadrado, de acuerdo al siguiente detalle:
1. Se define la semilla. 
2. Se eleva la semilla al cuadrado.
3. Se toma la parte central del número resultante. Si no es posible determinar la parte central, se completa el número agregando ceros al principio o al final. La cantidad de números que se extraen depende de la cantidad de dígitos que tendrá el número aleatorio. 
4. Para obtener números aleatorios entre 0 y 1, el resultado se debe normalizar. Si los números son de dos dígitos se normaliza dividiendo por $100$, si son de tres dígitos por $1000$ y así sucesivamente. Esto significa que el número obtenido en el paso anterior se divide por $10{^n}$, donde $n representa la cantidad de dígitos del número aleatorio. 
5. La parte central del número obtenido en el **paso 3** se transforma en la semilla. El procedimiento se repite, volviendo al **paso 2**.

Algunas desventajas del método: 
- Tiene una fuerte tendencia a degenerar a cero rápidamente. 
- Los números generados pueden repetirse cíclicamente después de una secuencia corta.
Ejemplo:
![[img/ejemplo cuadrado medio.png| center]]