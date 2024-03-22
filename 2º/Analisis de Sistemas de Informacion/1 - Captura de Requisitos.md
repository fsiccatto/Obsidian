#### Enumerar los requisitos candidatos
Lista de estas ideas que consideramos como un conjunto de requisitos candidatos que podemos decidir implemnetar en una versión futura del sistema. La lista de características se utiliza solo para la planificación del trabajo.
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
Cada usuario quiere que el sistema haga algo para él. Un caso de uso para el usuario es un modo de utilizar el sistema.
#### Captura de requisitos no funcionales
Especifican propiedades del sistema, como restricciones del entono o de la implementación, rendimiento, dependencias de la plataforma, facilidad de mantenimiento, extensibilidad, y fiabilidad.
### Modelo del Dominio
Un modelo del dominio captura los tipos más importantes de objetos en el contexto del sistema. Los objetos representan "cosas" que existen o los eventos que suceden en el entorno en el que trabaja el sistema. Las clases del dominio aparecen en tres formas:
- Objetos del negocio que representan cosas que se manipulan en el negocio, como pedidos, cuentas y contratos.
- Objetos del mundo real y conceptos de los que el sistema debe hacer un seguimiento, como la aviación enemiga, misiles, etc.
- Sucesos que ocurrirán o han ocurrido, como la llegada de un avión, su salida y la hora de la comida.
El modelado del dominio se hace mediante diagramas UML. En estos, se muestran a los clientes, usuarios, revisores  y otros desarrolladores y cómo se relacionan.
![[imgs/Modelo del Dominio.png]]
### Modelo del Negocio
Describe los procesos de negocio de una empresa en términos de casos de uso del negocio y actores del negocio qeu corresponden con los procesos del negocio y los clientes.
Un modelo de negocio se desarrolla en dos pasos:
1. Los modeladores del negocio deben confeccionar un modelo de casos de uso del negocio que identifique los actores del negocio y los casos de uso del negocio que utilicen los actores.
2. Los modeladores deben desarrollar a un modelo de objetos del negocio compuesto por trabajadores, entidades del negocio, y unidades de trabajo que juntos realizan los casos de uso del negocio.
#### 