# Sistemas de Comunicaciones
El objetivo funamental de un sistema de comunicaciones es *transferir información de un lugar a otro*.
La comunicación es la transmisión, recepción y procesamiento de información entre dos o más lugares, mediante circuitos electrónicos.
El sistema de comunicaciones se puede representar con un diagrama simplificado.
![[imgs/Esquema sistemas de comunicaciones simplificado.png]]
- Transmisor: conjunto de uno o más dispositivos o circuitos electrónicos que convierte la información de la fuente original en una señal que es más fácil su transmisión a través de determinado medio.
- Medio de Transmisión: transporta las señales desde el transmisor hasta el receptor.
- Receptor: conjunto de dispositivos y circuitos electrónicos que acepta del medio de transmisión las señales transmitidas y las reconvierte a su forma original.
## Modulación y Demodulación
La ***modulación*** nos permite transportar señales de información con una señal analógica de mayor frecuencia, llamada *portadora*. Modular es el proceso de cambiar uno o más parámetro/s de la onda portadora, en proporción con la señal moduladora (señal de información).
La ***demodulación*** es el proceso inverso a la modulación, y reconvierte a la portadora modulada en la información original. La demodulación se hace en un receptor, con un demodulador.

> [!info] ¿Por qué modulamos?
> 1. Es muy difícil irradiar señales de baja frecuencia en forma de energía electromagnética con una antena, ya que los criterios de diseño de antena están dados en $\frac{\lambda}{4} \text{ y } \frac{\lambda}{2}$. Por lo tanto, a bajas frecuencias, tendríamos antenas gigantescas $c= \lambda f$.
> 3. Las señales de la información ocupan la misma banda de frecuencia y si se transmiten al mismo tiempo las señales de dos o más fuentes interferirán entre sí. Nos permite elegir frecuencias portadoras para poder transmitir distintos tipos de información.
### Tipos de Sistemas de Comunicaciones
| Sistema Analógico                                              | Sistema Digital                                                                                                                             |
| :------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------ |
| La energía se transmite y recibe en forma analógica.           | Amplia variedad de técnicas de comunicación que incluyen transmisión digital y radio digital.                                               |
| Tanto la información como la portadora son señales analógicas. | Es un sistema digital donde los pulsos digitales (señales discretas) se transfieren entre dos o más puntos en un sistema de comunicaciones. |
### Tipos de Modulación/Demodulación
La expresión:
$$v(t) = V(2 \pi ft+\theta)$$
es la descripción general de una onda senoidal de voltaje variable en el tiempo, como puede ser una *señal portadora* de alta frecuencia.
> [!tip] RESUMEN
>  ![[imgs/resumen modulacion.png]]
- Si la señal de información es **analógica**, y variamos la portadora:
	- Si se varía la amplitud de la portadora proporcionalmente a la señal de la información, produce una modulación de Amplitud (**AM**).
	- Si se varía la frecuencia de la portadora en forma proporcional a la señal de la información, se produce la modulación de Frecuencia (**FM**).
	- Si se varía la fase de la portadora en proporción con la señal de información, se produce la modulación de Fase (**PM**).
- Si la señal de información es **digital**, y variamos la portadora:
	- Si se varía la amplitud de la portadora proporcionalmente a la señal de la información, produce una modulación de Amplitud (**ASK** -> amplitude shift keying).
	- Si se varía la frecuencia de la portadora en forma proporcional a la señal de la información, se produce la modulación de Frecuencia (**FSK** -> frecuency shift keying).
	- Si se varía la fase de la portadora en proporción con la señal de información, se produce la modulación de Fase (**PSK** -> phase shitf keying).
	- Si se varía al mismo tiempo amplitud y fase de la portadora en proporción con la señal de información, resulta la modulación de amplitud en cuadratura (**QAM** -> quadrature amplitude modulation).
### Diagrama de bloques de un Sistema de Comunicaciones
![[imgs/diagrama de bloques.png]]
VER COMO FUNCIONA
## Fuentes Contaminantes
Son efectos indeseados e inevitables.
- *Distorsión*: es la alteración de la señal debida a la respuesta imperfecta del sistema. La solución implica compensar dichas alteraciones para que la distorsión sea aceptable.
- *Interferencia*: son señales de forma similar a la de la señal original de información, no deseadas por el usuario. La solución viene por el lado de interrumpir la fuente que genera la señal interferente.
- *Ruido*: es una señal aleatoria e impredecible originada de forma natural. No existe solución a éste problema, pero podemos compensarlo.
# Espectro Electromagnético
El espectro total útil de radiofrecuencias (RF) se divide en bandas de frecuencia más angostas, a las que se dan nombres y números descriptivos, y algunas de ellas se subdividen a su vez en diversos tipos de servicios.
![[imgs/RF.png]]

| Frecuencias                      | Mínimo  | Máximo  |
|:---------------------------------|:--------|:--------|
| ELF (extremely low frequencies)  |   30 Hz |  300 Hz |
| VF (voice frequencies)           |  300 Hz | 3000 Hz |
| VLF (very low frequencies)       |   3 kHz |  30 kHz |
| LF (low frequencies)             |  30 kHz | 300 kHz |
| MF (medium frequencies)          | 300 kHz |   3 MHz |
| HF (high frequencies)            |   3 MHz |  30 MHz |
| VHF (very high frequencies)      |  30 MHz | 300 MHz |
| UHF (ultrahigh frequencies)      | 300 MHz |   3 GHz |
| SHF (superhigh frequencies)      |   3 GHz |  30 GHz |
| EHF (extremely high frequencies) |  30 GHz | 300 GHz |  
![[imgs/RF2.png]]
### Longitud de Onda
La longitud de onda $\lambda$ es la distancia que ocupa en el espacio un ciclo de una onda electromagnética. La longitud de onda es inversamente proporcional a la frecuencia de la onda, y directamente proporcional a su velocidad de propagación $\lambda = \frac{c}{f}$.
# Modos de Transmisión
- Serie -> mayor distancia, menos velocidad, más barato
- Paralelo -> menor distancia, más velocidad, más caro
### Modo Símplex
Las transmisiones sólo se hacen en una dirección. Es decir, pueden **sólo recibir o sólo transmitir**. Una estación puede ser un transmisor o un receptor, pero no ambos a la vez. Ejemplo: radio, tv.
$$Tx \to Rx$$
### Modo Half Duplex
Las transmisiones se pueden hacer en ambas direcciones, pero **no al mismo tiempo**. Una estación puede ser transmisora y receptora, pero no al mismo tiempo. Ejmplo: handys (un canal para T o R).
$$\frac{Tx}{Rx} \leftrightarrow \frac{Rx}{Tx}$$
### Modo Full Duplex
Transmisiones en ambas direcciones al mismo tiempo. Una estación puede transmitir y recibir en forma **simultánea**. Ejemplo: telefono (dos canales).
$$Tx \leftrightarrow  Rx$$
$$Rx \leftrightarrow Tx$$
![[imgs/trasnmisiones.png]]
# Series de Fourier
Este estudio es *válido para ondas periódicas no senoidales o cosenoidales*.
Cualquier forma de onda periódica está formada por un componente promedio, valor constante, y una serie de ondas senoidales y cosenoidales relacionadas armónicamente. Una armónica es un múltiplo entero de la frecuencia fundamental. La frecuencia fundamental es la *primera armónica*.
> [!note] ¿Para qué sirve?
> Se utiliza para pasar una señal al dominio de frecuencia para así obtener información que no es evidente en el dominio temporal.
> La transformada de Fourier es una fórmula matemática que **transforma una señal muestreada en tiempo o espacio con la misma señal muestreada en frecuencia temporal o espacial**.