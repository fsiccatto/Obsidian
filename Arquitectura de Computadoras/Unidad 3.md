# Memorias Electrónicas
Son los dispositivos de almacenamiento de datos e instrucciones en una computadora. Llamamos sistema de memoria al conjunto de estos dispositivos y los algoritmos de hardware y/o software de control de los mismos.
![[Circuito básico de memorias.png|200]]
Clasificación funcional de las memorias: 
1. Memoria interna: consituida por los registros internos de la CPU.
2. Memoria central: almacena programas y datos.
3. Memoria secundaria: se usa para almacenamiento de programas del sistema y grandes archivos.
Se pueden definir algunos parámetros generales aplicables a todas las memorias:
1) Unidad de almacenamiento: bit.
2) Capacidad de almacenamiento: cantitad de bits que puede almacenarse. 1Kb = 1024 bytes.
3) Tiempo de acceso (`ta`): es lo que tarda en leer o escribir una palabra en la memoria desde el momento que se direcciona.
4) Tipo de acceso:
	- Acceso aleatorio
	- Acceso serie
5) Tiempo de ciclo (`tc`): mínimo tiempo entre dos accesos sucesivos a la memoria. tc > ta.
6) Medio físico
	- Electrónicas
	- Magnéticas
	- Ópticas
7) Estabilidad
   - Volatilidad: el contenido de la memoria se pierde cuando se saca la alimentación eléctrica.
   - Almacenamiento dinámico: la información se pierde cuando el capacitor se descarga, es necesario un refresco periódico para restaurar el contenido antes que se deteriore.
   - Lectura destructiva (DRO): se pierde información al efectuar la lectura, debe acompañarse de una restauración.
## Clasificación de las Memorias Electrónicas
Las memorias electrónicas pueden considerarse como un sistema digital mixto (combinacional y secuencial) capaz de almacenar información binaria que se puede acceder (introducir o extraer información) sólo parcialmente en un momento dado.
En función del tipo de acceso, estas memorias se clasifican en:
1. **Memorias de acceso aleatorio** (*RAM*) en las que `ta` es similar para cualquier posición.
	- Memorias de lectura/escritura. Se caracterizan por tener los `ta` de lectura y escritura similares, presentan volatilidad, pierden su contenido cuando dejan de estar alimentadas.
		- Memorias estáticas (SRAM)
		- Memorias dinámicas (DRAM)
	- Memorias sólo lectura (*ROM*). Se caracterizan por tener el `ta` de escritura mucho mayor que el de lectura, no presentan volatidad, no pierden su contenido sin alimentación. Se subdividen:
		- ROM
		- PROM
		- EPROM
		- EEPROM
		- FLASH
2. **Memorias de acceso serie** en las que `ta` depende de la posición de la palabra dentro de la memoria. Son memorias de lectura/escritura. Se subdividen en:
	- Registros de desplazamiento
	- Memorias pila (LIFO), última escritura, primera lectura
	- Memorias cola (FIFO), primera escritura, primera lectura
## Memorias RAM
Podemos considerar la memoria como un conjunto de posiciones, donde cada una de ellas está formada por una o más celdas (dependen de la memoria y la tecnología utilizada).
![[RAM|center]]
Las memorias RAM operan de la siguiente manera:
- Una dirección (conjunto de `m` bits) se transfiere el registro de direcciones,
- El decodificador de direcciones procesa la dirección y selecciona una posición de memoria,
- La posición seleccionada se lee o escribe en función de las señales de control,
- Si es una *lectura*, el contenido de la posición seleccionada se transfiere al registro de datos de la salida (`n` bits). Si es *escritura*, se transfiere del registro de datos de entrada a la posición seleccionada.

La organización interna puede ser 2D o 3D:

| Organización 2D                                                                                                                                                                                                                                      | Organización 3D |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| Las celdas se organizan en una matriz de dos dimensiones, las que las filas vienen dadas por el número de palabras (N) y las columnas por la longitud (cantidad de bits) de cada palabra. Cada celda binaria accede por una sola línea de selección. |     Cada celda binaria se accede por dos líneas de selección. La activación simultánea de ambas determina la selección de la celda.            |
| ![[RAM 2D.png]]                                                                                                                                                                                                                                                     |       ![[RAM 3D.png]]          |

Cantidad de líneas de un decodificador en organizaciones:
- 2D: $`LS2D = 2^m \text{, donde m es la cantidad de líneas de direccionamiento}`$.
- 3D: $`LS3D = 2. 2^\frac{m}{2} \text{, considerando los dos decodificadores iguales}`$.
La reducción de la complejidad del decodificador y del retardo que introduce se logra a costa de **agregar un decodificador y una compuerta AND por cada palabra**.
### Memorias RAM de Lectura/Escritura
#### Memorias de Lectura/Escritura Estáticas
El elemento básico de estas memorias consiste en un biestable asíncrono y algunas compuertas adicionales para manejar la selección y el control de la celda.

| Celda básica 2D                                                                                                                                                                                                                                                                                                                     | Celda básica 3D                                                                 |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| Cuando la línea de selección está activa con un 1 lógico, se habilita la celda para lectura/escritura. Si L/E’ = 1 se trata de una operación de lectura, y las entradas al biestable se bloquean y se habilita la compuerta AND de salida. Si L/E’ = 0, se bloquea la compuerta AND de salida y se habilita la entrada al biestable | Se observa que hay una compuerta AND de dos entradas que completa la selección. |
| ![[Celda 2D.png]]                                                                                                                                                                                                                                                                                                                   | ![[Celda 3D.png]]                                                               |

RAM de lectura/escritura con organización interna 2D de 16 palabras de 4 bits.
![[RAM 2D 16 palabras 4 bits.png|400]]
Líneas de acceso externas a la memoria:
1. *Líneas de direccionamiento A0:A3* (Bus de Direcciones): 4 líneas unidireccionales para la selección de la palabra a acceder.
2. *Líneas de datos I/O0:I/O3* (Bus de Datos): 4 líneas bidireccionales que pueden actura como entradas o salidas. Para lograrlo se usan buffe triestado (así evitamos usar líneas independientes).
3. *Señal de control de lectura/escritura* (L/E')
	- Si L/E' = 1 se lee la memoria.
	- Si L/E' = 0 se escribe la memoria.
4. *Señales de control*:
	- Si C/S’ = 1 las líneas de datos se colocan en alta impedancia. 
	- Si C/S’ = 0 y L/E’ = 0 las líneas de datos externas se conectan a las líneas de datos de entrada interiores, y las líneas de datos de salida interiores se colocan en alta impedancia.
	- Si C/S’ = 0 y L/E’ = 1 las líneas de datos externas se conectan a las líneas de datos de salida interiores, y las líneas de datos de entrada interiores se colocan en alta impedancia.
	- Si O/E’ = 1 se deshabilitan los circuitos de salida de la memoria sin tener en cuenta el estado de las señales C/S’ y L/E’.

##### Ciclo de lectura y ciclo de escritura
Para una correcta operación de la memoria se necesita una temporización adecuada de las señales aplicadas a sus líneas. Cada memoria tiene su propia temporización, el fabricante provee los diagramas de tiempo de señales.

| CE' | R/W' | Accion                 |
| --- | ---- | ---------------------- |
| 0   | 1    | Operación de lectura   |
| 1   | 0    | Operación de escritura |
| 1   | X    | Memoria deshabilitada. Alta impedancia.                       |
#### Memorias de Lectura/Escritura Dinámicas
DRAM. En estas memorias la celda básica consiste en la capacidad parásita de una compuerta de un transistor MOSFET y los circuitos asociados de control. Puesto que debido a las pérdidas inevitables el capacitor se descarga, es necesario restaurar periódicamente la información mediante un proceso que se llama *refresco*. Este refresco consiste en una lectura seguida de una escritura automática cada aproximadamente 2ms (dependiendo de la memoria). Cuando está actuando el proceso de refresco, no es posible acceder a la memoria. La velocidad de estas memorias en menor que las estáticas, sin embargo la densidad de integración en apreciablemente mayor.
La estructura interna de estas memorias es generalmente 3D, con el mismo número de filas y columnas.
![[DRAM.png|300]]
Si bien estas memorias son más lentas que las estáticas, poseen una característica interesante. En muchos casos es necesario leer o escribir direcciones consecutivas de memoria.
### Memorias RAM de sólo Lectura (ROM)
Estas memorias una vez programadas sólo realizan operaciones de lectura. No son volátiles, y pueden utilizarse para almacenar códigos, en generadores de caracteres, en funciones aritméticas complejas, en unidades de control microprogramadas, o en almacenamiento de partes del sistema operativo (BIOS). La organización interna es parecida a la RAM.
#### Memorias ROM
Se usan diodos y transistores para su construcción. Los diodos se utilizan como elementos acopladores. La conexión de varios diodos a una misma línea implementa la función OR de las señales de entrada. Puede decirse que una ROM de $`2^n \ x \ m \text{ bits}`$, podría realizar cualquier combinacional de n variables de entrada y m funciones.
![[Memorias ROM.png|300]]
La salida del bus de datos son triestados para permitir la conexión de más de una memoria a un bus común.
#### Memorias PROM
Los elementos de conexión son diodos o transistores con un fusible en serie. Inicialmente la memoria presenta todas las conexiones establecidas. La programación consiste en destruir el fusible en aquellos lugares donde quiere almacenarse un 0. Esto se consigue direccionando la palabra deseada e inyectando una corriente adecuada en las salidas, así la conexión queda abierta y es como si no existiera el elemento acoplador. Se deduce que **una vez programada la memoria ya no es posible volver a hacerlo**.
#### Memorias RPROM
Las RPROM pueden ser reescritas por el usuario. Existen tres tipos:
- EPROM: constituidas por celdas de MOSFET's. La descarga es por luz ultravioleta y la repogramación es eléctrica aplicando tensiones superiores a las de funcionamiento, es parmanente hasta que vuelva a grabarse.
- EEPROM: similares a la anterior, pero el borrado es posición a posición.
- FLASH: similares a las anteriores, pero el borrado se realiza simultáneamente en todas las posiciones.
### Extensión de Longitud de palabra y capacidad
Es posible aumentar la capacidad de una memoria partiendo de circuitos integrados de menor capacidad. Esto puede lograrse aumentando la longitud de palabra o la cantidad de las mismas.
#### Extensión de la longitud de palabra
Memoria de `N` palabras de `k.m` bits, partiendo de un CI de `N` palabras de `m` bits. Las líneas de dirección y de control son compartidas por todos los CI. Las líneas de datos se amplían de m a `k.m` bits.
![[Extension de la longitud de palabra.png|300]]
#### Extensión del número de palabras
memoria de 2kN palabras de m bits, partiendo de un CI de N palabras de m bits. De las p + k líneas de dirección necesarias, p se interconectan a todos los CI a fin de seleccionar una de las N (2p) palabras en cada CI. El resto de las k líneas de dirección se inyectan a un decodificador cuyas salidas se conectan a las líneas de selección (CS) de cada CI. La señal de W/R’ es común para todos los CI. El bus de datos es común para todos los CI. Esto es posible gracias a la tecnología triestados de los CI. Para ampliar la longitud de palabra y la cantidad de las mismas, se suman las técnicas indicadas.
![[Extension del numero de palabras.png|300]]
Finalmente, si disponemos de memorias RAM de N palabras de m bits y pretendemos una memoria de `N’` palabras de `h` x `m` bits, se procede como sigue: 
- Se calcula el número de Chips, donde: Número de Cls = Entero `[N’/N]` x h
- Se calcula el decodificador de k entradas, donde: 2k >= Número de CIs
- La parte baja de la dirección se conecta a las líneas de dirección de los CIs (`p` líneas, siendo 2p=N). La parte alta de la dirección (k bits), se conecta a las entradas del decodificador.
- Las salidas del decodificador se conectan a las entradas de selección (CS) de cada CI, y • Las líneas de datos se conectan a un bus común de m + h bits.
## Memorias de Acceso Serie
Son aquellas en las que el tiempo de escritura o lectura de una posición depende de la situación física de la misma en el interior de la memoria. Para escribir o leer en una de estas memorias es preciso **pasar primero por todas las posiciones anteriores**.
La inormación puede organizarse de dos formas:
1. Organización bit a bit:
	Se disponen en *serie* tanto las palabras como los bits que las conforman. La memoria posee una sola línea de entrada de información y una sola de salida.
	   ![[Memoria serie bit a bit|200]]
2. Organización posición a posición:
	Se disponen las palabras en *serie* pero los bits que las conforman en *paralelo*. Existen n entradas de información y n salidas de información. Se clasifican en: memorias FIFO, memorias LIFO y Registros de desplazamiento.
	![[Memorias posición a posición|200]]
### Registros de Desplazamiento
Son aquellos en los que la información se desplaza una posición en un sentido, con cada orden de lectura o escritura, regida por los impulsos de un clock. Existen dos tipos: estáticos y dinámicos.
#### Registros de desplazamiento estáticos
Son aquellos en los que los impulsos de desplazamiento *pueden anularse* por tiempo indefinido sin que la información almacenada se pierda. Constituidos por biestables síncronos activados por flanco.
![[Registros de desplazamiento estaticos.png|200]]
#### Registros de desplazamiento dinámicos
Son aquellos en los que los impulsos de desplazamiento *no pueden anularse* porque la información se perdería. La celda elemental es la capacidad parásita del MOSFET (similar a las [[#Memorias Electrónicas#Memorias de Lectura/Escritura Dinámicas]]).
Permiten construir CI de gran capacidad y bajo costo, gracias a la sencillez de las celdas y su alta densidad de integración.
A fin de restaurar la información en estos registros **las salidas se conectan a las entradas**, de esta forma la información circula permanentemente en todo el registro sincrónicamente a los impulsos del reloj.
![[Registros de desplazamiento dinamicos.png|200]]
#### Memorias FIFO
Son memorias serie en las que la primera información que entra es la primera que sale (*First Input First Output*).
Las memorias FIFO pueden implementarse con registros de desplazamiento estáticos y una unidad de control. Debe tener en cuenta lo siguiente:
- La lectura es destructiva. El dato leído ya no está más en la memoria.
- Cada operación de lectura o escritura debe producir un desplazamiento del resto de la memoria.
- Cuando la memoria está llena no podrá escribirse.
- Generar las señales de control necesarias para que el primer dato escrito esté disponible para la primera lectura.
- Deberá aceptar al menos tres entradas exteriores: señal de lectura/escritura, señal de inicio de ciclo y señal de sincronismo.
Las FIFO se encuentran en CI de LSI y una de sus aplicaciones es acoplar sistemas digitales con velocidades de procesamiento diferentes.
#### Memorias LIFO
En estas memorias, la última información que entra es la primera que sale (*Last Input First Output*).
Una LIFO puede implementarse con un registro de desplazamiento reversible. Un registro de desplazamiento reversible está formado por biestables síncronos y multiplexores. La salida de la memoria es la salida del primer biestable y la entrada es el segundo canal del primer multiplexor.