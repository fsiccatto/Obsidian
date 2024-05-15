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
