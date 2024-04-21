# Captura de Requisitos
#### Enumerar los requisitos candidatos
Lista de estas ideas que consideramos como un conjunto de requisitos candidatos que podemos decidir implementar en una versión futura del sistema. La lista de características se utiliza solo para la planificación del trabajo.
Las características tienen un nombre corto y una breve explicación. Tiene un conjunto de valores:
- Estado (propuesto, aprobado, incluido o validado)
- Coste estimado de implementación (recursos y horas-personas)
- Prioridad
- Nivel de riesgo asociado a la implementación
#### Comprender el contexto del sistema
Se hace a través del **Modelado del Dominio** y **Modelado del Negocio**.
Un modelado del dominio describe los conceptos importantes del contexto como objetos del dominio, y enlaza estos objetos unos con otros.
Un modelo de negocio puede describirse como supraconjunto de un modelo de dominio. Su objetivo es describir los procesos (existentes u observados) con el fin de comprenderlos.
A medida que se desarrolla el modelo de negocio, los analistas aprenden mucho sobre el contexto del sistema software y lo describen en un modelo de negocio. Este especifica qué procesos de negocio soportará el sistema. Establece las competencias requeridas en cada proceso: sus trabajadores, responsabilidades y operaciones.
#### Captura de requisitos funcionales
Cada usuario quiere que el sistema haga algo para él. Un caso de uso para el usuario es un modo de utilizar el sistema. Los RF tienen que ser una respuesta funcional al usuario o a otro sistema. También, la especificación de los requisitos funcionales de un sistema debe ser completa y coherente. Completar significa que todos los servicios solicitados por el usuario y/u otro sistema están definidos. La coherencia significa que los requisitos no tienen una definición contradictoria. 
#### Captura de requisitos no funcionales
Especifican propiedades del sistema, como restricciones del entono o de la implementación, rendimiento, dependencias de la plataforma, facilidad de mantenimiento, extensibilidad, y fiabilidad. En otras palabras, no habla de "lo que" hace el sistema, sino de "cómo" lo hace.
### Actores
Es alguien o algo que interactúa con el sistema (persona, organización, programa o sistema de hardware o software). Un actor estimula al sistema con algún evento o recibe información del sistema. Un actor es **externo** al sistema y cumple un rol definido (cliente, banco, empleado).
### Modelo de Casos de Uso
¿Qué es un caso de uso? Es una técnica para especificar requisitos funcionales. Entonces, es un requisito funcional. Responden a la pregunta "¿Que se supone que el sistema debe hacer para los usuarios?". Son requisitos que generan valor al negocio.
Caracteristicas:
- Representa el comportamiento de un sistema desde la perspectiva del usuario para alcanzar los objetivos del negocio
- Describe lo que el software hace, y no la manera en que lo hace. Separa el "Qué" del "Cómo"
- Se componen de una representación grafica y una especificación funcional
- Deben escribirse desde la perspectiva del actor
- Describen la interacción del actor y del sistema
Se compone de:
- Diagrama -> importante las especificaciones
	- Actores
	- Funcionalidades (Casos de Uso)
	- Relaciones
- Especificación
	- Escenarios
	- Restricciones
### Modelo del Dominio
> [!tip]
 >Es una representación de las clases conceptuales del mundo real, no de componentes de software. No se trata de un conjunto de diagramas que describen clases software, u objetos software con responsabilidades.
 
Un modelo del dominio captura los tipos más importantes de objetos en el contexto del sistema. Los objetos representan "cosas" que existen o los eventos que suceden en el entorno en el que trabaja el sistema. Las clases del dominio aparecen en tres formas:
- Objetos del negocio que representan cosas que se manipulan en el negocio, como pedidos, cuentas y contratos.
- Objetos del mundo real y conceptos de los que el sistema debe hacer un seguimiento, como la aviación enemiga, misiles, etc.
- Sucesos que ocurrirán o han ocurrido, como la llegada de un avión, su salida y la hora de la comida.
El modelado del dominio se hace mediante diagramas UML. En estos, se muestran a los clientes, usuarios, revisores  y otros desarrolladores y cómo se relacionan.
![[Modelo del Dominio.png]]
> [!attention] Notación UML
> Clases, atributos y asociaciones. El texto al final de una lúnea de asociación explica el rol de la calse en relación con la otra (el rol de asociación). La multiplicidad indican cuántos objetos de la clase de ese extremo pueden enlazarse a un objeto en el otro extremo.
#### Clases Conceptuales
Es una idea, cosa u objeto. Podría considerarse en términos de:
- Símbolo: palabras o imágenes que representan una clase conceptual
- Intensión: la definción de una clase conceptual
- Extensión: el conjunto de ejemplos a los que se aplica la clase conceptual
No excluya una clase conceptual simplemente porque los requisitos no idican alguna necesidad obvia para registrar información sobre ella o porque la clase conceptual no tiene atributos.
### Modelo del Negocio
"Describe los procesos de negocio de una empresa en términos de casos de uso del negocio y actores del negocio que corresponden con los procesos del negocio y los clientes.
Un modelo de negocio se desarrolla en dos pasos:
1. Los modeladores del negocio deben confeccionar un modelo de casos de uso del negocio que identifique los actores del negocio y los casos de uso del negocio que utilicen los actores.
2. Los modeladores deben desarrollar a un modelo de objetos del negocio compuesto por trabajadores, entidades del negocio, y unidades de trabajo que juntos realizan los casos de uso del negocio."
Es todo aquello que el sistema no puede controlar, por ejemplo, al usuario con sus casos de uso. Se delimitan con linea punteada.
### Relaciones
Las usamos para ligar gráficamente dos casos de uso, cuyos flujos de eventos están unidos, normalmente en una sola sesión del usuario. 
Relaciones fundamentales:
- Uso
- Inclusión
- Extensión
- Generalización -> padre e hijo de una "clase" dependiendo sus atributos
#### Inclusión <\<include>>
Una relación de inclusión entre casos de uso especifica que un caso de uso base incorpora explicitamente el comportamiento de otro caso de uso en el lugar establecido en el caso de uso base.
Una relación de inclusión se representa como una dependencia que declara que un caso de uso utiliza información y servicios de otro.
Objetivo: compartir datos y se llama siempre!
#### Extensión <\<extend>>
Una relación de exclusión entre casos de uso especifica que un caso de uso base incorpora implicitamente el comportamiento de otro caso de uso en el lugar establecido en el caso de uso base que extiende.
La funcionalidad de un caso de uso incluye un conjunto de pasos que ocurren solo en algunas oportunidades, es decir, se tiene que cumplir una **condición**.
La excepción consiste en interrumpir el caso de uso A y pasar a ejecutar otro caso de uso B. (Autorizar pago con tarjeta).
Necesita una condición para que se cumpla