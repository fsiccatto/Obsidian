# UML

>[!important] Que es?
>El Lenguaje Unificado de Modelado (UML) es un lenguaje estándar utilizado para visualizar, especificar, construir y documentar sistemas de software. Es aplicable a diversos contextos, como sistemas de información empresariales, aplicaciones web distribuidas y sistemas empotrados de tiempo real.


Funcionalidades de UML: 
- **Visualización**: Cada símbolo en UML tiene una semántica clara que permite interpretar gráficamente los elementos y sus relaciones. 
- **Especificación**: Los modelos creados con UML son precisos y no ambiguos, lo que permite una clara interpretación. 
- **Construcción**: Facilita el desarrollo de sistemas de software y la creación de modelos completos y comprensibles. 
- **Documentación**: Genera artefactos entregables durante todo el proceso de desarrollo, proporcionando una base para futuras modificaciones o nuevas versiones.

## Ingeniería directa e inversa\

**Ingeniería Directa**: A partir de los modelos de UML, se puede derivar el código de programación. 
**Ingeniería Inversa:** A partir del código existente, se puede documentar y crear modelos UML, lo que facilita la comprensión de sistemas ya desarrollados.

## Elementos de UML

UML se compone de elementos básicos, reglas de construcción y mecanismos comunes. 

Elementos Básicos: 
1. **Estructurales:** Representan las partes estáticas del sistema, como: 
	- *Clases*: Conjunto de objetos que comparten atributos, operaciones y relaciones. 
	- *Casos de uso*: Representan una secuencia de acciones o funcionalidades del sistema. 
2. **De Comportamiento**: Representan las partes dinámicas del sistema, como: 
	- *Interacciones*: Conjunto de mensajes intercambiados entre objetos. 
	- *Máquinas de Estados*: Secuencia de estados que un objeto atraviesa durante su vida. 
	- *Actividades*: Pasos en el flujo de trabajo de un proceso. 
3. **De Agrupación**: Organizan los modelos en paquetes. Los paquetes agrupan elementos como clases y casos de uso.  
4. **De Anotación**: Sirven para hacer aclaraciones o comentarios dentro del modelo, como las notas. 

Relaciones en UML: 
- **Asociación:** Relación entre dos elementos, como entre un actor y un caso de uso, o entre clases. Puede tener multiplicidades. 
- **Agregación y Composición**: Relación de "todo-parte" entre objetos. 
- **Generalización:** Relación jerárquica donde un elemento especializado hereda características de uno general.

![[imgs/19.png|center]]

## Vista y modelado de UML

Para comprender un sistema complejo, se necesitan múltiples vistas del modelo. UML cubre las diferentes vistas necesarias en el ciclo de vida de desarrollo del software. Sin embargo, UML no especifica cuándo o qué modelos crear; esta tarea corresponde al proceso de desarrollo de software.

## Diagramas de UML

1. **Diagrama de clases**: Representa elementos como clases (estructurales) y relaciones (asociaciones y generalizaciones). Permite visualizar el sistema y cómo interactúan estos elementos. 
2. **Diagramas de objetos**: Similar al de clases, pero mostrando objetos específicos (indicados con ":" antes del nombre). 
3. **Diagramas de estados**: Muestran los estados de un objeto y las transiciones entre ellos basadas en eventos. 
4. **Diagramas de secuencia**: Ilustran la interacción entre objetos mediante el intercambio de mensajes en una secuencia temporal. 
5. **Diagramas de colaboración**: Muestran la organización estructural de los objetos que envían y reciben mensajes. 
6. **Diagramas de casos de uso:** Relacionan actores con los casos de uso (funcionalidades) que realizan.

## Reglas de UML

- **Nombres:** Deben seguir convenciones, por ejemplo, los nombres de clases en singular, los casos de uso en infinitivo. 
- **Alcance y visibilidad:** Define qué elementos pueden ver o interactuar con otros (por ejemplo, público, privado o protegido). 
- **Integridad:** Los diagramas deben ser consistentes entre sí, como los diferentes planos de una casa que deben ajustarse a la misma estructura. 
- **Ejecución:** Modelos dinámicos deben ser simulables, lo que permite previsualizar su funcionamiento real.

## Tipos de modelo

- **Abreviados**: Ocultan elementos para simplificar la vista (ej. mostrando solo el exterior de un coche).
- **Incompletos**: Faltan elementos, ya sea intencionadamente o por falta de información.
- **Inconsistentes**: No garantizan la integridad completa (ej. un prototipo de coche que no incluye todos los detalles).

## Mecanismos comunes

- **Especificaciones**: UML no es solo gráfico; cada notación tiene una sintaxis y semántica que debe seguirse. 
- **Adornos**: Símbolos adicionales como "+" (público), "-" (privado) o "#" (protegido) para definir visibilidad de atributos y operaciones. 
- **Divisiones comunes**: Separan elementos en: 
	- *Abstracción y concreción:* Como clase/objeto (Ej. Clase: Alumno, Objeto: Juan Martínez). 
	- *Interfaz e implementación*: Para operaciones y métodos (Ej. Interfaz: Diccionario ortográfico, Implementación: Asistente ortográfico). 
	- *Tipo/Rol*: Describe el significado de una entidad en un contexto particular. Las clases pueden asumir diferentes roles en distintas relaciones (Ej. Clase: Alumno y Cátedra; Rol 1: Alumno, Rol 2: Ayudante de 2da). 
- **Estereotipos y restricciones**: Permiten personalizar el vocabulario y reglas de UML, añadiendo estereotipos o restricciones específicas (ej. cómo ordenar elementos en una lista).

## Arquitectura del sistema

La arquitectura es fundamental para gestionar las múltiples perspectivas del sistema a lo largo de su ciclo de vida. No solo implica decisiones sobre la organización de los elementos estructurales, sino también sobre su comportamiento, las interacciones entre ellos y cómo se comunican a través de interfaces bien definidas. Estas decisiones deben tener en cuenta requisitos funcionales y no funcionales, como rendimiento, escalabilidad y seguridad, para asegurar que el sistema cumpla con sus objetivos de manera eficiente y sostenible.

![[imgs/20.png]]

