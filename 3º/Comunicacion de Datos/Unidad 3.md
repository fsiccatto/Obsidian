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
- $$f_{s} \geq 2f_{max}$$
### Cuantificación
### Decodificación