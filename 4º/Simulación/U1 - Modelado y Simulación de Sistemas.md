# Modelado y Simulación de Sistemas
## Modelado de Sistemas
### Introducción al modelado de sistemas
> [!info] Simulación
> La **SIMULACIÓN** se define como una técnica numérica utilizada para representar un proceso o fenómeno mediante otro más simple que permite analizar sus caracterísiticas.

Esto se utiliza para mejorar procesos, diseñar productos, planificar operaciones y prever resultados en entornos controlados y seguros.
La finalidad de la simulación no es optimizar, sino comparar los distintos escenarios, modificando el valor de las variables, para así encontrar posibles mejoras que se pueden implementar en el sistema real o sistema de análisis. Es importante resaltar que es una representacipon aproximada de la realidad.
### Ventajas
- No existe el sistema real -> la simulación es el único medio para lograr una solución
- Los experimentos son imposibles debido a impedimentos económicos, de seguridad, de calidad o éticos -> fallas en un avión
- Se puede utilizar para analizar un sistema propuesto o experimentar en el sistema real sin perturbar el sistema actual
- El sistema evoluciona muy lentamente o muy rápidamente -> evolución del clima o una explosión
- No se tiene el modelo matemático definido
- Proporciona un método más simple de solución cuando los procedimientos matmáticos son complejos y difíciles
- Puede ser aplicado repetidamente para varios tipos de experimentación, aunque la simulación pueda ser costosa
- Frecuentemente es menos costoso obtener datos de una simulación que del sistema real
### Desventajas
- Posibilidad de cometer errores
- No se puede conocer el grado de imprecisión de los resultados
- Al empezar a simular se puede interferir en las operaciones del sistema
- Difícil simpre obtener el mismo tamaño de muestra
- Se requiere gran cantidad de corridas computacionales para encontrar soluciones óptimas -> costoso
- Los modelos de simulación no generan soluciones ni respuestas a ciertas preguntas
- El desarrollo de un modelo puede ser costoso, laborioso porque requiere validación y desarrollo
### Consideraciones a tener en cuenta para modelar
- Tamaño insuficiente de la corrida -> para llegar a conclusiones estadísticas válidas es necesario que las variables aleatorias de respuesta se encuentren en estado estable. El problema es que si tenemos más de una variable, no pueden estar todas estables
- Variables de respuesta mal definidas -> si la variable de respuesta seleccionada no es la apropiada, será imposible tomar decisioens que tengan impacto en la operación
- Errores al determinar el tipo de distribución asociado a las variables aleatorias del modelo -> Falta de un análisis estadístico de los resultados. Un problema común por el que la simulación suele ser objeto de crítica, radica en asumir que se trata de una herramienta de optimización
- Uso incorrecto de la información obtenida -> la información no siempre está en el formato y presentación que se requiere para la simulación
- Falta o exceso de detalle
### Tratamiento analítico y numérico de un modelo matemático
Si las variables y sus relaciones dentro de un sistema son lo bastante simples, es probable que se pueda encontrar un modelo matemático reconocido que pueda describir el sistema y proporcionar información precisa sobre los aspectos relevantes -> solución **analítica** -> no es necesario recurrir a una simulación.
> [!missing] Simulación
> En la gran mayoría de casos de sistemas reales, la complejidad de las interacciones e interrelaciones entre las variables es tal que no suele hallarse una solución **analítica** adecuada. En estos casos una práctica común y muchas veces la única a la mano, es la **SIMULACIÓN** del sistema de interés.

> [!info] Métodos Numéricos
> Los **MÉTODOS NUMÉRICOS** corresponden a un conjunto de herramientas o métodos usados para obtener una solución de problemas matemáticos de forma aproximada. Se aplican principalmente a problemas que no presentan una solución exacta, por lo tanto precisan ser resueltos numéricamente.

### Sistemas y Modelos
> [!info] Sistema
> La definición básica de **SISTEMA** nos dice que se trata de un conjunto de elementos que se interrelacionan para funcionar como un todo. Desde el punto de vista de la simulación, tales elementos deben tener una frontera clara.

- **ENTIDADES** ->  son los objetos de interés que constituyen el sistema (responsables de que el estado del sistema cambie)
- **ATRIBUTOS** -> son las propiedades que caracterizan a las entidades componentes del sistema
- **ESTADO DEL SISTEMA** -> es la caracterización de las entidades del sistema y sus atributos en un instante dado (condición que guarda el sistema en un instante de tiempo dado)
- **ACTIVIDADES** -> son procesos que provocan cambios en el sistema
	- *ENDÓGENAS* ->ocurren dentro del sistema. Las variables endógenas son aquellas determinadas dentro del modelo, es decir, son resultado de las interacciones y procesos internos del sistema que se está simulando. Son las que podemos simular
	- *EXÓGENAS* -> ocurren en el medio ambiente y afectan al sistema. Las variables exógenas son aquellas externas al modelo cuyos valores son dados como parámetros de entrada al sistema. Influyen en el comportamiento del sistema, pero su valor no es determinado por las relaciones internas del modelo de simulación. Hay que tenerlas en cuenta al momento de modelar.
- **MEDIO AMBIENTE** -> es el exterior del sistema. Es importante establecer los límites entre el medio ambiente y el sistema.

> [!info] Modelo
> Un **MODELO** es una abstracción de la realidad.
> Un **MODELO** es una representación de la realidad que ayuda a entender cómo funciona.
> Un **MODELO** es una construcción intelectual y descriptiva de una entidad en la cual un observador tiene interés. Se construye para ser transmitido. Supuestos simples son usados para capturar el comportamiento importante.

### Tipos de Modelos
1. Según el **cambio con el tiempo**
	- *Dinámicos* -> utilizados para representar sistemas cuyo estado varía con el tiempo.
	  ![[img/dinamico.png]]
	- *Estáticas* -> utilizados para representar sistemas cuyo estado estado es invariable a través del tiempo.$$P(x) = ax{^2} + bx + c$$
2. Según su **forma de representación**
	- *Matemáticos* -> la realidad es representada en forma abstracta de diversas maneras. Se usan funciones matemáticas
	  ![[img/matematico.png]]
	- *Físicos* -> la realidad es representada por algo tangible, construido en escala o que por lo menos se comporta en forma análoga a esa realidad
	  ![[img/fisico.png]]
3. Según su **resolución**
	- *Analíticos* -> la realidad se representa por fórmulas matemáticas, mediante la resolución de ecuaciones con métodos matemáticos exactos.
	  ![[img/analitico.png]]
	- *Numéricos* -> se utilizan métodos computacionales para aproximar soluciones a través de cálculos iterativos.
	  ![[img/numerico.png]]
4. Según sus **variables**
	- *Continuos* -> representan sistemas cuyos cambios de estado son graduales. Las variables intervenientes son continuas.
	  ![[img/continua.png]]
	- *Discretos* -> representan sistemas cuyos cambios de estado son de a saltos. Las variables varían en forma discontinua.
	  ![[img/discreto.png]]
5. Según su **comportamiento**
	- *Determinístico* -> son modelos cuya solución para determinadas condiciones es única y siempre la misma
	  ![[img/deterministico.png]]
	- *Estocástico* -> son modelos donde los hechos suceden al azar, lo cual no es repetitivo. No se puede asegurar cuáles acciones ocurren en un determinado instante.
	  ![[img/estocastico.png]]
6. Según su **relación con el medio ambiente**
	- *Lazo Abierto* -> las entradas del sistema determinan completamente su comportamiento y no se tienen en cuenta las salidas o resultados para ajustar o modeficar las entradas.
	  ![[img/lazo abierto.png]]
	- *Lazo Cerrado* -> las salidas o resultados se usan para modificar o ajustar las entradas.
	  ![[img/lazo cerrado.png]]
7. Según su **relación con variables internas o externas**
	- *Abierto* -> tienen actividades exógenas. La entrada es externa al modelo e independiente. Interactúan en forma dinámica con el entorno.
	  ![[img/abierto.png]]
	- *Cerrado* -> no tiene actividades exógenas. No hay entrada externa.
	  ![[img/cerrado.png]]
8. Según su **naturaleza**
	- *Concreto* -> la naturaleza corresponde a un sistema físico o tangible (sistema de sonido, edificio) -> Hardware
	- *Abstracto* -> la naturaleza corresponde a un sistema simbólico o conceptual (sistema hexadecimal, idioma español, lógica difusa) -> Software
	  ![[img/abstracto y conceptual.png]]
9. Según su **origen**
	- *Natural* -> el origen es generado por la naturaleza (bosques, moléculas de agua)
	- *Artificial* -> en contraste con el de origen natural, éste es producto de la actividad del hombre (avión, edificio, idioma)
### Simulación de sistemas discretos, continuos y basados en agentes
|                            |                                                                         |                                                                                  |                                                                                    |
| -------------------------- | ----------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Enfoque**                | **Continuo**                                                            | **Discreto**                                                                     | **Basado en Agentes**                                                              |
| **Características**        | Modela sistemas donde las variables cambian continuamente en el tiempo. | Modela sistemas donde los cambios ocurren en puntos específicos en el tiempo.    | Modela la interacción de individuos autónomos en un entorno.                       |
|                            | Apropiado para sistemas con evolución fluida y gradual.                 | Se centra en eventos discretos y su impacto en el sistema.                       | Cada agente sigue reglas y toma decisiones basadas en el entorno y otros agentes.  |
| **Ejemplos de aplicación** | Dinámicas de población, procesos químicos, flujo de tráfico.            | Movimiento de productos en almacenes, planificación de rutas, sistemas de colas. | Propagación de enfermedades, análisis de mercados, comportamiento de consumidores. |
| Software usado             | Vensim                                                                  | Arena                                                                            | Python - Analogic                                                                  |
### Etapas de la simulación
El proceso de simulación se divide en varias etapas clave:
1. **Formulación del problema:** Se acuerdan los objetivos, variables, perturbaciones, métodos estadísticos y uso del simulador entre cliente y desarrollador.
2. **Definición del sistema:** Se delimita el sistema y sus interacciones con el entorno.
3. **Formulación del modelo:** Se crea un modelo inicial que captura los aspectos relevantes, refinándose iterativamente.
4. **Colección de datos:** Se obtienen y procesan los datos necesarios desde diversas fuentes, adaptándolos al modelo.
5. **Implementación del modelo:** Se codifica el modelo en un lenguaje de programación o se utiliza software especializado.
6. **Verificación:** Se asegura que la implementación esté libre de errores mediante herramientas de depuración.
7. **Validación:** Se compara el comportamiento del modelo con datos reales o históricos para garantizar su exactitud.
8. **Diseño de experimentos:** Se definen parámetros de simulación como tiempos y número de réplicas.
9. **Experimentación:** Se ejecutan las simulaciones, ajustando el modelo si es necesario.
10. **Interpretación:** Se analizan los resultados y la sensibilidad del modelo, refinando parámetros críticos si es preciso.
11. **Implementación:** Se acompaña al cliente para asegurar el correcto uso del simulador y sus resultados.
12. **Documentación:** Se elabora documentación técnica y manuales para facilitar mejoras futuras y asegurar el buen manejo del simulador.
#### Fortalezas
- Mejorar la toma de decisiones
- Reducir costos
- Identificación de cuellos de botella y áreas de mejora
- Evaluación de sistemas complejos
- Reducción de riesgos
- Optimización de procesos
- Predicción de resultados futuros
- Visualización y comunicación de resultados
- Mejor planificación y programación
- Flexibilidad en el análisis