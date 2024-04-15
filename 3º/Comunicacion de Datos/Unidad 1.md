# Sistemas de Comunicaciones
El objetivo funamental de un sistema de comunicaciones es *transferir información de un lugar a otro*.
La comunicación es la transmisión, recepción y procesamiento de información entre dos o más lugares, mediante circuitos electrónicos.
El sistema de comunicaciones se puede representar con un diagrama simplificado.
![[imgs/Esquema sistemas de comunicaciones simplificado.png]]
- Transmisor: conjunto de uno o más dispositivos o circuitos electrónicos que convierte la información de la fuente original en una señal que es más fácil su transmisión a través de determinado medio.
- Medio de Transmisión: transporta las señales desde el transmisor hasta el receptor.
- Receptor: conjunto de dispositivos y circuitos electrónicos que acepta del medio de transmisión las señales transmitidas y las reconvierte a su forma original.
## Modulación y Demodulación
La ***modulación*** nos permite transportar señales de información con una señal analógica de mayor frecuencia, llamada *portadora*. Modular es el proceso de cambiar uno o más parámetro/s de la onda portadora, en proporción con la seña moduladora (señal de información).
La ***demodulación*** es el proceso inverso a la modulación, y reconvierte a la portadora modula en la información original. La demodulación se hace en un receptor, con un demodulador.

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
- Si la señal de información es analógica, y variamos la portadora:
	- Si se varía la amplitud de la portadora proporcionalmente a la señal de la información, produce una modulación de Amplitud (**AM**).
	- Si se varía la frecuencia de la portadora en forma proporcional a la señal de la información, se produce la modulación de Frecuencia (**FM**).
	- Si se varía la fase de la portadora en proporción con la señal de información, se produce la modulación de Fase (**PM**).
- Si la señal de información es digital, y variamos la portadora:
	- Si se varía la amplitud de la portadora proporcionalmente a la señal de la información, produce una modulación de Amplitud (**ASK** -> amplitude shift keying).
	- Si se varía la frecuencia de la portadora en forma proporcional a la señal de la información, se produce la modulación de Frecuencia (**FSK** -> frecuency shift keying).
	- Si se varía la fase de la portadora en proporción con la señal de información, se produce la modulación de Fase (**PSK** -> phase shitf keying).
	- Si se varía al mismo tiempo amplitud y fase de la portadora en proporción con la señal de información, resulta la modulación de amplitud en cuadratura (**QAM** -> quadrature amplitude modulation).
### Diagrama de bloques de un Sistema de Comunicaciones
![[imgs/diagrama de bloques.png]]
VER COMO FUNCIONA
