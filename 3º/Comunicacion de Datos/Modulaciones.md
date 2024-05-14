# Modulación Digital Binaria
## Modulación por desplazamiento de amplitud (ASK)
Es una modulación de amplitud donde la señal moduladora (datos) es digital. Los dos valores binarios (0 y 1) se representan con dos amplitudes diferentes. *Uno de los dígitos binarios se representa mediante la presencia de la portadora a amplitud constante, y el otro dígito se representa mediante la ausencia de la señal portadora*, en este caso la frecuencia y la fase se mantiene constante.
![[ASK.png]]
## Modulación por desplazamiento de frecuencia (FSK)
Modulación de frecuencia cuya señal modulante es un flujo de pulsos binarios que varía entre valores predeterminados, en los sistemas de modulación por salto de frecuencia. La señal moduladora hace variar la frecuencia de la portadora, de modo que *la señal modulada resultante codifica la información asociándola a valores de frecuencia diferentes*.
$$v(t) = V_{c}\cos[\omega_{c}.t+v_{m}(t).\Delta \omega.t]$$
![[FSK.png]]
## Modulación por desplazamiento de fase (PSK)
Consiste en hacer variar la fase de la portadora entre dos valores discretos.
![[PSK.png]]
- Existe un desplazamiento de fase entre los símbolos de este sistema de modulación.
- El 1 lógico que produce un desplazamiento de fase de 𝟏𝟖𝟎° 𝝅. El cero lógico, no produce desfasaje de la portadora 𝟎°.
- Margen de ruido grande.
![[PSK constelaciones.png]]
# Modulación Digital Multinivel
La cantidad de condiciones posibles de salida para diversos valores de N se muestra en la siguiente tabla.
$$N=\log_{2}M$$
N: cantidad de bits codificados
M: cantidad de condiciones posibles de salida con N bits

| N     | M     |
| :---- | :---- |
| 1<br> | 2     |
| 2     | 4<br> |
| 3     | 8     |
| 4     | 16    |
| 5     | 32    |
