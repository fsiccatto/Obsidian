# Simulación basada en Agentes Contenidos
## Introducción
El **MBA** es una técnica de simulación en la que el sistema se representa como un conjunto de **agentes autónomos** que siguen reglas simples de comportamiento e interacción.
El MBA **se centra en la emergencia de patrones globales a partir de las interacciones locales de los agentes**.
Esta metodología permite estudiar fenómenos emergentes, patrones colectivos y dinámicas de sistemas que serían difíciles de analizar con enfoques tradicionales.

> [!info] MBA
> La simulación basada en agentes consiste en un conjunto de agentes autónomos que perciben su entorno, toman decisiones y realizan acciones que afectan tanto a ellos mismos como a otros agentes y al medio ambiente.

##### Caracterísitcas de la simulación basada en agentes
- **Autonomía**. Los agentes son entidades independientes que toman decisiones y ejecutan acciones sin intervención externa directa.
- **Interacción**. Los agentes pueden comunicarse y cooperar, competir o influenciarse mutuamente.
- **Adaptabilidad**. Los agentes pueden aprender y cambiar su comportamiento en respuesta a las condiciones cambiantes del entorno.
- **Heterogeneidad**. Los agentes pueden tener diferentes características, comportamientos y objetivos. 
- **Descentralización**. No hay una autoridad central que controle el sistema; el comportamiento global emerge de las interacciones locales entre los agentes.
##### Atributos de la simulación basada en agentes
- **Emergencia**. Comportamientos y patrones globales emergen a partir de las interacciones locales entre agentes. 
- **Escalabilidad**. La simulación basada en agentes puede manejar un gran número de agentes y es adecuada para estudiar sistemas de gran escala. 
- **Flexibilidad**. Permite modelar una amplia variedad de sistemas y escenarios, desde sociales y económicos hasta biológicos y ecológicos.
- **Experimentación**. Facilita la experimentación y el análisis de escenarios hipotéticos, ayudando a explorar los efectos de diferentes políticas y estrategias.

## Palabras claves de la simulación MBA

> [!todo] Definición
> Los modelos basados en agentes (ABM) son modelos de simulación computacional que involucran a muchos agentes discretos.
> - Computacional -> las reglas de comportamiento de cada agente se describen de una manera algorítmica en lugar de una manera puramente matemática.
> - muchos -> el contexto típico en el que se necesita una ABM es cuando los investigadores quieren estudiar el comportamiento colectivo de un gran número de agentes.
> - discreto -> un agente debe ser una entidad individual discreta, que tiene un claro límite entre el yo y el exterior.

Algunas propiedades típicas de agentes y modelos basados en agentes:
- Los agentes son entidades discretas. 
- Los agentes pueden tener estados internos.
- Los agentes pueden estar localizados espacialmente. 
- Los agentes pueden percibir e interactuar con el entorno. 
- Los agentes pueden comportarse en base a reglas predefinidas.
- Los agentes pueden ser capaces de aprender y adaptarse. 
- Los agentes pueden interactuar con otros agentes. 
- Los ABM a menudo carecen de supervisores/controladores centrales. 
- Las ABM pueden producir un “comportamiento colectivo” no trivial en su conjunto.
## Metodología bada en Agentes
Son tipos de sistemas donde l**os patrones están determinados no por una autoridad central, sino por interacciones locales entre componentes descentralizados**. 
> [!info]
> El MBA está enmarcado en la ciencia de la complejidad, donde lo que se trata de estudiar **son grandes conjuntos de componentes interactúan localmente entre si y se forman espontáneamente nuevas estructuras globales y comportamientos no triviales en escalas superiores. No hay líderes que dirijan estos comportamientos colectivos, sino que a través de todas estas interacciones surge nueva información**.

El MBA es un **sistema dinámico**, usa un enfoque bottom up, es decir que se define el sistema a partir de los agentes y sus relaciones con el entorno.

El MBA requiere una serie de pasos estructurados para diseñar y simular el comportamiento de agentes dentro de un sistema complejo. Se propone una metodología general:
1. Definir el problema y objetivo
	- Identificar el fenómeno o sistema a modelar (tráfico, redes sociales, mercados, etc.). 
	- Determinar los objetivos de la simulación (¿Qué se quiere analizar o predecir?). 
	- Establecer las métricas clave de evaluación.
2. Identificar agentes y entorno
	- Determinar quiénes o qué serán los agentes (individuos, empresas, vehículos, etc.). 
	- Definir el entorno en el que operan los agentes (espacial, digital, red de interacciones, etc.). 
	- Especificar las restricciones y condiciones del sistema.
3. Definir las Propiedades y Comportamientos de los Agentes 
	- Asignar atributos a los agentes (estado inicial, capacidades, reglas de decisión). 
	- Establecer comportamientos y reglas de interacción (¿Cómo toman decisiones? ¿Cómo influyen entre sí?).
	- Considerar el uso de modelos de decisión como reglas heurísticas, aprendizaje, etc.
4. Definir las Interacciones y Redes de Comunicación 
	 - Especificar cómo los agentes se comunican o afectan entre sí (interacciones locales, globales, redes sociales, etc.). 
	- Determinar el tipo de conexión entre agentes (estructuras de red: libre, aleatoria, escala libre, etc.). 
	- Evaluar la influencia del entorno en las interacciones. 
5. Implementar el Modelo en una Plataforma de Simulación
	 - Seleccionar una herramienta adecuada (AnyLogic, NetLogo, Mesa (Python), Repast, GAMA, etc.). 
	 - Codificar los agentes, su entorno y sus interacciones. 
	 - Incorporar parámetros configurables para pruebas y ajustes. 6
6. Ejecutar la Simulación y Analizar Resultados
	- Correr simulaciones bajo diferentes escenarios. 
	- Analizar los datos generados por la simulación (gráficos, métricas de desempeño, patrones emergentes).
	- Identificar tendencias, comportamiento global emergente y posibles optimizaciones.
7. Validar y Refinar el Modelo
	- Comparar los resultados con datos reales o modelos previos. 
	- Ajustar parámetros y reglas para mejorar la precisión del modelo. 
	- Repetir simulaciones hasta obtener un modelo representativo y confiable. 
8. Documentar y Presentar los Resultados 
	- Elaborar un informe con la metodología, implementación y hallazgos. 
	- Interpretar los resultados en función de los objetivos iniciales. 
	- Sugerir mejoras o aplicaciones prácticas del modelo en escenarios reales.
## Metodologías basadas en dinámica de sistemas y en agentes. Características. Diferencias
La Dinámica de Sistemas es un enfoque de variable continua que representa el comportamiento de un sistema mediante **ecuaciones diferenciales y flujos de retroalimentación**.
Por otro lado, el Modelado Basado en Agentes adopta un enfoque descentralizado, en el que el sistema se compone de **múltiples agentes individuales que toman decisiones de manera autónoma e interactúan con su entorno**.

##### Enfoque de modelado

| ***Dinámica de Sistemas***                                                                                                          | ***Agentes***                                                                                                                            |
| ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Enfoque Agregado.** Se modela la población como una *variable de nivel*, representando el número total de personas.               | **Enfoque Individual.** Cada persona es un *agente* con características únicas (edad, esperanza de vida, etc.).                          |
| **Ecuaciones Diferenciales.** Los nacimientos y muertes se modelan como *flujos* (tasas de cambio de la población).                 | **Interacciones locales.** Se *modelan eventos individuale*s (nacimientos y muertes) y cada agente puede actuar de manera independiente. |
| **No hay agentes individuales.** Se usa una estructura de ecuaciones en la que la población cambia de manera continua.              | **Comportamiento emergente.** La población total es una consecuencia del comportamiento de cada agente.                                  |
| **Ejemplo.** Se define la ecuación: <br><br>$dPobl/ dt = Nacimientos – Muertes$<br> <br>Nacimientos y Muertes dependen de población | **Ejemplo.** Cada persona tiene una edad y puede morir o reproducirse de forma independiente.                                            |
##### Características en la implementación en software

| **Características** | **Dinámica de Sistemas** <br> *Vensim (Dinámica de Sistemas)* | **Agentes** <br> *AnyLogic (Agentes)* |
|----------------------|---------------------------------------------------------------|---------------------------------------|
| **Unidad de Modelado** | Variables agregadas (niveles y flujos) | Individuos (agentes) |
| **Dinámica del Modelo** | Ecuaciones diferenciales continuas | Eventos discretos por agente |
| **Interacción entre Entidades** | Se modelan interacciones como tasas | Cada agente interactúa con otros |
| **Precisión en el Comportamiento Individual** | Baja: se usa un promedio poblacional | Alta: cada agente puede tener reglas específicas |
| **Escalabilidad** | Más eficiente para grandes poblaciones | Puede volverse computacionalmente costoso |
| **Uso Típico** | Crecimiento poblacional, economía, recursos naturales | Sistemas con individuos autónomos (epidemias, mercados, movilidad) |
### Metodología Anylogic
El modelado de **eventos discretos** y la **dinámica del sistema** adoptan una perspectiva de **arriba hacia abajo** a nivel de sistema, El enfoque **basado en agentes** emplea un método de abajo hacia arriba en el que el modelador se centra en el comportamiento de los objetos individuales.

VER USO!