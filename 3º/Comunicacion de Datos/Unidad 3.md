# Modulación Digital
Es la transmisión de un mensaje entre dos puntos del sistema de comunicación modulando la señal portadora con señal digital, como esto se hace en banda base, se requiere un medio de enlace entre el transmitor y el receptor (par trenzado, coaxial o fibra óptica).
La modulación digital, es el proceso de cambiar una de las características de una portadora analógica modulando con señal digital.
![[Modulacion Digital.png]]

| Ventajas                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Desventajas                                                                                                                                                                                                  |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - *Gran inmunidad al ruido*: si la separación entre los niveles binarios es mayor al ruido aleatorio, el receptor puede discernir qué es señal y qué es ruido.<br>- *Facilidad de procesamiento y medición*.<br>- *Capacidad para almacenar la señal en memorias*.<br>- *La señal se puede regenerar*: al no amplificar, regeneran la señal y minimizan el ruido.<br>- *Se pueden detectar errores y corregirlos*.<br>- *Gran capacidad de adaptación con otros sistemas*: se pueden adaptar con cualquier tipo de señales. | - *Necesita un gran ancho de banda para transmitir*: se debe a que se trasmite en pulsos, tienen gran contenido de armónicos.<br>- *Requiere sincronización*.<br>- *Trae aparejado error de cuantificación*. |
![[Tipos de Modulaciones.png]]

| Modulación digital binaria                                                                                                                                      | Modulación digital multinivel<br>                                                                                                                                                                                                    |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Se denomina así porque el sistema binario aparece directamente como modulación de la portadora, es decir, que a cada bit le corresponde un baudio en la salida. | Se denomina así porque el sistema binario no aparece directamente como modulación de la portadora, sino que se lo convierte a un sistema multinivel para modular. Es decir, que un baudio en la salida representa varios bits.&nbsp; |
| - ASK<br>- FSK<br>- PSK                                                                                                                                         | - m-PSK<br>- m-QAM                                                                                                                                                                                                                   |
### Relación entre Baudio y Tasa de bit entrada
- Bits: pieza más pequeña de información.
- Baudio: unidad de símbolos de señal por seg.
	- Tasa de bits N\[bps]: número de bits transmitidos por segundo.
	- Tasa de señal S\[baudio]: número de símbolos por segundo.
		- S = tasa de bits / número de bits por elemento de la señal
		$Baudio = \frac{f_{b}}{N}, f_{b}=\frac{1}{t_{b}}, t_{b}: \text{ tiempo de bit}$
El término tasa de bits es la *velocidad de transferencia de datos* de un sistema de transmisión digital.
Un baudio puede contener varios bits ya que es el *número de unidades de información por segundo*.
## Diagramas de Constelación
Un diagrama de constelación es una representación de un esquema de modulación digital en plano complejo. Los ejeres real e imaginario son "en fase" y "cuadratura". Los *puntos* en la constelación representan los símbolos de modulación que componen el alfabeto, es decir, todas las "palabras" que podrán usarse en un intercambio de información. Dado un alfabeto de $m$ símbolos, cada uno lleva la información correspondiente a $\log_{2}(m) \space bits$.
![[Diagrama de constelaciones.png]]
## Eficiencia del ancho de banda
La eficiencia de ancho de banda es una medida utilizada para comparar el funcionamiento de dos técnicas de modulación digital. Indica la cantidad de bits por seg que se pueden propagar a través de un medio por cada hertz de ancho de banda.
$$E_{BW} = \frac{f_{m}}{BW_{min}}$$
![[Modulaciones]]
# Digitalización de Señales
## Digitalización de señales analógicas
Las señales analógicas pueden convertirse en digitales, y viceversa. Para convertir una señal analógica en digital, se utiliza un dispositivo llamado conversor Analógico / Digital (o conversor A/D).
## Modulación por codificación de pulsos (PCM)
Es una de las técnicas más usadas para cambiar una señal analógica a digital. El codificador PCM tiene tres procesos:
1. Se *muestrea* la señal analógica
2. Se *cuantifica* la señal muestreada
3. Los valores cuantificados son *codificados* como flujos de bits
![[PCM.png]]
### Muestreo
En esta etapa la señal analógica es muestreada cada $T_{s}$, donde $T_{s}$ es el intervalo de muestreo o período de muestreo. La inversa es la *frecuencia* o tasa de muestreo $f_{s}$, definida en el Teorema de Nyquist. Este teorema nos dice que para muestrar y luego reproducir la señal analógica orginal es necesario que:
$$T_{s} = \frac{1}{f_{s}}\leq \frac{1}{2f_{max}} \text{ Relación de Nyquist}$$
#### Conclusión del Teorema de Nyquist
- En primer lugar, establece que la señal a muestrar debe estar en una banda finita. Es decir, debemos poder identificar una $f_{max}$ de valor finito.
- La frecuencia de muestreo $f_{s}$ debe ser al menos 2 veces la frecuencia más alta contenida en la señal a muestrear $f_{max}$. De esta manera la señal muestreada contiene toda la información de la señal original.
$$f_{s} \geq 2f_{max}$$
### Cuantificación
Consiste en **transformar los valores continuos** (infinitos valores dentro de un intervalo) de amplitud presentes en la señal PAM **en valores discretos** (cantidad finita de valores dentro de ese mismo intervalo), para poder codificarlos. Es decir, cada valor continuo de amplitud se aproximará al valor discreto más cercano.
![[cuantificación.png]]
#### Error de Cuantificación
El error de cuantificación *es la diferencia entre la señal de entrada y la señal cuantificada*. Este error no se puede disminuir a menos que aumente la cantidad de niveles discretos dentro del intervalo en consideración. Pero aumentar la cantida de niveles discretos tiene un límite: cuando el error de cuantificación se compara con el ruido, no existirá certeza de que la información recuperada es correcta. Entonces, **el máximo ruido permitido es igual al valor máximo posible del error de cuantificación mínimo**.
![[error de cuantificacion.png]]
### Codificación
La codificación es la última etapa en PCM. Luego de que la muestra ha sido cuantificada, y se ha decidido el número de bits a utilizar por muestra, a cada muestra se le asigna una palabra de un código de “n bits”.
![[codificacion.png]]
# Técnicas de Multiplexado
Es la técnica de combinar dos o más señales, y transmitirlas por un solo medio de transmisión. Para su implementación se emplean un multiplexor.
Permite aprovechar al máximo el Ancho de Banda disponible y así transmitir varias comunicaciones de forma simultánea.
![[clasificacion de los sistemas de multiplexado.png]]
- SDM: Multiplexación por división de espacio
- FDM: Multiplexación por división de frecuencia
- OFDM: Multiplexación por división de frecuencia ortogonal
- TDM: Multiplexación por división de tiempo
- WDM: Multiplexación por división de longitud de onda
- CDM: Multiplexación por división de código
# TDM - PCM 30+2
## Multiplexación por división de tiempo
Es una técnica que asigna el ancho de banda total del medio de transmisión a cada canal durante una fracción del tiempo total.
- Generalmente utilizada en sistemas de transmisión digitales.
- Cada canal multiplexado *se fracciona de una serie de muestras periódicas y ordenadas*, codificadas a flujo binario mediante la técnica estudiada PCM y moduladas mediante algún código de línea.
- Los distintos fragmentos de código, resultante del proceso anterior *son empaquetados en tramas* a las cuales se les añade cierto código adicional de control y señalización.
- Cada una de estas tramas son "encoladas" a través del medio de transmisión. Así, en el punto receptor, habrá que recoger el flujo transmitido, desentramarlo, extraer las fracciones de código de cada muestra y, para cada canal multiplexado, reconstituir el flujo original.
- Durante el proceso descrito, se requiere un perfecto entendimiento entre el punto emisor y el punto receptor, consiguiéndose mediante un proceso de *sincronismo*, que permita asignar a cada muestra su canal correspondiente.
- 30 canales vocales, a los que se les incorpora un canal para señalización y otro para alineación, generándose una trama final de 32 canales o muestras.
![[TDM.png]]
