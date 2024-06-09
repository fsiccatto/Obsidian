# 1-Modulacion por codificacion de pulsos (PCM)
El codificador PCM tiene tres procesos:
1. Se muestrea la señal analogica
2. Se cuantifica la señal muestreada
3. Los valores cuantificados son codificados como flujos de bits
## Muestreo
En esta etapa la señal analogica es muestreada cada cierto Ts (intervalo de muestreo). El teorema de Nyquist nos dice que para muestrar y luego reproducir esa señal analogica necesitamos que:
$$f_{s} \geq 2f_{max}$$
donde fs es la frecuencia de muestreo.
Necesitamos que la señal a muestrear este en una banda finita para establecer fmax y que la frecuencia de muestreo sea por lo menos 2 veces mayor que la fmax
## Cuantificación
Consiste en transformar los valores continuos de amplitud en la señal PAM en valores discretos para poder codificarlos. Es decir, cada valor continuo de amplitud se aproximara al valor discreto mas cercano.
Aparece un erro de cuantificacion que es la diferencia entre la señal de entrada y la señal cuantificada. Depende de la cantidad de niveles discretos dentro del intervalo en consideracion.
## Codificacion
Luego que de la muestra ha sido cuantificada y se ha decidido el numero de bits a utilizar por muestra, a cada muestra se le asigna una palabra de un codigo de "n bits"
# 2-Ventajas y Desventajas de modulacion digital
| Ventajas                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Desventajas                                                                                                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - *Gran inmunidad al ruido*: si la separación entre los niveles binarios es mayor al ruido aleatorio, el receptor puede discernir qué es señal y qué es ruido.<br>- *Facilidad de procesamiento y medición*.<br>- *Capacidad para almacenar la señal en memorias*.<br>- *La señal se puede regenerar*: al no amplificar, regeneran la señal y minimizan el ruido.<br>- *Se pueden detectar errores y corregirlos*.<br>- *Gran capacidad de adaptación con otros sistemas*: se pueden adaptar con cualquier tipo de señales. | - *Necesita un gran ancho de banda para transmitir*: se debe a que se trasmite en pulsos, tienen gran contenido de armónicos.<br>- *Requiere sincronización*.<br>- *Trae aparejado error de cuantificación*. |
# 3-Baudio y Tasa de bit
El término tasa de bits es la *velocidad de transferencia de datos* de un sistema de transmisión digital.
Un baudio puede contener varios bits ya que es el *número de unidades de información por segundo*.
$Baudio = \frac{f_{b}}{N}, f_{b}=\frac{1}{t_{b}}, t_{b}: \text{ tiempo de bit}$
$M=2^N$ donde M son los simbolos de un modular. Dependiendo de los numeros de bit por simbolo (N) es el modulado que vamos a utilizar.
# 4-Diagrama de Constelacion
Un diagrama de constelacion es una representacion de un esquema de modulacion digital en plano complejo. Los ejes reales e imaginarios son "en fase" y "en cuadratura". Los puntos en la constelacion representan los simbolos de modulacion que componen el alfabeto. Dado un alfabeto de m simbolos, cada uno lleva informacion correspondiente a $\log_{2}(m) \space bits$.
# 5-Multiplexacion
Es la tecnica de combinar dos o mas señales y transmitirlas por un solo medio de transmision. Se utiliza un multiplexor para su implementacion.
Permite aprovechar al maximo el ancho de banda y asi transmitir varias comunicaciones de forma simultanea.
Tecnicas
- SDM: Multiplexación por división de espacio
- FDM: Multiplexación por división de frecuencia
- OFDM: Multiplexación por división de frecuencia ortogonal
- TDM: Multiplexación por división de tiempo
- WDM: Multiplexación por división de longitud de onda
- CDM: Multiplexación por división de código
# 6-Conmutacion
El conmutador es un dispositivo importante, ya que cumple la funcion de conectar los usuarios entre si
- Garantizar que llegue la informacion
- Debe ser transparente al usuario
- Debe ser rapida
## Conmutacion de paquetes
Los mensajes se dividen en paquetes (cada uno con un encabezado). El canal es compartido por muchos usuairos, se caracteriza porque los datos son ensamblados en forma de paquetes. Cuando llegan, los paquetes son reensambaldos.
- Ventajas
	- comparte enlaces
	- se tarifca por tiempo de utilizacion
	- son mas rapidos que la conmutacion de mensajes
	- se trabaja casi en tiempo real
- Desventajas
	- hace falta un protocolo de comunicacion
	- se pueden perder paquetes, caso de datagramas
### Circuitos Virtuales (Orientados a la conexión)
En esta técnica, el emisor envía un paquete de control, conocido como paquete de llamada, éste será el encargado de establecer un camino virtual por donde pasarán todos los paquetes de datos. De esta manera llegan en orden establecido por el emisor.
### Datagramas (NO orientados a la conexión)
En esta técnica el emisor **enumera cada paquete**, se caracteriza porque cada paquete puede tomar rutas distintas, y por lo tanto pueden llegar en distinto orden, o también se pueden perder paquetes. El trabajo del receptor es **ordenar los paquetes**.
# 7-FO
El funcionamiento se basa en transmitir por el nucleo de la FO un haz de luz, tal que no atraviese el nucleo, sino que se refleje y siga propagandose. Esto se consigue si n1>n2 y si el angulo de incidencia no es mayor al angulo limite, que esta dado por el cono de aceptacion.
## Ventanas de Trabajo
El origen de esta curva es debido a las características físicas del material (silicio) de la FO. la FO presenta picos de atenuación importantes en las ventanas 950 nm, 1240 nm y, la más importante de todas, en cuanto atenuación es 1380 nm.
GRAFICO

| 1º Ventana                                 | 2º Ventana                                           | 3º Ventana                                         |
| ------------------------------------------ | ---------------------------------------------------- | -------------------------------------------------- |
| $850nm$                                    | $1300nm$                                             | $1550nm$                                           |
| LED                                        | LÁSER                                                | LÁSER                                              |
| ETH/LAN con FO multimodo                   | FO monomodo                                          | FO monomodo                                        |
| Tendidos no mayores a 1-2km, Tx económicos | Tendidos urbanos, los enlaces no son mayores a 20 km | Tendidos interurbanos, enlaces mayores a los 20 km |
# 8-GPON
PON (Passive Optical Network), red optica punto-multipunto. No existen elementos activos entre la OLT (Optical Line Terminal) y el ONT (Optical Network Termination).
GPON recomendaciones que se describen las tecnicas para compartir un medio comun (FO) por varios usuarios, encapsular la ifnormacion y gestionar los elemtnso de red.
Utiliza multiplexacion por division de longitud de onda, facilitando la conmutacion bidireccional sobre una sola FO.
-  Trabaja en 1.24 Gbit/s subida y 2.48 Gbit/s bajada.
- Alcance físico máximo: 20km.
- Radio de multiplexación 1:64 y 1:128
## Downstream
En direccion de bajada los paquetes de datos son transmitidos por broadcast, GRAFICO
Broadcast: Cada host envía sus datos hacia todos los demás hosts del medio de red. No existe un orden que las estaciones deban seguir para utilizar la red. Es por orden de llegada, es cómo funciona el protocolo Ethernet.
## Upstream
En direccion de subida los paquetes de datos son transmitidos por TDMA (Time Division Multiplexing Access), GRAFICO
# 9-WIFI
Wireless Fidelity. Objetivo: proporcionar una conexion a internet y a redes locales sin la necesidad de calbes, facilitando la movilidad y la flexibilidad en el acceso a la informacion.
- Banda de 2.4 GHz
	Mayor alcance, pero menor capacidad de datos comparada con la de 5GHz.
	- Tiene mejor penetración de la señal electromagnética a través de paredes y otros obstáculos.
	- Más suceptible a interferencias debido a la saturación y uso compartido con otros dispositivos.
- Banda de 5GHz
	Mayor capacidad de datos, pero menor alcance que la banda de 2.4GHz
	- Menos congestión y más canales disponibles, reduce las interferencias.
	- Menor capacidad de penetración a través de los obstáculos físicos.
Utiliza OFDM Técnica de multiplexación que divide el espectro de frecuencia en múltiples subportadoras ortogonales, cada una transmitiendo una parte de la señal.
# 10-Satelites
Son redes que utilizan como medios de transmisión satélites artificiales puestos en órbita alrededor de la tierra. Actuan como grandes espejos de las ondas recibidas y enviadas desde la estacion terrestre.
La principal **ventaja** de estos es lograr establecer enlaces de comunicación con áreas que por otros métodos es imposible ya sea por distancia o limitaciones geográficas.
Como **desventaja**, son sistemas muy costosos. El retardo de señal puede llegar a ser de 1.5 segundos.

Los satélites son puestos en diferentes órbitas como pueden ser las siguientes:
- LEO 600-1600km Starklink
- MEO 10000-20000km se usan para posicionamiento
- GEO 35848km son los mas utilizados - comunicaciones
- HEO orbitas elipticas - cartografiar la tierra