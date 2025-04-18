# U3
## Digitalización de Señales
![[imgs/PCM.png]]
![[imgs/cuantificación.png]]
![[imgs/error de cuantificacion.png]]
![[imgs/codificacion.png]]
## Modulación Digital
![[imgs/Modulacion Digital.png]]

| Ventajas                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Desventajas                                                                                                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - *Gran inmunidad al ruido*: si la separación entre los niveles binarios es mayor al ruido aleatorio, el receptor puede discernir qué es señal y qué es ruido.<br>- *Facilidad de procesamiento y medición*.<br>- *Capacidad para almacenar la señal en memorias*.<br>- *La señal se puede regenerar*: al no amplificar, regeneran la señal y minimizan el ruido.<br>- *Se pueden detectar errores y corregirlos*.<br>- *Gran capacidad de adaptación con otros sistemas*: se pueden adaptar con cualquier tipo de señales. | - *Necesita un gran ancho de banda para transmitir*: se debe a que se trasmite en pulsos, tienen gran contenido de armónicos.<br>- *Requiere sincronización*.<br>- *Trae aparejado error de cuantificación*. |
![[imgs/Tipos de Modulaciones.png]]
![[imgs/Diagrama de constelaciones.png]]
![[imgs/modulaciones.png]]
$$E_{BW} = \frac{f_{m}}{BW_{min}}$$
## Técnicas de Multiplexado
![[imgs/clasificacion de los sistemas de multiplexado.png]]
- SDM: Multiplexación por división de espacio -> cada canal utiliza todo el B y durante todo el tiempo
- FDM: Multiplexación por división de frecuencia
- OFDM: Multiplexación por división de frecuencia ortogonal
- TDM: Multiplexación por división de tiempo
- WDM: Multiplexación por división de longitud de onda
- CDM: Multiplexación por división de código
![[imgs/Clasificacion Multiplexado.png]]
![[imgs/tecnicas de multiplexado.png]]
## TDM - PCM 30 + 2
Es una técnica que asigna el ancho de banda total del medio de transmisión a cada canal durante una fracción del tiempo total.
- Generalmente utilizada en sistemas de transmisión digitales.
- Cada canal multiplexado *se fracciona de una serie de muestras periódicas y ordenadas*, codificadas a flujo binario mediante la técnica estudiada PCM y moduladas mediante algún código de línea.
- Los distintos fragmentos de código, resultante del proceso anterior *son empaquetados en tramas* a las cuales se les añade cierto código adicional de control y señalización.
- Cada una de estas tramas son "encoladas" a través del medio de transmisión. Así, en el punto receptor, habrá que recoger el flujo transmitido, desentramarlo, extraer las fracciones de código de cada muestra y, para cada canal multiplexado, reconstituir el flujo original.
- Durante el proceso descrito, se requiere un perfecto entendimiento entre el punto emisor y el punto receptor, consiguiéndose mediante un proceso de *sincronismo*, que permita asignar a cada muestra su canal correspondiente.
![[imgs/tramas.png]]
---
# U4
- Condiciones para códigos de linea
## Conmutacion
![[imgs/resumen conmutacion.png]]
### Aplicación MPLS
MPLS (MultiProtocol Label Switching) es un protocolo de conmutación por etiquetas definido para funcionar sobre múltiples protocolos como Sonet, Frame Realy, ATM, Ethernet, aprovechando las eficiencias de cada uno de ellos.
![[imgs/MPLS.png]]
Se intercala entre la capa 2 y 3 del Modelo OSI y TCP/IP![[imgs/Label MPLS.png]]
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
| ![[imgs/FO.png]] | ![[imgs/FO cono de aceptacion.png]] |
### Multimodo
Multiples rayos de luz (LED)

| Multimodo de índice escalonado   | Multimodo de índice gradual   |
| -------------------------------- | ----------------------------- |
| ![[imgs/FO Multimodo escalonado.png]] | ![[imgs/FO Multimodo gradual.png]] |
### Monomodo
Un solo haz de luz (Laser)
![[imgs/Monomodo.png]]
### Ventanas de Trabajo
![[imgs/Ventanas de trabajo FO.png]]

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
GPON: recomendaciones que se describen las técnicas para compartir un medio común (FO) por varios usuarios, encapsular la información y gestionar los elementos de red, entre otros. Utiliza multiplexacion por division de longitu de onda, con comunicacion bidireccional.
- Trabaja en 1.24 Gbit/s subida y 2.48 Gbit/s bajada.
- Alcance físico máximo: 20km.
- Radio de multiplexación 1:64 y 1:128
![[imgs/GPON.png]]
![[imgs/Downstream.png]]
![[imgs/TDMA.png]]
## Topologías
- Fisicas

| Topología | Descripción                                                                                                                                                                                       | Imagen                                                   |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Bus       | Usa solo un cable backbone que debe terminarse en ambos extremos. Todos los elementos de la red se conectan directamente al backbone.                                                             | ![[imgs/Bus.png]]                                             |
| Estrella  | Conecta todos los nodos con un nodo central. Red punto a punto. Si falla un nodo, la red sigue funcionando.                                                                                       | ![[imgs/Estrella.png]]                                        |
| Anillo    | Consiste en conectar varios nodos a una red que tiene una serie de repetidores. Cuando un nodo transmite información a otro, la información pasa por cada repetidor hasta llegar al nodo deseado. | ![[imgs/Anillo.png]]                                          |
| Árbol     | Tiene varias terminales conectadas de forma que la red se ramifica desde un servidor base. Un fallo o rotura en el cable interrumpe las transmisiones                                             | ![[remote-repo/3º/Comunicacion de Datos/imgs/Arbol.png]] |
| Malla     | Se implementa para proporcionar la mayor protección posible para evitar una interrupción del servicio.                                                                                            | ![[imgs/Malla.png]]                                           |
| Mixta     | Aquella en la que se aplica una mezcla entre alguna de las otras topologías: bus, estrella o anillo. Estrella-bus o estrella-anillo.                                                              | ![[imgs/Mixta.png]]                                           |
- Logicas

| Topología | Descripción                                                                                                                                                                                                                                                                                                      | Imagen             |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| Broadcast | Cada host envía sus datos hacia todos los demás hosts del medio de red. No existe un orden que las estaciones deban seguir para utilizar la red. Es por orden de llegada, es cómo funciona el protocolo Ethernet.                                                                                                | ![[imgs/Broadcast.png]] |
| Token     | Controla el acceso a la red mediante la transmisión de un token electrónico a cada host de forma secuencial. Cuando un host recibe el token, ese host puede enviar datos a través de la red. Si el host no tiene ningún dato para enviar, transmite el token al siguiente host y el proceso se vuelve a repetir. | ![[imgs/Token.png]]     |