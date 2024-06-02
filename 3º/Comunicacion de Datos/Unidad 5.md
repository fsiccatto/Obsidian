# Medios de Transmisión de Datos
## Medios de Transmisión Guiados
### Par Trenzado
Un par trenzado está formado por dos conductores, generalmente de cobre, cada uno con su aislamiento de plástico. El aislamiento de plástico tiene asignado un color, con el fin de poder identificar los pares.
## Medios de Transmisión NO Guiados
### Par Trenzado UTP
Es un tipo de cable que tiene dos conductores eléctricos aislados y entrelazados para **anular las interferencias de fuentes externas y diafonía de los cables adyacentes**.
Existen distintos tipos de categorías según la asilación (trabaja sobre $\frac{S}{N}$):
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
### Fibra Óptica
Se aplican las leyes de la óptica geométrica (ley de reflexión, principio de reflexión interna total, y a la ley de Snell).  El funcionamiento se basa en transmitir por el núcleo de la FO un haz de luz, tal que este no atraviese el núcleo, sino que se refleje y siga propagándose. Esto se consigue si $n_{1} > n_{2}$ y si el ángulo de incidencia no es superior al ángulo límite, este ángulo límite estará dado por el **cono de aceptación**.

| n1 > n2     | Cono de Aceptación             |
| ----------- | ------------------------------ |
| ![[FO.png]] | ![[FO cono de aceptacion.png]] |
|             |                                |
#### Tipos de Fibra Óptica
##### Multimodo
Se denomina así porque hay múltiples rayos de luz de una fuente luminosa que se mueven a través del núcleo por caminos distintos, dependiendo de la estructura del núcleo.

| Multimodo de índice escalonado | Multimodo de índice gradual          |
| ------------------------------ | ------------------------------------ |
| ![[FO Multimodo escalonado.png]]          | ![[FO Multimodo gradual.png]] |
##### Monomodo
Se fabrica con un diámetro mucho más pequeño que las fibras multimodo y con una densidad (índice de refracción) sustancialmente menor. Por lo tanto, la propagación de los distintos rayos es casi idéntica, los rayos llegan "juntos" a destino y se pueden recombinar sin distorsionar la señal.
![[Monomodo.png]]
#### Ventanas de Trabajo
![[Ventanas de trabajo FO.png]]
El origen de esta curva es debido a las características físicas del material (silicio) de la FO. la FO presenta picos de atenuación importantes en las ventanas 950 nm, 1240 nm y, la más importante de todas, en cuanto atenuación es 1380 nm.

| 1º Ventana                                 | 2º Ventana                                           | 3º Ventana                                         |
| ------------------------------------------ | ---------------------------------------------------- | -------------------------------------------------- |
| $850nm$                                    | $1300nm$                                             | $1550nm$                                           |
| LED                                        | LÁSER                                                | LÁSER                                              |
| ETH/LAN con FO multimodo                   | FO monomodo                                          | FO monomodo                                        |
| Tendidos no mayores a 1-2km, Tx económicos | Tendidos urbanos, los enlaces no son mayores a 20 km | Tendidos interurbanos, enlaces mayores a los 20 km |
#### Fuentes de luz para cables ópticos
El dispositivo emisor debe estar equipado con una **fuente luminosa** y el dispositivo receptor con una **célula fotosensible** capaz de traducir la luz recibida en corriente que pueda ser usada en una computadora.
- LED: fuente más barata, luz desenfocada y se difumina con la distancia. Se utiliza para distancias cortas
- Láser: se pueden enfocar en un rango muy estrecho. Se utiliza para distancias considerables.
#### Ventajas y Desventajas
| Ventajas                                                                                                                                                                                                                                                  | Desventajas                                                                                                                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - Inmunidad al ruido electromagnético<br>- Transmisión de datos a alta velocidad<br>- Gran ancho de banda <br>- Ocupa menor espacio que el coaxial y par trenzado<br>- Video y sonido con mejor performance<br>- Compatibilidad con la tecnología digital | - Costo alto de la conexión<br>- Costo alto de instalación<br>- Flexibilidad en la fibra<br>- Mayor complejidad a la hora de empalmar<br>- Alta complejidad en reparación de rotura de cable |
# Redes GPON - FTTH
## Terminología
- PON: Passive Optical Network. Red óptica punto-multipunto. No existen elementos activos entre la OLT y el equipo terminal ONT.
- GPON: recomendaciones que se describen las técnicas para compartir un medio común (FO) por varios usuarios, encapsular la información y gestionar los elementos de red, entre otros.
- OLT: Optical Line Terminal. Equipo central.
- ONT/ONU: Optical Network Termination. Equipo de usuario.
## Funcionamiento
GPON utiliza multiplexación por división de longitud de onda, facilitando la comunicación bidireccional sobre una sola fibra. 
- Trabaja en 1.24 Gbit/s subida y 2.48 Gbit/s bajada.
- Alcance físico máximo: 20km.
- Radio de multiplexación 1:64 y 1:128
![[GPON.png]]
Para separar las señales de subida y bajada de múltiples usuarios en una sola FO, GPON adopta dos mecanismos:
- En dirección de bajada (Downstram), los paquetes de datos son transmitidos por **broadcast**.
![[Downstream.png]]
- En dirección de subida (Upstream), los paquetes de datos son transmitidos mediante **TDMA** (Time Division Multiplexing Access)
![[TDMA.png]]
Se pueden utilizar muchos servicios por este medio como Internet, telefonía fija, IPTV, RPV, Trama IP, TX, IoT. Lo que separa a estos servicios es VLAN.
# Topologías
## Físicas
| Topología | Descripción                                                                                                                                                                                       | Imagen            |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| Bus       | Usa solo un cable backbone que debe terminarse en ambos extremos. Todos los elementos de la red se conectan directamente al backbone.                                                             | ![[Bus.png]]      |
| Estrella  | Conecta todos los nodos con un nodo central. Red punto a punto. Si falla un nodo, la red sigue funcionando.                                                                                       | ![[Estrella.png]] |
| Anillo    | Consiste en conectar varios nodos a una red que tiene una serie de repetidores. Cuando un nodo transmite información a otro, la información pasa por cada repetidor hasta llegar al nodo deseado. | ![[Anillo.png]]   |
| Árbol     | Tiene varias terminales conectadas de forma que la red se ramifica desde un servidor base. Un fallo o rotura en el cable interrumpe las transmisiones                                             | ![[remote-repo/3º/Comunicacion de Datos/imgs/Arbol.png]]    |
| Malla     | Se implementa para proporcionar la mayor protección posible para evitar una interrupción del servicio.                                                                                            | ![[Malla.png]]    |
| Mixta     | Aquella en la que se aplica una mezcla entre alguna de las otras topologías: bus, estrella o anillo. Estrella-bus o estrella-anillo.                                                              | ![[Mixta.png]]    |
## Lógicas
| Topología | Descripción                                                                                                                                                                                                                                                                                                      | Imagen             |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| Broadcast | Cada host envía sus datos hacia todos los demás hosts del medio de red. No existe un orden que las estaciones deban seguir para utilizar la red. Es por orden de llegada, es cómo funciona el protocolo Ethernet.                                                                                                | ![[Broadcast.png]] |
| Token     | Controla el acceso a la red mediante la transmisión de un token electrónico a cada host de forma secuencial. Cuando un host recibe el token, ese host puede enviar datos a través de la red. Si el host no tiene ningún dato para enviar, transmite el token al siguiente host y el proceso se vuelve a repetir. | ![[Token.png]]     |

