# Clasificación y Representación de sistemas para la automatización
## Introducción a los sistemas de control
**Controlar** un sistema implica tener la capacidad de gestionar y mejorar los procesos de manera eficiente, permitiendo a las organizaciones adaptarse rápidamente a los cambios y demandas del mercado.
> [!info] Sistema
>  Un sistema es una combinación de componentes que actúan interconectados, para cumplir un determinado objetivo.
>  Podemos verlo como una caja negra y variables que actúan sobre el sistema. Podemos pensar en sistemas como la relación de entradas-salidas.
>  ![[sistema.png]]

Un **sistema de control** es una configuración estructurada y coordinada de componentes que recibe **entradas**, **procesa** estas **entradas** y **genera salidas** para influir en el **comportamiento** de un sistema con el fin de alcanzar un **objetivo** específico, generalmente utilizando mecanismos de **retroalimentación** para mantener la **estabilidad** y compensar las **perturbaciones**.
### Modelado
Mediante el modelado, podemos codificar el funcionamiento interno de un sistema, creando representaciones matemáticas que capturan sus dinámicas y comportamientos.
> [!info] Modelado
>  El modelado de sistemas proporciona una comprensión profunda y detallada de cómo operan los sistemas, permitiendo su control y mejora continua.
#### Modelado Entrada-Salida
Se basa en la idea de que, para cualquier entrada dada, el sistema generará una salida específica.
Se representa matamáticamente por la **Función de Transferencia**.
### Control
> [!info] Control
>  Un **sistema de control** es el conjunto de elementos, que hace posible que otro sistema, proceso o planta permanezca fiel a un programa establecido.

Los elementos de un sistema de control trabajan juntos para **monitorear, regular y ajustar** el **comportamiento** del sistema objetivo, asegurando que opere de acuerdo con las especificaciones deseadas.
#### Características Principales
- Entradas $\to$ señales de entrada que se desean controlar o afectan el comportamiento del sistema
- Salidas $\to$ respuestas del sistema controlado, resultan del procesamiento de entradas
- Controlador $\to$ procesa las entradas y determina las acciones necesarias para obtener la salida deseada
- Sistema de Controlado $\to$ dispositivo cuya conducta se desea controlar (planta)
- Retroalimentación $\to$ parte de la salida se devuleve a la entrada para ajustarla y corregir cualquier desviación del estado deseado
- Perturbaciones $\to$ factores externos que afectan al sistema y deben ser compensados por el controlador
### Señales
> [!info] Señal
>  En un sistema de control, una **señal** se puede definir como una **representación física** de una cantidad variable que transmite **información** sobre el estado o el comportamiento del sistema.
>  Características comunes:
>  - Dependencia de Variables: son funciones de una o más variables independientes
>  - Portadoras de Información: contienen infromación sobre la naturaleza del fenómeno físico.

| Tipo de señal eléctrica | Descripción                                                                                 | Gráfica                  |
| :---------------------- | :------------------------------------------------------------------------------------------ | ------------------------ |
| Señal analógica         | Número infinito de valores que tiene una variación continua en el tiempo.                   | ![[señal analogica.png]] |
| Señal digital           | Número finito de valores que tiene una variación discreta de valores en el tiempo.          | ![[señal digital.png]]   |
| Señal digital binaria   | Dos valores concretos: 1 y 0. La señal eléctrica sólo puede adoptar dos niveles de tensión. | ![[señal binaria.png]]   |
### Lazo abierto y  lazo cerrado
#### Lazo abierto
La entrada se elige en base en la experiencia que se tiene con dichos sistemas para producir el valor de salida requerido. **No existe retroalimentación**.
![[Lazo abierto.png]]
Ventajas $\to$ son más sencillos y de bajo costo, y con buena confiabilidad
Desventajas $\to$ son inexactos y se deben reemplazar si se descomponen
#### Lazo cerrado
Se tiene una señal de retroalimentación hacia la entrada desde la salida, la cual se utiliza para modificar la entrada de modo que la salida se mantenga constante a pesar de los cambios en las condiciones de operación.
![[Lazo cerrado.png]]
Ventajas $\to$ más exactos y menos sensible a las perturbaciones y a los cambios en las características de los componentes. La velocidad de respuesta se incrementa.
## Clasificación de los sistemas de control
### Sistema Lineal (L)
> [!info] Sistema lineal
> Un sistema se define como lineal si cumple con dos principios fundamentales:
> - Principio de **homogeneidad** (proporcionalidad o escabilidad)
> - Principio de **superposición** (o aditividad).
#### Principio de Homogeneidad
El sistema cumple con el principio de homogeneidad si **la entrada multiplicada por un escalar** produce una la **salida del sistema multiplicada por el mismo escalar**.
![[principio de homogeneidad.png]]
#### Principio de Superposición
El sistema cumple con el **principio de superposición** si **dos entradas son sumadas y pasadas a través del sistema lineal**, la **salida** será equivalente a la **suma de las dos entradas evaluadas individualmente**.
![[principio de superposicion.png]]
### Sistema Invariante en el Tiempo (TI)
> [!info] Sistema invariante en el tiempo
> Un sistema invariante en el tiempo TI (Time-Invariant) tiene la propiedad de que cierta entrada siempre dará la misma salida, independientemente del momento en que fue aplicada al sistema.
> ![[sistema invariante en el tiempo.png]]

En un sistema invariante en el tiempo, ambas salidas serán idénticas, excepto que la segunda figura estará **retrasada en $t_{0}$**.
Si un sistema es invariante en el tiempo puede ser descripto por **ecuaciones diferenciales**. Los sistemas invariantes en el tiempo son modelados con ecuaciones de **coeficientes constantes**.
### Sistema Lineal Invariante en el Tiempo (LTI)
![[sistema lineal invariante en el tiempo.png]]
Como los sistemas LTI son subconjuntos de los sistemas lineales, éstos obedecen al **principio de superposición**. El efecto de aplicar el tiempo invariante a la definición de sistema lineal de la sección anterior es el siguiente:
![[LTI superposicion.png]]
### Sistema Causal
> [!info] Sistema causal
> Un sistema es causal si no depende de valores futuros de las entradas para determinar la salida.

Esto significa que si **la primera entrada es recibida en tiempo $t_{0}$, el sistema no deberá dar ninguna salida hasta ese tiempo**.
Un sistema causal es un tipo de sistema en el cual la salida del sistema en cualquier instante de tiempo $t$ depende únicamente de las entradas presentes y pasadas, y no de las futuras.
### Sistema Inversible
> [!info] Sistema inversible
> Un sistema es invertible si distintas entradas producen distintas salidas.

Dicho de otra forma, un sistema es invertible si al **observar su salida podemos determinar la entrada**. Es decir, que podemos recuperar las entradas originales a partir de las salidas observadas.
### Sistema sin Memoria
> [!info] Sistema sin memoria
> Un sistema es sin memoria si su salida para cada valor de su variable independiente depende sólo de la entrada en ese mismo instante de tiempo.

Un sistema **sin** memoria depende únicamente de la entrada actual.
Un sistema **con** memoria depende de las entradas y/o estados anteriores además de la entrada actual. El sistema guarda información sobre las entradas y/o estados anteriores, lo que le permite tener "memoria" de su comportamiento pasado.
## Modelo de sistema en el espacio de estado
