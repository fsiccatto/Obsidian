## Asíncronos
### Biestable Asíncrono SR
![[Biestable SR.png]]

|  R  |  S  | Qt  | Qt+1 |
|:---:|:---:|:---:|:----:|
|  0  |  0  |  0  |  0   |
|  0  |  0  |  1  |  1   |
|  0  |  1  |  0  |  1   |
|  0  |  1  |  1  |  1   |
|  1  |  0  |  0  |  0   |
|  1  |  0  |  1  |  0   |
|  1  |  1  |  0  |  X   |
|  1  |  1  |  1  |  X   |

#### Analogía
Sistema Digital para una alarma domiciliaria:
- Dos variables de entrada:
	- Variable S: entrada de sensor
	- Variable R: entrada de inicialización
- Una variable de salida:
	- Variable Q salida a la sirena
$$
Q_{t+1} = \sum_{3}(1, 2, 3, 6, 7) \text{ o } Q_{t+1} = \prod_{3}(0, 1, 2, 3, 7)
$$
Por Karnaugh podemos hacer las simplificaciones y nos queda:
$$
Q_{t+1} = S + Q_{t}\overline{R} = \overline{\overline{S+Q_{t}\overline{R}}}
$$
Se denomina SET-RESET o SR Asíncrono. Se puede ver que las salidas están cruzadas.
Las compuertas lógicas reales se diferencian de las ideales en:
1. Poseen un tiempo de retardo, es decir: la señal lógica tarda un tiempo para atravesar la compuerta.
2. Disipan calor.
## Síncronos
### Biestable Síncrono Activados por nivel
Son aquellos en los cuales la tabla de verdad es válida sólo en presencia de un nivel activo en la entrada de sincronismo.
![[Biestable SR Activado por nivel.png]]
### Biestable Síncrono Maestro - Esclavo
Formado por 2 biestables activados por nivel. 
- Cuando `Ck = 1` funciona el primer biestable maestro. 
- Cuando `Ck = 0` la información del maestro pasa al esclavo.
Este biestable actúa como si estuviera activado en el flanco de bajada de la señal de sincronismo, las entradas actúan sobre el maestro mientras `Ck = 1`.
![[Biestable Maestro-Esclavo.png]]
### Biestable Activados por flancos
Las entradas actúan sólo en presencia de un flanco (de subida o bajada) en la entrada de sincronismo. Por lo que la tabla de verdad será válida en esos instantes.
Se trata de un SR síncrono por nivel al cual se le agrega un circuito detector de flancos.
![[Biestable Activado por flancos.png]]
#### Tipos de Biestables
### Biestables J-K
|  K  |  J  | Qt+1 |
|:---:|:---:|:----:|
|  0  |  0  |  Qt  |
|  0  |  1  |  1   |
|  1  |  0  |  0   |
|  1  |  1  | Qt'  |

![[Biestable JK.png]]
Para J=K=1, Qt+1=Qt', es decir que la salida adopta el valor opuesto anterior.
### Biestables T
|  T  | Qt+1 |
|:---:|:----:|
|  0  |  Qt  |
|  1  |  Qt'   |
No están disponibles comercialmente. Se obtienen a partir de un biestable JK haciendo J=K=T. También pueden obtenerse a partir de un biestable D por flancos.
### Biestables D
|  D | Qt+1 |
|:---:|:----:|
|  0  |  0  |
|  1  |  0   |
Este Biestable **carece** de aplicación. Pueden obtenerse a partir de un SR síncrono, haciendo S = R’ = D. También desde un JK, haciendo J = K’ = D.
![[Biestable D.png]]