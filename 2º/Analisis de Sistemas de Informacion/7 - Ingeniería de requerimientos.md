# Ingeniería en requerimientos

La ingeniería de requerimientos tiene como objetivo principal crear y mantener un documento que administre los requerimientos de un sistema. El proceso involucra cuatro etapas:

1. Estudio de viabilidad: Analiza si el sistema es útil y factible para el negocio. 
2. Obtención y análisis de requerimientos: Colaboración con usuarios y clientes para identificar los requerimientos, tanto funcionales como no funcionales. 
3. Especificación de requerimientos: Consiste en documentar detalladamente los requerimientos en formatos entendibles por todos los involucrados. 
4. Validación de requerimientos: Verificación de que los requerimientos reflejan lo solicitado por los clientes.

## Modelos de desarrollo

El modelo en espiral es una forma iterativa que permite refinar los requerimientos a medida que se desarrolla el sistema. Inicia con la comprensión del negocio y repite el ciclo de obtención, especificación y validación de requerimientos

![[imgs/16.png|center|380]]

## STAKEHOLDERS (Interesados)

Los stakeholders se dividen en: 
- **Directos**: Aquellos que interactúan con el sistema (ej. clientes). 
- **Indirectos**: Aquellos que influyen en el sistema sin interactuar directamente (ej. directivos). 
- **Del** **dominio**: Aquellos que definen restricciones propias del dominio del sistema (ej. normativas interbancarias).

## Validación de los requerimientos

Para asegurar la validez de los requerimientos, es necesario realizar una serie de verificaciones a través de un checklist que contemple las siguientes características:

- Validez: Los requerimientos deben responder a las necesidades del cliente, evitando funciones innecesarias o incorrectas. 
- Verificabilidad: Cada requisito debe poder ser demostrado. 
- Completitud: Todos los requerimientos especificados por el cliente deben estar incluidos. 
- Consistencia: No deben existir conflictos o contradicciones entre los requerimientos. 
- Realismo: Los requerimientos deben ser implementables con los recursos y la tecnología disponibles.

## Clasificación de los requerimientos

Se pueden clasificar en dos grandes categorías: 
- Duraderos: Propios del dominio del sistema y se mantienen estables. 
- Volátiles: Cambian debido a las circunstancias, como cambios en las leyes o políticas. Estos pueden ser: 
	- Cambiantes: Debido a factores externos como nuevas regulaciones. 
	- Emergentes: Que surgen al comprender mejor el sistema. 
	- Consecuentes: Resultados de la implementación del sistema. 
	- De compatibilidad: Relacionados con la interacción entre diferentes sistemas.

## Gestión de trazabilidad de los requerimientos

La gestión de requerimientos es un proceso iterativo, ya que los requerimientos evolucionan con el tiempo. La trazabilidad es clave para seguir los cambios en los requerimientos, desde su definición hasta su implementación. 

La trazabilidad horizontal se enfoca en las distintas versiones de un requerimiento, mientras que la vertical conecta un requerimiento con los artefactos del desarrollo del sistema

![[imgs/17.png|center]]

## Pre y Post - trazabilidad

**Pre-trazabilidad**: Esta fase cubre la definición de los requisitos por parte de los actores o interesados, quienes contribuyen a la especificación inicial de los requerimientos.

**Post-trazabilidad:** En esta fase, los requerimientos definidos inicialmente avanzan hacia la arquitectura del sistema y, eventualmente, hacia los casos de prueba. La arquitectura permite visualizar los diferentes componentes o artefactos del sistema desde diversas perspectivas. La trazabilidad asegura que los requisitos, desde su definición por los usuarios, se mantengan coherentes hasta la implementación de los casos de prueba que validan dichos requisitos.

![[imgs/18.png|center|500]]

## Herramientas case

Las herramientas CASE (Ingeniería de Software Asistida por Computadora)son fundamentales para gestionar los requerimientos, como el almacenamiento, la trazabilidad y la gestión del cambio. 

Un ejemplo es Enterprise Architect, que permite visualizar la relación entre requerimientos, usuarios y módulos del sistema a través de matrices de trazabilidad.

## Proceso de gestión de cambios 

El proceso de gestión de cambios incluye: 
- Identificación del problema que requiere un cambio en el sistema. 
- Análisis del cambio: Evaluación de costos, impacto y recursos necesarios. 
- Implementación del cambio: Actualización del documento de requerimientos y modificaciones en el diseño e implementación del sistema.



