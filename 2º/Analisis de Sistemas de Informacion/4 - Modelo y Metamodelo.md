>[!Important] Definicion de Modelo
>Un modelo es una representación simplificada o abstracta de una realidad, diseñada para capturar y organizar información clave de un sistema o proyecto. Los modelos se usan en muchos contextos, como la construcción o el desarrollo de software, y permiten anticipar y gestionar aspectos clave antes de la implementación real.

**Ejemplo de un modelo simple**: Al diseñar una cucha para un perro, con herramientas caseras y un esquema básico en papel, creamos un modelo mínimo. 
**Modelos complejos**: Al construir una casa o un edificio, el modelo incluye planos, maquetas y diferentes perspectivas, como la estructura, electricidad o gas. A mayor complejidad, más planificación y herramientas especializadas se requieren, incluyendo gerenciamiento y normas claras.

Los modelos permiten: 
1. Capturar requisitos del sistema. 
2. Abstraer la realidad en múltiples vistas o planos. 
3. Facilitar el diseño y evaluación de alternativas.

>[!Important] Definicion de Metamodelo
>Un metamodelo es el conjunto de reglas y notaciones que guían la creación de modelos. En desarrollo de software, por ejemplo, se utilizan lenguajes como UML (Lenguaje de Modelado Unificado), que proporciona una estructura estándar para representar un sistema.

## Modelo

- **Semántica y notación:** Los modelos tienen reglas y significados específicos que deben ser comprendidos por todos los involucrados. Un plano de construcción sigue normas para que cualquier profesional (arquitecto, ingeniero) lo interprete correctamente. 

- **Medio**: Un modelo puede representarse en diferentes medios. Por ejemplo, en la construcción, un plano en papel es un medio diferente a una maqueta o una casa piloto. Del mismo modo, en software, un diagrama UML es una representación abstracta de un sistema

Un **modelo de software** es una representación del sistema en un lenguaje de modelado (como UML), que facilita la comprensión y colaboración dentro del equipo de desarrollo

Los modelos sirven para: 
1. Capturar requisitos y conocimiento del dominio. 
2. Explorar y pensar en varias soluciones de diseño. 
3. Documentar decisiones de diseño. 
4. Generar productos útiles
5. Organizar, filtrar y corregir información en sistemas grandes. 
6. Manejar la complejidad.

### Niveles de modelos

1. Guías del proceso de pensamiento: Ofrecen una visión abstracta y conceptual del sistema. 
2. Especificaciones abstractas: Definen la esencia del sistema, sin incluir todos los detalles. 
3. Especificaciones completas: Describen todos los detalles del sistema, como si fuera la versión final.
4. Ejemplos de sistemas típicos o posibles: Muestran ejemplos prácticos o teóricos de sistemas reales o potenciales. 
5. Descripciones completas o parciales: Ofrecen una visión total o parcial de un sistema, con diferente grado de detalle.

### Semántica y notación de modelos

Los modelos en ingeniería de software tienen dos aspectos importantes: 

- Semántica: El significado que representa un modelo. Este significado es compartido por todos los miembros de un equipo. 
- Notación: La representación visual (como gráficos, flechas, actores, etc.) que sigue reglas uniformes y debe ser utilizada consistentemente

![[imgs/9.png|center|200]]


Un modelo siempre se utiliza dentro de un contexto específico, lo que le otorga un significado completo. 
Un diagrama de clases puede **interpretarse de diferentes** maneras dependiendo de su contexto: 
- En la fase de captura de requisitos, puede representar un **modelo de dominio**. 
- Durante el análisis del sistema, será un **modelo de clases**. 
- En la etapa de diseño, se transforma en un **modelo de diseño**


## Metamodelo

Un **metamodelo** es un modelo que especifica los conceptos de un lenguaje, sus relaciones y las reglas estructurales. UML es un ejemplo de un metamodelo que proporciona los elementos necesarios para construir diagramas. Este metamodelo está definido por un estándar (MOF - Meta Object Facility), que se organiza en cuatro niveles jerárquicos:

1. Nivel de Sistema: La aplicación real. 
2. Modelo de Sistema: Representa el sistema en UML. 
3. Meta Modelo: Define los conceptos de UML. 
4. Meta-Metamodelo: Define los metamodelos.

>[!Example] Ejemplo
>Notacion Musical (Metamodelo) ------> Partitura (Modelo)

![[imgs/10.png|center|250]]

El **proceso de captura de requisitos** se organiza mediante un **workflow** donde participan diferentes roles: 
- Analista de sistemas, arquitecto, especificador de casos de uso y diseñador de interfaces. 
- Las tareas incluyen identificar actores y casos de uso, priorizar y detallar los casos, estructurar el modelo de casos de uso, y crear prototipos de interfaz de usuario.

![[imgs/11.png|center|450]]


En la **etapa de análisis**, se realiza un análisis de arquitectura y de casos de uso, que luego son desglosados en clases y paquetes. Este análisis mantiene la trazabilidad con los requisitos definidos en la fase previa para asegurar que el sistema cumpla con lo requerido.

![[imgs/12.png|center|450]]

Los modelos deben ser evaluados para garantizar que los requisitos se cumplan mediante varios criterios: 
- **Validez**: Los requisitos responden a las necesidades del cliente.
- **Verificabilidad**: Se pueden verificar todos los requisitos. 
- **Completitud**: Todos los requisitos están cubiertos. 
- **Consistencia**: No hay contradicciones entre los requisitos. 
- **Realismo**: Los requisitos son posibles de implementar con los recursos y tecnología disponibles



