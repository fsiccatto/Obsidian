# Gray

| Decimal | 2bits | 3 bits | 4 bits |
|:-------:|:-----:|:------:|:------:|
|    0    |  00   |  000   |  0000  |
|    1    |  01   |  001   |  0001  |
|    2    |  11   |  011   |  0011  |
|    3    |  10   |  010   |  0010  |
|    4    |       |  110   |  0110  |
|    5    |       |  111   |  0111  |
|    6    |       |  101   |  0101  |
|    7    |       |  100   |  0100  |
|    8    |       |        |  1100  |
|    9    |       |        |  1101  |
|   10    |       |        |  1111  |
|   11    |       |        |  1110  |
|   12    |       |        |  1010  |
|   13    |       |        |  1011  |
|   14    |       |        |  1001  |
|   15    |       |        |  1000  |
# Johnson
| Decimal | Johnson |
|:-------:|:-------:|
|    0    |  00000  |
|    1    |  00001  |
|    2    |  00011  |
|    3    |  00111  |
|    4    |  01111  |
|    5    |  11111  |
|    6    |  11110  |
|    7    |  11100  |
|    8    |  11000  |
|    9    |  10000  |
# BCD
| Decimal | BCD Natural |  BCD AIKEN  | BCD Exceso 3 |
|:-------:|:-----------:|:-----------:|:------------:|
|         |  **8421**   |  **2421**   |  **n + 3**   |
|    0    |    0000     |    0000     |     0011     |
|    1    |    0001     |    0001     |     0100     |
|    2    |    0010     |    0010     |     0101     |
|    3    |    0011     |    0011     |     0110     |
|    4    |    0100     |    0100     |     0111     |
|    5    |    0101     |    1011     |     1000     |
|    6    |    0110     |    1100     |     1001     |
|    7    |    0111     |    1101     |     1010     |
|    8    |    1000     |    1110     |     1011     |
|    9    |    1001     |    1111     |     1100     |
|         | *Ponderado* | *Ponderado* |   *Libre*    |
# ASCII
![[ASCII.png|500]]
# Detectores de Errores
| Decimal | 2 entre 5 | Biquinario  |
|:-------:|:---------:|:-----------:|
|         | **7421P** | **5043210** |
|    0    |   11000   |   0100001   |
|    1    |   00011   |   0100010   |
|    2    |   00101   |   0100100   |
|    3    |   00110   |   0101000   |
|    4    |   01001   |   0110000   |
|    5    |   01010   |   1000001   |
|    6    |   01100   |   1000010   |
|    7    |   10001   |   1000100   |
|    8    |   10010   |   1001000   |
|    9    |   10100   |   1010000   |
# Correctores de Errores
## Hamming
### Tabla Correctora
| Condicion de error | c3  | c2  | c1  |
|:------------------:|:---:|:---:|:---:|
|    Sin errores     |  0  |  0  |  0  |
|   Error en el b1   |  0  |  0  |  1  |
|   Error en el b2   |  0  |  1  |  0  |
|   Error en el b3   |  0  |  1  |  1  |
|   Error en el b4   |  1  |  0  |  0  |
|   Error en el b5   |  1  |  0  |  1  |
|   Error en el b6   |  1  |  1  |  0  |
|   Error en el b7   |  1  |  1  |  1  |
### Código Hamming
| Decimal | *b7* *b6* *b5* | b4  | *b3*  | b2 b1 |
|:-------:|:--------:|:---:|:---:|:-----:|
|    0    |  0 0 0   |  0  |  0  |  0 0  |
|    1    |  0 0 0   |  0  |  1  |  1 1  |
|    2    |  0 0 1   |  1  |  0  |  0 1  |
|    3    |  0 0 1   |  1  |  1  |  1 0  |
|    4    |  0 1 0   |  1  |  0  |  1 0  |
|    5    |  1 0 1   |  0  |  1  |  0 1  |
|    6    |  1 1 0   |  0  |  0  |  0 1  |
|    7    |  1 1 0   |  0  |  1  |  1 0  |
|    8    |  1 1 1   |  1  |  0  |  0 0  |
|    9    |  1 1 1   |  1  |  1  |  1 1  |
$`b_3, b_5, b_6 \space y \space b_7`$ son los bits del código original *Aiken*, mientras que los bits restantes se forman de acuedo a las condiciones de paridad (en este caso, par).
### Códigos Bidimensionales
Se presenta el código bidimensional, a las filas se agregan bits Hamming y al código de columnas se le agrega un bit de paridad.
El código de filas tendrá `Dm = 3` ya que es código Hamming, el código de las columnas tendrá una `Dm = 2` ya que es un código de paridad.
![[código bidimensional.png|300]]
A fin de determinar la `Dm` del código Bidimensional podríamos encontrar un patrón de bits de error que no sea detectado por el receptor. En el caso del código horizontal habrá que cambiar 3 bits, en el caso del vertical sólo 2 bits. Por lo que `Dm = 6`. Podemos generalizar:
$$
	D_m (bidimensioanl) = D_m(filas) x D_m(columnas)
$$