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