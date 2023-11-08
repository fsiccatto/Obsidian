# Arquitectura Básica
## Arquitectura Von Neumann
Está compuesta por cinco elementos:
1. Unidad de Proceso Central (CPU)
2. Unidad de Memoria (UM)
3. Unidad de Entrada/Salida (UE/S)
4. Unidad de Buses (UB)
5. Programa Almacenado en UM (PA)
![[imagenes/Arquitectura Von Neumann.png|200]]
El funcionamiento de la Computadora implica una fuerte cooperación entre las unidades que la componen y supone que, en la memoria, reside un conjunto ordenado de INSTRUCCIONES llamado PROGRAMA.
#### Funcionamiento
Las instrucciones del programa se buscan y ejecutan secuencialmente por la CPU hasta que el programa finaliza. Durante la ejecución, es posible que sea necesario obtenero o guardar datos desde o hacia la UM, o a través de la UE/S.
1. CPU → contiene:
	- Varios REGISTROS, que se usan para alamacenar información temporalmente.
	- ALU. Realiza operaciones lógico-aritméticas necesarias en la ejecución de una instrucción.
	- UC. La unidad de control realiza el control del sistema, para lo cual genera un conjunto de señales de control.
2. UM → almacena programas y datyos. Es una memoria RAM de lectura/escritura. Por otro lado, una porción de la UM podría ser ROM, para almacenar programas o datos que no cambien y deberían permancer aún si se quita la alimentación.
3. UE/S → se encarga de interconectar la computadora con los periféricos accesibles al usuario (teclado, monitor, mouse). Las UE/S cuentan con INTERFACES (adaptan niveles eléctricos de señales) y CONTROLADORES que son sistemas digitales para controlar periféricos.
4. UB → la unidad de buses cumple la función de transportar información entre las unidades del sistema. Podrían clasificarse en:
	- BUS DE DATOS → transporta operandos o información
	- BUS DE DIRECCIONES → transporta direcciones
	- BUS DE CONTROL → transporta señales de control
5. PA → el programa almacenado es un conjunto de instrucciones almacenadas correlativamente en la UM. Tienen un comienzo y un fin. Las instrucciones son propias de cada máquina y se conocen como Set de Instrucciones.
# Máquina Elemental
Las características principales de esta computadora son:
- Arquitectura Von Neumann
- Usa sistema binario y aritmética en complemento a 2
- Su memoria es de 4096 x 16
- Usa punto fijo y sus datos son de 16 bits (15 bits mantisa y 1 un bit de signo)
- Usa instrucciones de formato fijo de 16 bits (4 bits para el código de operación y 12 bista para el campo de dirección)
- Usa un BUS común de 16 bits multiplexado (datos y direcciones)
- Capacidada para manejar hasta 128 periféricos (64 de entrada y 64 de salida)
- La ALU realiza, sobre 1 o 2 operandos, las siguientes operaciones:

| ADD | OR  | XOR | AND | RAL | NOT |
| --- | --- | --- | --- | --- | --- |
Externamente tiene una consola con llaves, pulsadores y luces, que permite al operador comunicarse con la Máquina:
![[imagenes/Maquina Elemental.png|200]]
El diagrama de bloques es el siguiente
![[imagenes/Diagrama de bloques de la maquina elemental.png|400]]
### Arquitectura de la Computadora Elemental
#### CPU
La CPU cuenta con:
- REGISTROS
	- ACC (16 bits) → el registro Acumulador es un registro de propósitos generales.
	- IR (16 bits) → el registro de Instrucciones se utiliza para guardar la instrucción que se ha buscado desde la memoria. (16 luces leds).
	- PC (12 bits) → el registro Contador de Programa se utiliza para guardar la dirección de memoria de la próxima instrucción a buscar.
	- Z e Y (16 bits) → son registros de operandos de entrada a la ALU y no son accedidos por el programador.
	- 1 (1 bit) → permite generar un bit.
- ALU → realiza operaciones aritméticas entre los registros Z e Y. Genera la señal OV (overflow) si el resultado de la suma supera la capacidad de representación.
- UC → tiene una entrada de sincronismo y genera órdenes en sincronismo con los flancos del reloj. Existen dos tipos: UC cableada y UC microprogramada.
#### UM
Memoria RAM L/E. Posee un registro asociado a las líneas de datos MBR (16 bits), a través del cual pasará la información que se lea o escriba en la memoria. También posee otro asociado a las líneas de dirección MAR (12 bits), cuyo contenido deberá ser la dirección de memoria a la que se pretende acceder. RAM de `ta = 400ns`.
#### UE/S
Se observan dos casos:
- La **CONSOLA**: conectada directamente al BUS. Se comunica con la CPU a través de las 6 pulsadores, 16 llaves y 16 luces leds.
	- ARRANQUE
	- PARADA
	- CARGAR PC → transfiere el contenido del SR al PC
	- DEPOSITAR → transfiere el contenido del SR a la posición de la memoria indicada por el PC, luego el PC aumenta
	- EXAMINAR → transfiere el contenido de la posición de memoria indicada por el PC al IR, luego incrementa pC
	- RESET → borra la RAM y los registros
- Los DISPOSITIVOS EXTERNOS: son los periféricos (P0 a P63 de entrada y P0 a P63 de salida). Tienen destinado un BUS bidireccional dedicado a E/S (8 bits) para los Datos y un BUS (6 bits) para selección de periférico.
### El Conjunto de Instrucciones
Esta computadora posee un tipo de instrucción de longitud fija de 16 bits con el formato:
![[imagenes/Conjunto de Instrucciones.png|200]]
Como tenemos 4 bist para el código de operación, se dispone de 16 instrucciones:
![[imagenes/Codigo de operacion.png|400]]
![[Códigos de Operación#Códigos de Operación]]
### El Ciclo de Máquina
Procedimiento que consta de   para poder buscar y ejecutar completamente una instrucción del programa almacenado en memoria, que podemos sintetizar de la siguiente forma:
- Búsqueda de una instrucción a memoria
- Lectura e interpretación de esa instrucción
- Ejecución de la misma
- Almacenamiento de resultados
- Preparación para leer la próxima instrucción
La BLUE tiene un ciclo de máquina básico compuesto en dos:
	➢ Ciclo de Búsqueda
	➢ Ciclo de Ejecución
Durante el *Ciclo de Búsqueda*, la instrucción almacenada en la memoria y apuntada por el *Contador de Programa* (PC) se localiza en la memoria y se copia en el *Registro de Instrucciones* (RI). Luego, el número almacenado en el *PC* se incrementa en uno, logrando así que ahora apunte a la próxima celda de memoria (o sea, a la siguiente instrucción).
Al completar el *Ciclo de búsqueda*, la instrucción que está en el *IR* se analiza, decodifica y ejecuta. Si la presente instrucción no necesita hacer una nueva búsqueda a memoria (de algún dato u operando) el ciclo de máquina termina en ese momento.
Si es necesario buscar un operando a memoria, entonces comienza el *Ciclo de Ejecución*, para realizar un nuevo acceso a memoria para traer al operando necesario y completar así la instrucción.
### Flujo de Información
El **Flujo de direcciones** en la BLUE son movimientos entre registros de 12 bits:
- Load PC: envía los 12 bits más bajos del registro de llaves (R.Sw.) al PC. 
- Saltos (JMP, JMA, SRJ): envían los 12 bits más bajos del RI al PC. 
- SRJ (salto a subrutina): envía los 12 bits del PC al Acumulador (ACC). 
- Búsqueda de una instrucción: envía los 12 bits del PC al MAR. 
- Búsqueda de un Operando: envía los 12 bits más bajos de RI al MAR.
![[imagenes/imagenes/imagenes/Transmision de Operaciones.png|300]]
El **Flujo de instrucciones y operandos** en la BLUE son movimientos entre registros de 16 bits:
- CSA: copia los 16 bits del R.Sw. al ACC. 
- Deposit: copia los 16 bits del R.Sw. al MBR. 
- Instrucciones: se copian del MBR al RI. 
- LDA: copia los 16 bits del MBR al ACC. 
- STA: copia los 16 bits del ACC al MBR. 
- Operaciones de la ALU (en el ciclo de ejecución): 
	- Copia los 16 bits del ACC al Registro Z de la ALU. 
	- Copia los 16 bits del MBR al Registro Y de la ALU. 
	- El Resultado (o salida de la ALU) se copia al ACC.
![[imagenes/Transmision de instrucciones.png|300]]
Para poder hacer las transferencias vistas es necesario implementar un BUS COMÚN.
### Unidad de Control
La tarea de la unidad de control es coordinar todas las acciones de la máquina. Para este trabajo se necesita una secuencia de pulsos y señales que deben generarse sincrónicamente al reloj.
Existen dos manera de diseñarla, su diferencia es la implementación interna:
- Unidad de Control Cableada
- Unidad de Control Micoprogramada
### Bus en la Máquina Elemental
Las órdenes qe emite la UC implican una gran transferencia entre registros. Son 20 señales entre enviar al BUS y cargar desde el BUS.
Por lo tanto los registros deben estar eficazmente interconectados y esto se logra con la arquitectura de BUS COMÚN. Este puede transportar un dato (16 bits), una instrucción (16 bits) o una dirección (12 bits) en distintos momentos. Las señales de control son diseminadas por la máquina por un BUS de CONTROL.