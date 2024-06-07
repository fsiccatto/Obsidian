# U3
## Digitalización de Señales
![[PCM.png]]
![[cuantificación.png]]
![[error de cuantificacion.png]]
![[codificacion.png]]
## Modulación Digital
![[Modulacion Digital.png]]

| Ventajas                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Desventajas                                                                                                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - *Gran inmunidad al ruido*: si la separación entre los niveles binarios es mayor al ruido aleatorio, el receptor puede discernir qué es señal y qué es ruido.<br>- *Facilidad de procesamiento y medición*.<br>- *Capacidad para almacenar la señal en memorias*.<br>- *La señal se puede regenerar*: al no amplificar, regeneran la señal y minimizan el ruido.<br>- *Se pueden detectar errores y corregirlos*.<br>- *Gran capacidad de adaptación con otros sistemas*: se pueden adaptar con cualquier tipo de señales. | - *Necesita un gran ancho de banda para transmitir*: se debe a que se trasmite en pulsos, tienen gran contenido de armónicos.<br>- *Requiere sincronización*.<br>- *Trae aparejado error de cuantificación*. |
![[Tipos de Modulaciones.png]]
![[Diagrama de constelaciones.png]]
$$E_{BW} = \frac{f_{m}}{BW_{min}}$$
## Técnicas de Multiplexado
![[clasificacion de los sistemas de multiplexado.png]]
- SDM: Multiplexación por división de espacio
- FDM: Multiplexación por división de frecuencia
- OFDM: Multiplexación por división de frecuencia ortogonal
- TDM: Multiplexación por división de tiempo
- WDM: Multiplexación por división de longitud de onda
- CDM: Multiplexación por división de código
## TDM - PCM 30 + 2
Es una técnica que asigna el ancho de banda total del medio de transmisión a cada canal durante una fracción del tiempo total.
- Generalmente utilizada en sistemas de transmisión digitales.
- Cada canal multiplexado *se fracciona de una serie de muestras periódicas y ordenadas*, codificadas a flujo binario mediante la técnica estudiada PCM y moduladas mediante algún código de línea.
- Los distintos fragmentos de código, resultante del proceso anterior *son empaquetados en tramas* a las cuales se les añade cierto código adicional de control y señalización.
- Cada una de estas tramas son "encoladas" a través del medio de transmisión. Así, en el punto receptor, habrá que recoger el flujo transmitido, desentramarlo, extraer las fracciones de código de cada muestra y, para cada canal multiplexado, reconstituir el flujo original.
- Durante el proceso descrito, se requiere un perfecto entendimiento entre el punto emisor y el punto receptor, consiguiéndose mediante un proceso de *sincronismo*, que permita asignar a cada muestra su canal correspondiente.
![[tramas.png]]
---
# U4
- Condiciones para códigos de linea
## Conmutacion
![[resumen conmutacion.png]]
### Aplicación MPLS
MPLS (MultiProtocol Label Switching) es un protocolo de conmutación por etiquetas definido para funcionar sobre múltiples protocolos como Sonet, Frame Realy, ATM, Ethernet, aprovechando las eficiencias de cada uno de ellos.
![[MPLS.png]]
Se intercala entre la capa 2 y 3 del Modelo OSI y TCP/IP![[Label MPLS.png]]
La idea es **rutear en los bordes y Conmutar en el Núcleo de la red** en cuestión. De esta forma, en los **bordes tenemos Datagramas y en el nucleo Circuitos Virtuales**. Esta aplicación es la que hoy en día hace posible la implementación de redes de datos de alta capacidad, como LTE referido a 4G y 5G en redes móviles.

---
# U5
## MNG
Según aislación (trabaja sobre $\frac{S}{N}$):
- UTP
- FTP
- STP
- SFTP
- SSTP
Categorías de cables (trabaja sobre $B$):
- Categoría 1- frecuencia máxima de 1MHz.
- Categoría 2- frecuencia máxima de 4MHz.
- Categoría 3- Velocidad de transmisión de 10 Mbps y frecuencia máxima de 16 MHz.
- Categoría 4- hasta 20 Mbps y frecuencia máxima de 20 MHz.
- Categoría 5- hasta 100 Mbps y frecuencia máxima de 100 MHz
- Categoría 6- hasta 1 Gbps y frecuencia máxima de 250 MHz
- Categoría 7- hasta 10 Gbps y frecuencia máxima de 600 MHz
## FO
| n1 > n2     | Cono de Aceptación             |
| ----------- | ------------------------------ |
| ![[FO.png]] | ![[FO cono de aceptacion.png]] |
### Multimodo
Multiples rayos de luz (LED)

| Multimodo de índice escalonado   | Multimodo de índice gradual   |
| -------------------------------- | ----------------------------- |
| ![[FO Multimodo escalonado.png]] | ![[FO Multimodo gradual.png]] |
### Monomodo
Un solo haz de luz (Laser)
![[Monomodo.png]]
### Ventanas de Trabajo
![[Ventanas de trabajo FO.png]]

| 1º Ventana                                 | 2º Ventana                                           | 3º Ventana                                         |
| ------------------------------------------ | ---------------------------------------------------- | -------------------------------------------------- |
| $850nm$                                    | $1300nm$                                             | $1550nm$                                           |
| LED                                        | LÁSER                                                | LÁSER                                              |
| ETH/LAN con FO multimodo                   | FO monomodo                                          | FO monomodo                                        |
| Tendidos no mayores a 1-2km, Tx económicos | Tendidos urbanos, los enlaces no son mayores a 20 km | Tendidos interurbanos, enlaces mayores a los 20 km |
-led
-haz de luz

| Ventajas                                                                                                                                                                                                                                                  | Desventajas                                                                                                                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - Inmunidad al ruido electromagnético<br>- Transmisión de datos a alta velocidad<br>- Gran ancho de banda <br>- Ocupa menor espacio que el coaxial y par trenzado<br>- Video y sonido con mejor performance<br>- Compatibilidad con la tecnología digital | - Costo alto de la conexión<br>- Costo alto de instalación<br>- Flexibilidad en la fibra<br>- Mayor complejidad a la hora de empalmar<br>- Alta complejidad en reparación de rotura de cable |
## GPON
![[GPON.png]]