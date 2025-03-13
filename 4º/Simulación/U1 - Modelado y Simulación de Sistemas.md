# Modelado y Simulación de Sistemas
## Modelado de Sistemas
### Introducción al modelado de sistemas
> [!info] 
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
> [!missing]
> En la gran mayoría de casos de sistemas reales, la complejidad de las interacciones e interrelaciones entre las variables es tal que no suele hallarse una solución **analítica** adecuada. En estos casos una práctica común y muchas veces la única a la mano, es la **SIMULACIÓN** del sistema de interés.

> [!info] 
> Los **MÉTODOS NUMÉRICOS** corresponden a un conjunto de herramientas o métodos usados para obtener una solución de problemas matemáticos de forma aproximada. Se aplican principalmente a problemas que no presentan una solución exacta, por lo tanto precisan ser resueltos numéricamente.

### Sistemas y Modelos
> [!info] Sistema
> La definición básica de **SISTEMA** nos dice que se trata de un conjunto de elementos que se interrelacionan para funcionar como un todo. Desde el punto de vista de la simulación, tales elementos deben tener una frontera clara.

- **ENTIDADES** ->  son los objetos de interés que constituyen el sistema (responsables de que el estado del sistema cambie)
- **ATRIBUTOS** -> son las propiedades que caracterizan a las entidades componentes del sistema
- **ESTADO DEL SISTEMA** -> es la caracterización de las entidades del sistema y sus atributos en un instante dado (condición que guarda el sistema en un instante de tiempo dado)
- **ACTIVIDADES** -> son procesos que provocan cambios en el sistema
	- ENDÓGENAS ->ocurren dentro del sistema. Las variables endógenas son aquellas determinadas dentro del modelo, es decir, son resultado de las interacciones y procesos internos del sistema que se está simulando.
	- EXÓGENAS -> ocurren en el medio ambiente y afectan al sistema. Las variables exógenas son aquellas externas al modelo cuyos valores son dados como parámetros de entrada al sistema. Influyen en el comportamiento del sistema, pero su valor no es determinado por las relaciones internas del modelo de simulación.
- **MEDIO AMBIENTE** -> es el exterior del sistema. Es importante establecer los límites entre el medio ambiente y el sistema.

> [!info] Modelo
> Un **MODELO** es una abstracción de la realidad.
> Un **MODELO** es una representación de la realidad que ayuda a entender cómo funciona.
> Un **MODELO** es una construcción intelectual y descriptiva de una entidad en la cual un observador tiene interés. Se construye para ser transmitido. Supuestos simples son usados para capturar el comportamiento importante.

### Tipos de Modelos

