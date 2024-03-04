# Arquitectura Convencional
## Visión General
### Formato de Instrucciones
Cualquier instrucción que involucre una operación diódica (dos operandos y un resultado), requiere cuatro piezas de datos además del código de operación:
- Ubicación del primer operando
- Ubicación del segundo operando
- Ubicación del resultado
- Ubicación de la próxima instrucción
#### Formato de Cuatro Direcciones
Las primeras máquinas solían tener estas cuatro piezas en la propia instrucción. No usa CP.

| Codigo de Operación | Dirección del Operando A | Dirección del operando B | Dirección del resultado en C | Dirección de la próxima instrucción en D |
| ------------------- | --------------------------- | --------------------------- | ---------------------------- | ---------------------------------------- |
La instrucción ADD A, B, C, D implica sumar A+B, colocar el resultado en C y buscar la próxima instrucción en D (puntero).
#### Formato de Tres Direcciones
La primera pieza a eliminar es la dirección de la próxima instrucción. Las instrucciones van de forma sucesiva en la memoria y se obtiene con el contador de programa.

| Codigo de Operación | Dirección del Operando A | Dirección del operando B | Dirección del resultado C |
| ------------------- | --------------------------- | --------------------------- | ---------------------------- |
La instrucción ADD A, B, C implica sumar A+B, colocar el resultado en C y buscar la próxima instrucción de acuerdo al PC.
#### Formato de Dos Direcciones
La siguiente pieza a eliminar es la ubicación del resultado. Usan nuestras computadoras.

| Codigo de Operación | Dirección del Operando A | Dirección del operando B | 
| ------------------- | --------------------------- | --------------------------- |
La instrucción ADD A,B implica sumar A + B, colocar el resultado en B y buscar la próxima instrucción de acuerdo al PC. La dirección del operando B no se utiliza.
#### Formato de Una Dirección
La siguiente pieza a eliminar es la dirección del primer operando. Este operando se encuentra en un registro de la CPU.

| Codigo de Operación | Dirección del Operando B |
| ------------------- | --------------------------- |
La instrucción ADD B implica sumar el contenido del Acc + B, colocar el resultado en el Acc, y buscar la próxima instrucción de acuerdo al PC. **Este es el caso de la BLUE**.
### Modos de Direccionamiento
Son medios que facilitan la tarea de programación, permitiendo el acceso a los datos. Estos Modos de Direccionamiento indican al procesador cómo calcular la dirección absoluta (real o efectiva) para determinar donde se encuentran los datos. Es decir, especifican la manera de obtener un operando. El operando puede estar ubicado: 
- En la Memoria,
- En un Registro de la CPU, 
- En la propia Instrucción (el dato se encuentra dentro de la instrucción almacenada en el IR, y por lo tanto, en la CPU).
De acuerdo a donde está ubicado el operando y a cómo se especifica, tenemos los siguientes modos de direccionamiento:
![[imagenes/Modos de Direccionamiento.png|300]]
#### Operando en la CPU
##### Modo de direccionamiento inmediato
El operando está en la instrucción. En la BLUE, no disponemos de este modo.
##### Modo de direccionamiento por registro
El operando está en un Registro de la CPU. En la BLUE este modo está ejemplificado en las instrucciones:
- NOT → El Operando está en el ACC. Se trata de una operación sobre un único operando en el ACC.
- RAL → El Operando está en el ACC. Es un caso similar al anterior.
- CSA → EL OPERfuente está en el SR y el OPERdestino está en el ACC. Se trata de una operación de movimiento de datos de un operando.
#### Operando en la Memoria
##### Modo de direccionamiento directo
La dirección del operando está en la instrucción. En la BLUE este modo está en las siguientes instrucciones:
- LDA XXXX → El OPERfuente está en la dirección XXXX de Memoria (Modo de direccionamiento directo) y el OPERdestino en el ACC (Modo de direccionamiento registro).
- STA XXXX → El OPERfuente está en el Acc (Modo de direccionamiento por registro) y el OPERdestino en la dirección XXXX de Memoria (Modo de direccionamiento directo).

También son ejemplos las instrucciones: ADD XXXX, IOR XXXX y XOR XXXX. 
En estos casos, el OPER2 está en la Memoria y su dirección (XXXX) se indica en la instrucción (Modo de direccionamiento directo) y el OPER1 está en un registro de la CPU: el ACC (Modo de direccionamiento por Registro).
##### Modo de direccionamiento indirecto por memoria
En la instrucción se especifica la dirección de la dirección del operando. Este modo de direccionamiento no está en la máquina elemental. El soporte del mismo implica ampliar el hardware y el software de la BLUE.
##### Modo de direccionamiento indirecto por registro
La dirección del operando (o parte de ella) está en Registros destinados a tal fin. Este modo de direccionamiento no está en la BLUE. También en este caso sería necesario ampliar los componentes de la BLUE.
Este Modo de Direccionamiento es en realidad indirecto, ya que la dirección del operando no está en la instrucción sino en un Registro, razón por la cual también se lo suele llamar Indirecto por Registro.

Los modos de direccionamiento indirecto son muy útiles para el programador en relación con tareas muy comunes en el ámbito de la programación. Estas son:
- Modificar direcciones,
- Generar contadores a fin de implementar lazos repetitivos,
- Reducir el espacio ocupado en memoria por las instrucciones,
- Permitir la reubicación del código, y 
- Facilitar el manejo de las estructuras de datos, entre otras.
Con esto surge la idea de mejorar el hardware a fin de facilitar tareas.
## Nuevo Hardware y Nuevo Software
### Registros Nuevos
#### Registros Índices
Vamos a agregar Registros Índice, los cuales *facilitan el movimiento de un bloque de datos en la memoria*, a la máquina elemental. Serán dos registros de 16 bits:
- Registro Índice Fuente (RIF)
- Registro Índice Destino (RID)
Modificaremos el formato de instrucción, a fin de poder indicar de qué modo de direccionamiento se trata. Planteamos el formato:
![[imagenes/Formato de Instruccion modificado.png]]
Las instrucciones con estos campos *requerirán 2 posiciones de memoria* de 16 bits, asignando la segunda posición al Campo Dirección.
Con 5 bits de Código de Operación, podremos tener hasta 32 instrucciones.
Con los 2 bits en el Campo Modificador podremos seleccionar hasta 4 Modos de Direccionamiento.
Con 16 bits en el Campo de Dirección podremos direccionar hasta 65536 posiciones de memoria.
Las instrucciones de la BLUE de un solo ciclo, que permanecen en la Máquina Elemental Indexada (MEI), *ocuparán una sola posición de memoria* (16 bits), ya que no necesitan el Campo Modificador y/o el Campo de Dirección.
- Directo
	Si el contenido del campo modificador es 0, usa el campo de dirección como la dirección del operando. Ejemplo: 
		LDA 0, 100 → Carga el Acc con el contenido de la posición 100.
- Indirecto por memoria
	Si el contenido del campo modificador es 1, el campo de dirección apunta a una posición de memoria cuyo contenido no es el operando sino la dirección de éste. Ejemplo:
		Suponiendo que el contenido de la posición 1000 es 3400
		LDA 1, 1000 → Carga el Acc con el contenido de la posición 3400.
- Indirecto por registro (indexado)
	- Si el contenido del campo modificador es 2, el contenido del RIF se suma al campo de dirección obteniendo así la dirección del operando. Ejemplo:
		Suponiendo que el contenido de RIF es 5000
		LDA 2, 1000 → Carga el Acc con el contenido de la posición 6000 (1000 + 5000)
	- Si el contenido del campo es 3, el contenido del RID se suma al campo de dirección obteniendo así la dirección del operando.
##### Sumador
Para realizar la suma indicada para el direccionamiento indexado, agregamos un sumador en la CPU dedicado sólo a esta tarea (ya no usamos el tiempo de la ALU). Este sumador tiene dos registros de entrada: el registro W y el registro X de 16 bits cada uno. Además siempre suma al resultado el contenido de un tercer registro que agregaremos: el Registro Base de 16 bits.
##### Decodificador del Campo Modificador
Implementamos en la Unidad de Control un nuevo decodificador: el DECODIFICADOR DEL CAMPO MODIFICADOR, además del Decodificador de Instrucciones ya existente. Esto permite realizar simultáneamente la decodificación del Código de Operación de la instrucción y del Campo Modificador.
#### Registro Base
*Permite reubicar programas* (guarda el contexto), es un registro de 16 bits. Es parecido al Registro Índice en el sentido que su contenido se suma al campo de dirección de la instrucción a fin de obtener la dirección efectiva. La *diferencia* consiste en que:
- El usuario común **no tiene control** sobre el contenido del Registro Base, y
- El contenido del Registro Base se suma **siempre** a la dirección efectiva cuando se realiza una referencia a memoria (puntero) en la Ejecución de la instrucción.
- Las constantes son inmunes al cambio de instrucción en la dirección.
### Máquina Elemental Indexada
Se propone una nueva Máquina Elemental Indexada (MEI) incluyendo los Registros Índice, el Registro Base y el Sumador de Direcciones con sus registros de entrada W, X, y RB.
![[imagenes/Maquina elemental indexada.png|300]]
El Sumador de Direcciones realiza la suma aritmética de direcciones sobre 3 operandos:
- El registro W de 16 bits
- El registro X de 16 bits
- El registro base de 16 bits
Siempre que se genera una dirección en tiempo de Ejecución se realiza esta suma. Ésta suma no influye para la Búsqueda, ya que la dirección de la instrucción buscada es el contenido del registro PC. El acarreo de este sumandor no se tiene en cuenta.
![[imagenes/Instrucciones MEI 1.png]]
![[imagenes/Instrucciones MEI 2.png]]
![[imagenes/Instrucciones MEI 3.png]]
![[imagenes/Instrucciones MEI 4.png]]
### Ciclos de Máquinas
VER EJEMPLOS EN EL PDF
- La Máquina Elemental Indexada no tiene formato fijo de instrucción,
- No todas las instrucciones que hacen referencia a memoria deben tener todos los modos de direccionamiento. Por ejemplo, la instrucción LIX 2, XXXXXX no posee modo de direccionamiento indexado ya que se estaría autoindexando.
- Las instrucciones pueden tener de 1 a 4 ciclos de máquina para ejecutarse, dependiendo de la instrucción y de su modo de direccionamiento.
### Interrupciones
Existen formas de manejar las operaciones de entrada-salida que no inmovilizan la CPU mientras ocurre una transferencia de datos. Tiene que ver con la velocidad de los periféricos. Existen problemas de eventos de periféricos externo que conviene atender.
El modo más conveniente es que se produzca una interrupción automática del programa corriente, y se transfiere el control temporariamente a una rutina especial para manejar estos eventos.
Podríamos clasificar la transferencia de Entrada/Salida de la siguiente forma:
![[Manejo de E-S.png]]
Algunas de las interrupciones internas del procesador pueden ser el desborde de registro, división por cero, código de operación no válida, etc. Y las llamadas por software, cuando se dispara un proceso de interrupción mediante instrucciones especiales.
##### Manejo de Entrada/Salida Bajo Control del Procesador
En general, las operaciones de entrada/salida son iniciadas por el procesador. Una vez iniciada la operación el procesador espera que la misma se complete, y luego, continúa con el programa principal. Este es el caso de la BLUE.
Si la velocidad del dispositivo es inferior a la del procesador este está inmovilizado por mucho tiempo. Peor aún, si el dispositivo sufre algún desperfecto, el procesador puede esperar eternamente.
##### Manejo de Entrada/Salida con Interrupciones
La otra opción es iniciar la operación de entrada/salida y continuar con el programa principal. Cuando el dispositivo en cuestión termina, solicita un pedido de atención (solicitud de interrupción) que, al ser atendido por el procesador, finaliza con la operación.
Es más eficaz que el anterior porque no hay que esperar al periférico, pero requiere hardware e instrucciones epeciales que lo soporten. Además, si existe más de un dispositivo que solicite atención, es necesario identificarlo y asignar prioridades.
Las interrupciones se pueden clasificar en:
- Polling
- Vectorizadas
####  Sistema Elemental de Interrupciones
Se define un biestable en la UC que se llama Sistema de Interrupción (SI). El valor o estado del SI puede controlarse por medio de dos nuevas instrucciones: ION e IOF. La UC lo desactiva cuando se está procesando una interrupción, y lo activa cuando el proceso ha concluido.
- Si el SI está en 1 el sistema de interrupciones está "habilitado".
- Si el SI está en 0 el sistema de interrupciones está "deshabilitado".

Cada dispositivo con capacidad de interrumpir posee una línea de solicitud de interrupción que pone a 1 cuando necesita atención. Estas Banderas de Dispositivo (BD) van a una compuerta OR cuya salida, será una línea única de pedido IRQ (Interrupt Request) de interrupción a la CPU.
Si las interrupciones están habilitadas (SI=1) e IRQ pasa a 1, *se produce una interrupción en la ejecución del programa corriente*, justo **antes** del comienzo del próximo ciclo de búsqueda. Es decir, la instrucción actual termina de ejecutarse.
Ocurren tres eventos cuando la CPU acepta una interrupción:
- El biestable SI se coloca en 0, inhabilitando el sistema de interrupciones.
- El contenido del PC se guarda en la posición CERO.
- Se carga el PC con el valor 1 y se dispara un ciclo de búsqueda.
Estos eventos los lleva la Unidad de Control. El biestable PRO indica que la CPU está atendiendo una interrupción.
Ahora existen tres estado en la máquina:
- Búsqueda (F)
- Ejecución (E)
- Interrupción (I)
Podemos ver que el estado de interrupción ocurre cuando:
- La línea IRQ está en 1 (algún dispositivo requiere atención),
- El sistema de interrupciones está habilitado (SI = 1),
- Ha finalizado la ejecución de la instrucción corriente
	- Con CP8 en el estado de Ejecución, o
	- al final de un ciclo de Búsqueda,
		- Si la instrucción corriente es de 1 ciclo.
![[imagenes/UC con sistema de interrupciones.png|400]]
##### Ciclo de Interrupción

| Pulso de reloj | Accion                            |
| :--------------: | :---------------------------------: |
| CP1            | Envie 1, cargue Z, cargue Y, SI=0 |
| CP2            | Envie PC, cargue MBR              |
| CP3            | Envie ALU (XOR), cargue MAR, OE    |
| CP4            | Envie 1, cargue PC                |
| CP5            | -                                 |
| CP6            | -                                 |
| CP7            | -                                 |
| CP8            | Biestable I=0                                  |
##### Rutina de Interrupción
En la posición de memoria 1 debe haber una instrucción de salto a la rutina de interrupción cuya tarea consiste en la secuencia de acciones:
1. Salvar contexto ↓ (guardar registros, datos del programa principal)
2. Determinar quién causó la interrupción ↓ (polling o vectores de interrupción)
3. Saltar a la rutina de atención del periférico ↓ (específica para cada periférico)
4. Restaurar contexto ↓ (volver a cargar los registros de la CPU con los valores que tenían antes)
5. Habilitar interrupciones y retornar al programa principal (RTI: Retorno de Interrupción, se ven en los cuadros de abajo)

|  Pulso de reloj  |               Accion                |
|:----------------:|:-----------------------------------:|
|       CP1        |  Envie PC, cargue MAR, orden de lectura  |
|       CP2        |        -         |
|       CP3        |   -   |
|       CP4        |         -         |
|       CP5        |                  -                  |
|       CP6        |                  Envie MBR, IR                 |
|       CP7        |                  Envie 1, cargue Z, cargue Y      |
|       CP8        |            Pasar a *ejecución*            |

|  Pulso de reloj  |               Accion                |
| :--------------: | :---------------------------------: |
|       CP1        |  Envie ALU (XOR), cargue MAR, orden de lectura  |
|       CP2        |        -         |
|       CP3        |   -    |
|       CP4        |         -         |
|       CP5        |                  -                  |
|       CP6        |                  Envie MBR, cargue PC                  |
|       CP7        |                  -                  |
|       CP8        |            PRO=0, SI=0, Pasar a *búsqueda*            |
Ciclo de máquina de la instrucción RTI
##### Polling
Sirve para determinar qué periférico solicitó la interrupción.
Se recuerda que cada dispositivo con capacidad de interrumpir posee una "Bandera de Dispositivo" (BD). Si BD está en 1 indica que solicita interrupción, y 0 en caso contrario.
En la técnica de polling *se pregunta secuencialmente* por las BD con un cierto orden. La primera BD=1 resulta en un salto a la subrutina de atención del periférico que corresponda. Se puede proponer una nueva instrucción que verifique estas banderas:
	***SKF XX*** → Omitir la próxima instrucción si XX es CERO, donde XX representa la bandera que se corresponde con los dispositivos que solicitan interrupción.
El orden en que se realiza la verificación de las banderas de dispositivo, en la Rutina de Interrupción, determina la prioridad del dispositivo que solicita atención.
Una alternativa, que no se implementa en la Máquina Elemental Indexada, es agregar un nuevo registro llamado Registro Máscara (RM) cuyo contenido puede modificarse con una nueva instrucción: EMR Valor.
Este registro permite enmascarar (evitar dar curso a) solicitudes de interrupción.
![[imagenes/Registro mascara.png|200]]
##### Vector de Interrupciones
Otro método para determinar quién interrumpe. Por un lado, se guardan los drivers de los periféricos (el espacio de memoria de los dispositivos son todos diferentes). Por otro lado, se asigna a cada dispositivo solo la primer dirección de los drivers (el espacio de memoria son todos iguales). Lo único que falta es algo que nos diga a cual periférico hay que saltar.
A cada dispositivo se le asigna una dirección llamada vector de interrupción (Trap Vector Address). Esta dirección es suplida por el dispositivo que interrumpe y en la misma, el programador debe almacenar la dirección de comienzo de la Rutina de Atención que corresponda. De esta forma toma lugar un salto indirecto a través del vector a la Rutina de Atención.
![[imagenes/Vector de interrupciones.png|200]]
Éste método es más rápido que el Polling ya que no es necesario preguntar bandera a bandera. Por otro lado, es conveniente considerar una Señal de Reconocimiento de Interrupción ACK, generada por la UC, cuando ha reconocido una solicitud de interrupción y comienza el proceso de su atención.
#### Inicio de una Transferencia
Los periféricos son dispositivos externos a la MEI. Los periféricos pueden poseer:
- Elementos de micromecánica (servomotores, relay, motores paso a paso, sensores ópticos, sensores magnéticos, indicadores luminosos, componentes electrónicos de media potencia, etc.),
- Circuitos electrónicos que permiten controlar a los diferentes elementos constitutivos del periférico (CONTROLADOR), y
- Circuitos electrónicos que permiten la adaptación de los niveles de tensión y corriente (INTERFASE), para poder conectarlos a la MEI.

Las acciones de control de un periférico se realizan por los **controladores**. Se trata de sistemas electrónicos dedicados solo al periférico en cuestión, de forma que el control no es tarea del CPU. La mayoría de los periféricos dejan ver a la CPU los siguientes registros:
- REGISTRO DE DATOS: a través del cual fluyen los datos de la transferencia.
- REGISTRO DE CONTROL: a través del cual la CPU envía los comandos.
- REGISTRO DE ESTADO: refleja el estado del periférico.
![[imagenes/Metodo vectorizado señal ack.png|200]]
Los periféricos se clasifican en función de la dirección de los datos que fluyen por el BUS de E/S, en:
- Periféricos de Entrada
- Periféricos de Salida
Si los datos se dirigen hacia el Periférico se considera de Salida y viceversa.
Simplificamos la cuestión suponiendo que los periféricos sólo tienen REGISTRO DE DATOS.

**Ciclo de las instrucciones de entrada salida con interrupciones**
Las transferencias de E/S, en general, son iniciadas por el programa, a través de:
- INP YY
- OUT YY
Estas instrucciones tienen ahora ciclos de máquina diferentes a los vistos en la BLUE. La diferencia consiste en que *no realizan la verificación de la señal R* (Ready). Simplemente hacen TRA = 1 durante un pulso de reloj, y luego, TRA = 0.
OUT YY ya no espera la señal R desde el periférico, sólo genera un 1 (de pulso de reloj de duración) que le indica al periférico YY el comienzo de una transferencia de salida (Tabla). El periférico, al recibir TRA=1, carga su Registro de Entrada con el valor de los 8 bits menos significativos del ACC a través del BUS de E/S, y comienza a realizar la acción correspondiente (ej imprimir). El programador deberá cargar el ACC con el dato que desea transferir, antes de la instrucción OUT YY.

|  Pulso de reloj  |               Accion                |
| :--------------: | :---------------------------------: |
|       CP1        |  Envie PC, cargue MAR, cargue Z, orden de lectura |
|       CP2        |        Envie 1, cargue Y         |
|       CP3        |   -    |
|       CP4        |         Envie SUMA, cargue PC         |
|       CP5        |                  -                  |
|       CP6        |                  Envie MBR, cargue IR                 |
|       CP7        |                  TRA=1                 |
|       CP8        |            TRA=0, Pasar a *búsqueda*            |
Mientras que INP YY genera un pulso TRA = 1 (igual que la instrucción OUT YY) sólo si PRO = 0, es decir, si la CPU no está involucrada en un Proceso de Interrupción (Tabla).

|  Pulso de reloj  |               Accion                |
| :--------------: | :---------------------------------: |
|       CP1        |  Envie PC, cargue MAR, cargue Z, orden de lectura |
|       CP2        |        Envie 1, cargue Y         |
|       CP3        |   -    |
|       CP4        |         Envie SUMA, cargue PC         |
|       CP5        |                  -                  |
|       CP6        |                  Envie MBR, cargue IR                 |
|       CP7        |                  Si PRO=0, TRA=1                 |
|       CP8        |            Si PRO=1, envie PYY, cargue ACC, TRA=0, Pasar a *búsqueda*            |
En el caso que la CPU esté en Proceso de Interrupción (en algún lugar de la Rutina de Interrupción), no se genera TRA y en CP8 se cargan los 8 bits más significativos del ACC con el valor del Registro de Salida del periférico YY (PYY) a través del Bus de E/S.
#### Controladores Elementales de Periféricos
##### Periféricos de Salida
Si se trata de un Periférico de Salida y se ha ejecutado una instrucción OUT YY, su Registro de Datos se cargará con el dato que esté en el BUS de E/S cuando el periférico seleccionado (YY) reciba la señal TRA e iniciará acciones.
##### Periféricos de Entrada
Si se trata de un Periférico de Entrada y se ha ejecutado una instrucción INP YY hay dos opciones: 
- Si PRO = 0, la Máquina no está atendiendo una interrupción. Por lo tanto, cuando se ejecuta INP YY, el periférico YY recibe TRA e inicia las acciones para obtener el dato solicitado. 
- Sin PRO = 1, la Máquina está atendiendo una interrupción y su Registro de Datos tendrá el dato solicitado y estará disponible en el Bus de E/S cuando el periférico sea seleccionado (CP7 de la instrucción INP YY). La señal TRA no se genera en este caso por la instrucción INP YY.
#### Registro de Puntero de Pila
El Sistema de Interrupciones descripto no permite que la CPU sea interrumpida cuando está atendiendo una interrupción, ya que la dirección de retorno guardada en la posición CERO se perdería. *Entonces el Registro Puntero de Pila guarda varias direcciones de retorno de interrupciones.*
Si el contexto de la máquina (incluido el PC) se guardara en la memoria en una estructura LIFO (pila), cuya dirección inicial se indicará en un nuevo Registro, sería posible atender interrupciones dentro de una interrupción (interrupciones anidadas). A este registro se le llama REGISTRO PUNTERO DE PILA (SP). Por cada nueva interrupción, sólo debe incrementarse este Registro en la cantidad adecuada, y su contenido debe decrementarse por cada retorno de interrupción. Además, el biestable SI debería ponerse en 1 justo al comienzo de la Rutina de Atención de Dispositivo.
El programador debe escribir la Rutina de Interrupción de manera que los dispositivos de menor prioridad no puedan interrumpir un proceso de interrupción corriente de mayor prioridad. Y habría que agregar nuevo hardware y más instrucciones.
## Microprocesador Intel 8088
El término microprocesador se refiere a una CPU contenida en un solo circuito integrado.
![[imagenes/8088.png|200]]
Tiene las siguientes características principales:
- Interfase al bus de datos de 8 bits
- Arquitectura interna de 16 bits
- Capacidad de direccionamiento de 1Mbyte (20 pines)
- Compatibilidad de Software con el 8086 CPU
- Variedad en modos de direccionamiento
- Operaciones en bloques, palabras y bytes
- Aritmética signada y no-signada de 8 y 16 bits (punto fijo), en binario, decimal, incluyendo multiplicación y división
- 14 registros de 16 bits
*El bus de datos es de 8 bits*, si bien el 8088 es un microprocesador de 16 bits. Además, está multiplexado en el tiempo, es decir, algunas líneas son de datos en un momento o direcciones de memoria en otro.
### Diagramas en bloques
![[imagenes/Diagrama en bloque 8088.png|400]]
### BIU Y EU
Las funciones internas del 8088 están divididas lógicamente en dos unidades de procesamiento: la BIU y la EU. Estas unidades pueden interactuar directamente, realizando las operaciones asincrónicamente.
1. La **Unidad de Interfaz al Bus** (BIU) cumple:
	1. Busca las instrucciones en la memoria.
	2. Llena la cola de instrucciones que consta de 4bytes (FIFO).
	3. Proporciona el control del bus.
	4. Proporciona a la EU los operandos a procesar.
	 La BIU está formado por un sumador, un conjunto de 5 registros de 16 bits y la cola de instrucciones de 4 bytes.
	
2. La **Unidad de Ejecución** (EU) recibe la instrucción buscada previamente por la BIU y se encarga de ejecutarla.
	La EU consta de una Unidad de Control (CU), la ALU y un conjunto de 9 registros de 16 bits.

El 8088 posee tres buses internos (A, B, C). La ALU posee tres registros temporarios de entrada (estando limitada una entrada a uno solo de ellos). La salida de la ALU (sin registro temporario) puede fluir por el bus a cualquier registro, incluidos los de su propia entrada. Puede realizar operaciones de 8 o 16 bits, y las condiciones resultantes son almacenadas en el registro de condiciones.
La Unidad de Control del 8088 es **microprogramada**, y posee una ROM de 504 palabras de 21 bits que almacena, aproximadamente, 90 microprocedimientos. Cada instrucción, para ejecutarse, requerirá de al menos un microprocedimiento.

Cuando la BIU detecta que el bus externo está ocioso, envía una solicitud a la memoria para leer el siguiente byte en el flujo de instrucciones. Los *bytes leídos son almacenados temporariamente* en la cola de instrucciones. Cuando la EU requiere un nuevo byte de instrucción, lo toma de esta cola. La dimensión de cuatro bytes de la cola responde al compromiso de que la EU no tenga que estar esperando por un nuevo byte por un lado. Y por otro lado, colas demasiado largas ocuparían mucho al bus llenándolas con bytes que podrían no utilizarse (por ejemplo, cuando se ejecuta una instrucción de salto).
La instrucción que se encuentra almacenada en la cola de instrucciones, es transferida al registro de instrucciones (IR), el decodificador la extrae y la disemina por la Unidad de Control. La información relacionada con la fuente y destino de los operandos se transfiere a los registros M y N. El código de operación se transfiere al registro X (para indicar a la ALU la operación a realizar) y al registro B (para indicar a la ALU si se trata de una operación de 8 o 16 bits). El código de operación también se transfiere a un combinacional (PLA) a fin de obtener la dirección de comienzo del microprocedimiento correspondiente. Cada microprocedimiento tiene como máximo 16 microinstrucciones.
Formato de microinstrucciones del 8088:
![Formato de Instrucción del 8088](imagenes/Formato%20de%20instruccion%20del%208088.png)
- Campo Fuente: Indica el registro fuente de una operación.
- Campo Destino: Indica el registro destino de una operación.
- Campo Tipo: Indica el tipo de microinstrucción:
	- Operación de la ALU
	- Operación de la memoria
	- Salto corto
	- Salto largo
	- Llamada de microprocedimiento
	- Contabilidad
- Campo ALU: indica la operación que debe realizar la ALU.
- Campo Registro: Proporciona el operando.
- Campo de Condición: Indica la activación de registro F.

Las microinstrucciones se ejecutan una por ciclo de reloj. La dirección de la primera microinstrucción a ejecutar la proporciona el código de operación de la instrucción a través de la PLA, cargando el microMAR. Se observa en la configuración de pines de la 8088 que el microMAR puede ser cargado también desde la ROM de traslación, que mapea direcciones de 5 bits y desde el registro SR. La ROM de traslación se usa cuando el microprograma requiere de un salto, y el registro SR se utiliza para guardar la dirección de retorno de una micro-subrutina.
### Registros del 8088
El 8088 tiene catorce registros que se agrupan en las siguientes tres categorías:
#### Registros Generales
Ocho registros generales de 16 bits se dividen en dos grupos:
- Cuatro regitros direccionables como de 16 bits u 8 bits:
	**AX** (Acumulador), usado para almacenar resultados de operaciones, L/E desde o hacia memoria o los puertos (AH, AL).
	**BX** (Base), usado en direccionamiento (BH, BL).
	**CX** (Contador), usado en interacciones como contador (CH, CL).
	**DX** (Datos), usado para el acceso de datos (DH, DL).
- Cuatro registros índice y registros base:
	**BP** (Puntero de base), usado en direccionamiento.
	**SI** (Ídice), usado en direccionamiento.
	**DI** (Ídice), usado en direccionamiento.
	**SP** (Puntero de pila), apunta a la última dirección de pila utilizada.
#### Registros de Segmento
Cuatro registros de 16 bits de propósitos especiales, están relacionados con la segmentación de la memoria.
	**CS** Selecciona el área de memoria destinada a las instrucciones del programa. 
	**DS** Selecciona el área de memoria destinada a los datos. 
	**SS** Selecciona el área de memoria destinada a la pila (STACK). 
	**ES** Selecciona el área de memoria destinada a dato externo.
#### Registros de control y estado
Dos registros de 16 bits de propósitos especiales:
- **F** Registro de condiciones.
- **IP** Puntero de instrucciones, indica la dirección de la próxima instrucción a ejecutar.
### Organización de la Memoria
¿Cómo direcciona con 20 bits una instrucción el 8088? Combina el registro de segmento CS y el puntero de instrucciones IP.
¿Cómo direcciona con 20 bits un dato el 8088? Combina el registro de datos DS y la dirección final o efectiva del dato.
La memoria está organizada como un conjunto de cuatro segmentos, cada **SEGMENTO** como una secuencia lineal de hasta 64 kbytes (de 0000h a FFFFh). La memoria se direcciona usando dos componentes de dirección consistentes en un *selector de segmento* de 16 bits y un *offset* de 16 bits. El primero indica el segmento seleccionado y el segundo indica el byte deseado dentro del segmento. El registro de segmento correcto es elegido automáticamente.
![[imagenes/Suma del segmento y offset.png|150]]
Las primeras 03FFh posiciones (como se verá posteriormente) se encuentran destinadas para el proceso de interrupciones. Las últimas Fh posiciones (desde la FFF0h a la FFFFh) están reservadas para operaciones que tienen que ver con la carga del programa inicial.
### Modos de Direccionamiento
En el 8088 son posibles *ocho modos* de direccionamiento para especificar operandos.
Dos de ellos son provistos para instrucciones que operan sobre registros o con operandos inmediatos:
- **Modo de operando en registro**: el operando está en uno de los registros generales (8 o 16 bits). 
	  MOV AX, DX --- (DX)→(AX)
- **Modo de operando inmediato**: el operando está incluido en la instrucción. 
	  MOV AH, 14 --- 14 → AH

Los seis modos de direccionamiento restantes permiten especificar operandos ubicados en un segmento de memoria. Como se observó, una dirección de operando en memoria posee dos componentes de 16 bits: el selector de segmento y el offset. El selector de segmento se suple por alguno de los registros de segmento, mientras que el offset se calcula por la suma de diferentes combinaciones de los siguientes tres elementos de dirección:
- el *desplazamiento*: valor de 8 o 16 bits incluido en la instrucción.
- el *base*: contenido de cualquier registro base BP o BX.
- el *índice*: contenido de cualquier registro índice SI o DI.

La combinación de estos elementos de dirección define los siguientes seis modos:
- **Modo directo**: el offset está contenido en la instrucción como un desplazamiento.
	  MOV \[14], AL --- (AL) → (DS) * 10h + 14h
- **Modo indirecto por registro**: el offset está contenido en uno de los registros BX, BP, SI o DI. 
	  MOV \[BX], CX --- (CX) → (DS) * 10h + (BX)
- **Modo basado**: el offset resulta de la suma de un desplazamiento y el contenido de BP o BX. 
	  MOV \[BP + 3], 2A --- 2A → (DS) * 10h + (BP) + 3h
- **Modo indexado**: el offset resulta de la suma de un desplazamiento y el contenido de SI o DI. 
	  MOV \[SI + 3], 2A --- 2A → (DS) * 10h + (SI) + 3h
- **Modo basado indexado**: el offset resulta de la suma del contenido de un registro base y de un registro índice.
	  MOV \[BP + SI], 2A --- 2A → (DS) * 10h + (BP) + (SI)
- **Modo basado indexado con desplazamiento**:el offset resulta de la suma del contenido de un registro base más un registro índice y un desplazamiento.
	  MOV \[BP + SI + 3], 2A --- 2A → (DS) * 10h + (BP) + (SI) + 3h
Cualquier acarreo con la suma se ignora y el desplazamiento es un valor signado.
![[imagenes/Modos de direccionamiento clase.png]]

También cabe aclarar que el offset puede obtenerse del registro IP en la búsqueda de una instrucción o en las instrucciones de salto. En este último caso, el contenido de IP puede modificarse de tres formas: 
- salto relativo: al contenido de IP se le suma un desplazamiento. 
- salto directo: al contenido de IP se lo cambia por un desplazamiento. 
- salto indirecto: el contenido de IP es cambiado por el offset obtenido por cualquiera de los modos indirectos vistos anteriormente.
### Conjunto de Instrucciones
Las instrucciones del 8088 se dividen en siete categorías:
- Transferencia de datos 
- Aritméticas
- Lógicas
- De desplazamiento y rotación
- De manipulación de cadenas.
- De control de programa
- De control del procesador
  
Una instrucción puede referirse a cero, uno o dos operandos, donde un operando puede residir en un registro, en la propia instrucción o en la memoria. Las instrucciones con cero operando (NOP, HLT) tienen un byte de longitud. Las de un operando (INC, DEC) tienen usualmente dos bytes de longitud. Las de dos operandos (MOV, ADD) usualmente tienen una longitud de tres a seis bytes y pueden hacer referencia a un registro o a una locación de memoria. Así, estas instrucciones permiten los siguientes cinco tipos de operaciones:
- registro a registro 
- memoria a registro 
- inmediato a registro 
- registro a memoria
- inmediato a memoria

Los tipos de datos que soporta el 8088 son:
- Entero: valor signado de 8 o 16 bits (Complemento a 2)
- Ordinal: sin signo de 8 o 16 bits
- Puntero: 32 bits compuesto por un selector de segmento y un offset, 16 bits cada uno
- Cadena: secuencia continua de bytes, desde 1 hasta 64Kbytes
- BCD: un byte en BCD
- BCD empaquetado: un byte representa dos dígitod BCD
### Direccionamiento de E/S
El 8088 permite operar sobre un mapa de E/S independiente del de la memoria mediante las instrucciones IN y OUT. Estas instrucciones durante su ejecución hacen la línea IO/* M a=1.
Todas las operaciones de E/S requieren al Acumulador con operando.
- AL para el caso de 8 bits.
- AX para el caso de 16 bits.
Existen dos modos de direccionamiento E/S:
##### Directo
Para los puertos de E/S: 0 a 0FFH.
El Registro (AL o AX) indica el destino del contenido del puerto referenciado.
##### Por Registro
Para los puertos de E/S: 0000H a 0FFFFH.
El Registro DX se usa como puntero, el cual no se altera después de ejecutada la instrucción IN o OUT.
### Interrupciones del 8088
Está compuesto por un *sistema de interrupciones vectorizado*. Se pueden clasificar en:
1. Interrupciones iniciadas por hardware
	- Externas
		- Enmascarables (pin INTR -> Interrupt Request)
		- No Enmascarables (pin NMI -> No Masq Interrupt)
	- Internas
2. Interrupciones iniciadas por software 
	Usan la instrucción INT XX

Una interrupción resulta en la transferencia del control a un nuevo programa.
En las primeras 1024 (03FF) posiciones de memoria reside una tabla de 256 elementos, que contiene punteros a programas de servicio de interrupción.
Cada elemento (puntero) es de 4 bytes, y se corresponde con lo que se llama tipo de interrupción. El dispositivo que interrumpe suministra, durante el proceso de reconocimiento de interrupción, un valor de 8 bits que se usa como un vector hacia el tipo de interrupción que corresponda.