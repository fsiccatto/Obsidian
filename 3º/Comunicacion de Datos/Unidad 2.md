# Teoría de la Información
> [!info] Objetivo
> - Se ocupa de la medición de la información
> - La capacidad de los sistemas para transmitir y procesar información
> - Garantiza el transporte masivo de datos sin merma de la calidad
> - No perder ninguna información transmitida
## Transmisión de la Información
- Teoría de la información: nace con la necesidad de saber la capacidad de los Sistemas de Comunicaciones de llevar información. Se centra en las señales eléctricas y su contenido de información.
- Fuentes: es todo aquello que emite mensajes
	- Estructurada: posee cierto nivel de redundancia.
	- No estructurada: los mensajes no se pueden comprimir sin que haya una pérdida de mensaje.
- Mensaje: datos enviados. Conjunto de 0 y 1.
- Código: conjunto de 1 y 0 que se usan para representar un cierto mensaje. Información contenida en el mensaje $S$, es la *cantidad mínima de bits para codificar un mensaje*.
- Información: es simplemente lo que produce la fuente para transferir al usuario. Es *proporcional a la cantidad de bits*.
	- La ocurrencia de mensajes de alta probabilidad de aparición aporta menos información que la ocurrencia de mensajes menos probables. A medida que la probabilidad de ocurrencia del mensaje sea mayor, menor información contendrá el mismo.
### Cantidad de Información
La cantidad de información esta relacionada con probabilidad de ocurrencia $p$, dado por:
$$ I = \log_{n}\left( \frac{1}{p} \right)$$

| Sistemas | Información  |
| :------- | :----------- |
| n = 2    | I en bits    |
| n = 10   | I en Hartley |
| n = e    | I en nat     |
### Entropía de la Fuente
El nivel de información de una fuente se puede medir según la entropía de la misma.
La entropía de la fuente es la base de la compresión de datos.
Para codificar los mensajes de una fuente se utilizará: 
	Menor cantidad de bits → para los mensajes más probables
	Mayor cantidad de bits → para los mensajes menos probables
$$H = \sum_{j=1}^mp_{j}I_{j} = \sum_{j=1}^mp_{j}\log_{2}\left( \frac{1}{p_{j}} \right)$$
- La entropía de la fuente determina la *compresión que podemos aplicar*.
- Se demuestra que *no es posible comprimir un mensaje más allá de su entropía* (Shannon).
- El **objetivo** de la compresión de datos es encontrar los $𝑰_{j}$ que minimizan a $H$.
- Los $𝑰_{j}$ se determinan en función de las $𝒑_{j}$ , pues la longitud de los códigos dependen de la probabilidad de ocurrencia de los mismos.
### Ancho de Banda
Es una caracterísitica importante ya que **determina la capacidad del canal**, para la transferencia de información dentro de una rango de frecuencias.
$$ B = f_{2} - f_{1} \text{ [Hz]}$$
![[imgs/ancho de banda.png]]
### Capacidad de Canal
##### Capacidad de Canal SIN Ruido - Nyquist
Nyquist planteó la existencia de un límite en la capacidad de un canal ideal (sin ruido ni distorsiones) de ancho de banda finito. Establece que la *velocidad máxima de transmisión de datos* en bps viene limitada por la siguiente expresión:
$$C=2B\log_{2}(M)$$
C: capacidad de canal en bps
B: ancho de banda en Hz
M: número de niveles posible de la señal -> corresponde al número de señales diferentes que sale de un modulador digital
- Si n = 2 entonces: $M = 2^N \implies C = 2B$

> [!caution] Nota
> Para aumentar la capacidad de canal se deben incrementar los niveles de tensión, M.
> Cuanto mayor es la velocidad de transmisión, mayor es el daño que puede ocasionar el ruido.
> No representa los efectos causados por el ruido, en un canal de comunicaciones real.
##### Capacidad de Canal CON Ruido - Shannon
El teorema de Shannon es:
$$C=B\log_{2}\left( 1+ \frac{S}{N} \right)$$
C: velocidad máxima en bits por segundo
B: ancho de banda
S/N: relación señal a ruido
Este es límite teórico impuesto por el teorema de Shannon, porque nunca lo han igualado.
###### Aplicaciones
Cableado Estructurado
	![[imgs/cableado estructurado.png]]
Mejora continua en medios de transmisión
	Los medios de transmisión continuamente están *aumentando las velocidades máximas disponibles*, la forma en que lo consiguen es o bien *mejorando el ancho de banda o bien mejorando la relación señal a ruido*.

> [!tldr] Comparación Teorema de Shannon con Nyquist
> Comparando la capacidad del canal de Shannon con la tasa de información de Nyquist, podemos encontrar el número eficaz de los niveles distinguibles o estados de modulación M.
> $$2B\log_{2}(M) = B \log_{2}\left( 1+\frac{S}{N} \right)$$
> $$ M = \sqrt{ 1 + \frac{S}{N} }$$

# Señales Analógicas y Digitales
## Señales Analógicas
Las señales analógicas son *continuas en tiempo y amplitud*. Representan variaciones físicas y se pueden describir como una *función continua en un período determinado*. Ejemplo común es la señal de audio en un disco de vinilo, donde las variaciones en la forma de la onda representan diferentes sonidos.
- Naturaleza Continua -> la SA no tiene interrupciones y fluye de forma constante.
- Representación -> mediante una onda sinusoidal continua en función del tiempo.
- Suceptibilidad al ruido -> son más suceptibles a la interferencia y al ruido.
- Alacenamiento y transmisión -> pueden ser difíciles de almacenar y transmitir en comparación con SD.
## Señales Digitales
Las señales digitales, por otro lado, tienen una *naturaleza discreta*. Se representan mediante una *serie de valores discretos*, típicamente 0 y 1, y se transmiten en forma de pulsos. Ejemplo común es la música en formato MP3, donde los datos se almacenan en forma digital.
- Naturaleza Discreta -> tiene valores definidos en puntos específicos en el tiempo.
- Representación -> mediante una serie de valores binarios (0 y 1).
- Resistencia a ruido -> son menos susceptibles al ruido y la interferencia.
- Almacenamiento y transmisión -> más fáciles de almacenar y transmitir, manteniendo la calidad.
## Impacto Tecnológico
Dependerá de la aplicación específica, la necesidad de precisión, el entorno de transmisión y otros factores.
- Telecomunicaciones : Las señales digitales han ganado prominencia en las telecomunicaciones debido a su resistencia al ruido y facilidad de transmisión . Esto ha llevado a una mayor calidad en las comunicaciones móviles y por Internet.
- Audio y video: las señales digitales permiten una mayor portabilidad y acceso en dispositivos modernos.
- Medicina : En el campo médico, las señales digitales facilitan la captura y el análisis de datos.
- Automatización Industrial : La utilización de señales digitales en la automatización industrial permite un control preciso y en tiempo real de maquinarias y procesos.
# Banda Base
Banda de frecuencias producidas por un transductor. Ejemplo: micrófono, telégrafo.
## Tipos de Banda Base
![[imgs/tipos de banda base.png]]

| Banda Base               | Banda Ancha                  |     |
| :----------------------- | :--------------------------- | --- |
| Transmite solo una señal | Transmite más de una señal   |     |
| No es decodificada       | Es decodificada y regenerada |     |
| Recursos limitados       | Recursos amplios             |     |
| Activo / Inactivo        | Siempre activo               |     |
![[imgs/banda ancha vs banda base.png]]