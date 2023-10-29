## Cableada
Está integrada por los siguientes componentes:
1. Decodificador de instrucciones: es un sistema combinacional. Un deco de 4:16, que se utiliza para determinar qué instrucción contiene el IR. Por lo tanto, sus entradas serán IR12 a IR15.
2. Secuenciador: es un sistema secuencial. Consta de: 
	- 2 biestables para definir los estados RUN (biestable SR) y STATE (biestable D)
	- 1 biestable relacionado con E/S
	- 1 biestable para tareas relacionadas con los pulsadores EXA y DEP
	- 1 reloj externo de 8MHz
3. Lógica de Control: sistema combinacional que consiste en un conjunto de compuertas que generan las señales de control.
![[Unidad de control cableada.png|500]]
### Secuenciador
La señal de sincronismo es un oscilador de 8 MHz llamado RELOJ que se divide en una secuencia de *8 pulsos* (`750 ns` en total), llamado CICLO DE MEMORIA, en líneas distintas separadas en tiempo por `125 ns`.
Si RUN = 1 el contador cuenta los pulsos del reloj. Las salidas del contador están conectadas a las entradas de un deco binario cuyas salidas son de `125 ns`.
Cuando la cuenta llega a 1001 (CP9), el contador borra y comienza un nuevo CICLO DE MEMORIA. Además, se usa para sincronizar el biestable ESTADO y borrar el SR sin nombre. Si la instrucción en proceso es de un ciclo, D toma el valor 0; en el caso de instrucciones de más de un ciclo, D toma el valor 1. De esta forma la máquina pasa de CICLO DE BÚSQUEDA a CICLO DE EJECUCIÓN automáticamente después del CP8.
Nótese que la máquina arranca con RUN = 1, al presionar el pulsador START y se detiene al presionar STOP, con un OV o con la instrucción HLT, siempre y cuando ESTADO = 0 (BÚSQUEDA).
El biestable SR E/S genera la señal TRA hacia los periféricos en las condiciones que se ven en la Figura 4.10. Además, recibe la señal R (READY) desde los periféricos y se pone en cero.
Los pulsadores EXA y DEP funcionan sólo si RUN = 0 y ESTADO = 0, y disparan un único CICLO DE MEMORIA. Más adelante se muestra el diagrama de tiempo del secuenciador, y aparecen los CP1 a CP8. El CP9, que no se usa en el CICLO DE MEMORIA, es de menor duración.
La ALU tiene un tiempo de suma de `200 ns`, es decir, que es mayor al del reloj. El de operación es de `80 ns`.
![[Secuenciador Cableado.png|400]]
#### El Ciclo de Búsqueda
Si el biestable RUN = 1, arranca el reloj, el biestabl de STATE = 0 está en Búsqueda y se inicia el ciclo de búsqueda de la máquina, en la cual la máquina carga la instrucción cuya dirección está en el PC, en el registro de instrucciones. Se necesita que el operador haya cargado un PROGRAMA en memoria y la dirección de la primera instrucción en el PC desde la consola.
![[Ciclo de busqueda cableada.png|200]]

| CP  | Acción       | Comentario                                                                           |
| --- | ------------ | ------------------------------------------------------------------------------------ |
| 1   | PC→MAR  PC→Z | Transfiere el PC al MAR y a Z, y comienza a leer la instrucción                      |
| 2   | +1→Y         | Coloca +1 en Y                                                                       |
| 3   |              | Tiempo de espera                                                                     |
| 4   | ALU→PC       | Hace la suma de PC+1 y coloca el resultado en el PC                                  |
| 5   | M→MBR        | Coloca el dato leído de la memoria en el MBR                                         |
| 6   | MBR→IR       | Transfiere el contenido del MBR al IR y comienza la decodificación de la instrucción |
| 7   |              | Disponible para decodificación y ejecución                                           |
| 8   |              | Se define si el próximo ciclo es de búsqueda o de ejecución                          |
<small>
**Dibujar para entender**
En el pulso de reloj 1 se copia el contenido del contador de programa (PC) al registro de direcciones de memoria (MAR) y al registro Z de la ALU, y se inicia el ciclo de lectura de la memoria. En el pulso de reloj 2 se coloca el número +1 en el registro Y de la ALU. En el pulso de reloj 3 esperamos que se realice la suma PC + 1, ya que requiere 200ns y el ciclo es de 125ns. En el pulso 4 se copia el resultado de la suma (la salida de la ALU) al contador de Programa (esto incrementa el PC y está listo para indicar la próxima instrucción). En el pulso 5 se copia el dato de la memoria al registro buffer de memoria (MBR). En el pulso 6 se copia el contenido del MBR al registro de instrucción (IR). Así culmina el Ciclo de Búsqueda.
Si la instrucción en cuestión no requiere en su ejecución acceder a la memoria por un dato, se pueden utilizar los pulsos de reloj 7 y 8 para ejecutar algunas instrucciones de la BLUE. Este es el caso de las instrucciones HALT, NOP, JMP, JMA, SRJ, CSA, NOT, RAL. Las mismas finalizan en el ciclo de memoria asignado a la Búsqueda (no necesitan otro ciclo de memoria) y las llamamos instrucciones de un ciclo. Es decir, la búsqueda y ejecución de estas instrucciones se realizan en un mismo ciclo de memoria. Al finalizar el ciclo de búsqueda, empieza un nuevo ciclo que debe asignarse nuevamente a Búsqueda.
Si la instrucción en cuestión requiere en su ejecución acceder a la memoria, o si se trata de las instrucciones INP o OUT, será necesario asignar el próximo ciclo a Ejecución.
</small>
#### El Ciclo de Ejecución
Las instrucciones que requieren de un dato a memoria para realizar una operación lógica o matemática, o realizar una transferencia de datos hacia o desde la memoria, requieren un segundo ciclo de memoria. Estas son: LDA, STA, ADD, XOR, AND, IOR. Para acceder a memoria es necesario un segundo ciclo de memoria.
Pero también existen instrucciones que requieren más de un ciclo y no acceden a memoria en su ejecución. Es el caso particular de las instrucciones de E/S: INP y OUT. Utilizan nuevos ciclos para esperar al periférico involucrado. Y serán tantos ciclos como el tiempo de espera.
a) Instrucciones de 8 pulsos (`1000ns = 1micros`).
b) Instrucciones de 16 pulsos (`2000ns = 2micros`).
![[Ejecucion de las instrucciones uno y dos ciclos.png]]
<small>Ejecución de las instrucciones de uno y dos ciclos.</small>
![[Ciclo de busqueda de las instrucciones INP y OUT.png]]
<small>Ciclo de Búsqueda de las instrucciones INP y OUT.</small>
El hardware es:
![[Logica para el funcionamiento de la E-S.png|300]]
#### Lógica de Control
Las entradas a este bloque combinacional son los códigos de operación decodificados, los pulsos de reloj y el estado de búsqueda o ejecución. Las salidas deben ser las órdenes concretas que emite la unidad de control.
Ejemplo: ¿En qué casos la UC debe emitir la orden de CARGAR MAR?
1. Si la máquina está parada y se presiona el pulsador EXA o DEP durante el CP1,
2. Si la máquina está funcionando, y está en búsqueda y durante el CP1, o
3. Si la máquina está funcionando y está en ejecución de las instrucciones LDA, STA, ADD, IOR, AND o XOR durante el CP1.
El circuito de control deberá tener en cuenta si la máquina está parada y que se producirá una única secuencia de pulsos CP1 a CP8 sólo si el operador presionó EXA o DEP.
## Microprogramada
![[Unidad de control Microprogramada.png]]
La búsqueda y ejecución de cada macroinstrucción son realizadas por los microprogramas residentes en la micro-ROM (al contenido de la ROM, es decir, los microprogramas y la propia ROM se le llama FIRMWARE). La dirección de la primera microinstrucción a ejecutar, es proporcionada por el código de operación de la macroinstrucción, es decir, será alguna de las 16 primeras posiciones.
Cada microinstrucción está compuesta de 45 bits, divididos en seis campos: Acción, Test, Envíe, Reciba, Falso, y Éxito.
El campo Acción está relacionado con las órdenes que debe dar la Unidad de Control (leer la memoria, escribir la memoria, etc.), el campo Test se relaciona con la necesidad de chequear el estado de la máquina en un momento dado (Bit 15 del acumulador, señal de overflow, etc.). Los campos Envíe y Reciba tienen que ver con enviar los contenidos de los registros al bus o levantarlos del mismo. Por último, los campos falso y éxito están relacionados con el resultado del chequeo indicado por el campo Test y definen la próxima microinstrucción a ejecutar. Nótese que la máquina interior no posee contador de programa.