# Modelo de dominio
El modelo de dominio es una representación visual de las clases conceptuales y los objetos del mundo real con un dominio de interés. **Los modelos de dominio no representan componentes de un software**

## Clases conceptuales
Una clase conceptual definida formalmente es un símbolo, extensión e intención, si lo queremos entender de una mejor manera y mas informal este es una idea, objeto u cosa Existen muchísimos tipos de clases conceptuales:

| Categoria de la clase conceptual         | Ejemplos                                   |
| ---------------------------------------- | ------------------------------------------ |
| Objetos tangibles                        | Avion                                      |
| Especificacion, disenios o descripciones | Descripcion del vuelo                      |
| Lugares                                  | Tienda                                     |
| Transacciones                            | Venta, Pago, reserva                       |
| Linea de transaccion                     | Linea en venta                             |
| Roles de la gente                        | Piloto                                     |
| Contenedores                             | Lata                                       |
| Cosas en un contenedor                   | Pasajero                                   |
| Sistemas informaticos                    | Sistemas de autorizaion de pago de credito |
| Conceptos abstractos                     | Ansia                                      |
| Organizaciones                           | Compania                                   |
| Hechos                                   | Reunión, Colisión, Aterrizaje              |
El error mas típico al identificar una clase conceptual es cuando representamos una clase como un atributo cuando la deberíamos haber representado como un concepto

# Modelo de negocio
Un modelado de negocio cumple estos pasos

- Listas de clases candidatas 
- Representamos en un modelo de dominio 
- Añadimos las asociaciones necesarias para registrar relaciones que hay que mantener en la memoria 
- Añada los atributos necesarios para satisfacer los requisitos de información

## UML (Lenguaje de Montado Unificado)
Es un tipo de notación que describe los diagramas de clase y los diagramas de secuencia. Que no superpone un método o perspectiva en el modelado de ellos Esta misma notación puede utilizarse en 3 tipos de modelos:

- Perspectiva conceptual
- Perspectiva de especificación
- Perspectiva de implementación

Esta ultima permite que los diagramas tengan tecnología e implementaciones de software en ellas

## Modelos
Con UML se construyen modelos. Un modelo es:

- Una abstracción de un sistema 
- Una representación grafica y completa de la realidad, creado para comprender mejor el sistema

En el contexto del software existen distintas vistas que sirven para: visualizar, especificar , construir y documentar un SW desde distintas perspectivas y modelar cosas estáticas (*modelado estructural*) o modelar cosas dinámicas *(modelado de comportamiento*). Estas vistas contienen distintos diagramas de elementos, que se dibuja como un grafo con nodos

### Diagramas estructurales

- Diagrama de Clases: clases, interfaces y colaboraciones 
- Diagrama de Objetos: Objetos 
- Diagrama de Componentes: Componentes 
- Diagrama de Despliegue: Nodos 
- Diagrama de Casos de Uso: Organiza los comportamientos del sistema

#### Diagrama de paquetes
Los paquetes agrupan clases en base a algún criterio de organización . Cada paquete tiene un nombre que lo distingue, estos también se pueden anidar. Existen 2 tipos de notación:

- Visualizar el contenido 
- Sin saber que se contiene 

Estas notaciones semánticamente son iguales pero se diferencian a la viste en el UML. Este permite administrar la complejidad del sistema y subdividirlo en porciones para hacerlo mas manejable 

**Características**
- Un Elemento pertenece al paquete donde esta definido 
- Un elemento puede ser referenciado por otros paquetes

### Diagramo de comportamiento dinámico

- Diagrama de Secuencia: Centrados en la ordenación temporal de mensajes 
- Diagrama de Colaboración: Centrados en la organización estructural de los objetos que envían y reciben mensajes 
- Diagrama de Estados: Centrado en el estado cambiante de un objeto 
- Diagrama de Actividades: Centrado en el flujo de control de actividades

# Conceptos y principios orientados a objetos
Estos objetos existen en la naturaleza, en entidades hechas por el hombre, en los negocios y en los productos que usamos. Ellos pueden ser clasificados, descritos, organizados, combinados, manipulados y creados. Antes de seguir con los conceptos debemos entender que es la visión orientada a objetos

#### Que es la visión orientada a objetos 
El punto de vista orientado a objetos en el análisis de sistemas es una metodología que se enfoca en modelar un sistema en términos de objetos. Estos objetos representan entidades del mundo real o conceptos abstractos que interactúan entre sí para formar el sistema completo.

## Clases y Objetos
Una clase es un concepto OO que encapsula las abstracciones de datos y procedimiento que se requieren para describir el contenido y comportamiento de alguna entidad del mundo real. Visto de otra manera, una clase es una descripción generalizada que describe una colección de objetos similares. Por definición, todos los objetos que existen dentro de una clase heredan sus atributos y las operaciones disponibles para la manipulación de los atributos.

Existen superclases que son colecciones de clases. Además existen las subclases que son instancias de las clases

### Atributos
Es una descripción con palabras que indican características estables, donde una característica puede verse como una relación binaria entre una clase y cierto dominio

### Operaciones, métodos y servicios
Un objeto encapsula datos y los algoritmos que procesan estos datos. Estos algoritmos son llamados *operaciones, métodos o servicios*. Cada una de las operaciones encapsuladas por un objeto proporciona una representación de uno de los comportamientos del objeto.

### Mensajes
==Los mensajes son el medio a través del cual los objetos interactúan. Usando la terminología introducida en la sección precedente, un mensaje estimula la ocurrencia de cierto comportamiento en el objeto receptor==. El destino define el objeto receptor el cual es estimulado por el mensaje, operación se requiere al método que recibe el mensaje, operación, se refiere al método que recibe el mensaje y parámetros proporciona información requerida para el éxito de la operación

### Encapsulamiento, herencia y polimorfismo
Como ya hemos observado, las clases OO y los objetos derivados de ellas encapsulan los datos y las operaciones que trabajan sobre estos en un único paquete. La ==herencia== es una de las diferencias clave entre sistemas convencionales y sistemas OO. Una subclase Y hereda todos los atributos y operaciones asociadas con su superclase X. Esto significa que todas las estructuras de datos y algoritmos originalmente diseñados e implementados para X están inmediatamente disponibles para Y El ==polimorfismo== es una característica que reduce en gran medida el esfuerzo necesario para extender un sistema OO. Este permite que un numero de operaciones diferentes tengan el mismo nombre. Esto reduce el acoplamiento entre objetos, haciendo a cada uno mas independiente

# Vista estática
Los elementos de la vista estática de un modelo son los conceptos significativos en una aplicación, incluyendo conceptos del mundo real, conceptos abstractos, conceptos de implementación, conceptos de computación y todo tipo de conceptos controlados por el sistema

## Clasificadores
Un clasificador es un concepto discreto en el modelo, que tiene identidad, estado, comportamiento, y relaciones. Las clases de clasificadores incluyen la clase, la interfaz, y los tipos de datos. Otras clases de clasificadores son materializaciones de conceptos de comportamiento, de cosas del entorno, o de estructuras de implementación.

*Interfaz:* Una interfaz es la descripción del comportamiento de objetos sin dar su implementación o estado, una interfaz contiene operaciones pero no atributos, y no tiene asociaciones salientes que muestran la visibilidad desde la propia interfaz 
*Tipo de dato:* Un tipo de dato es la descripción de los valores primitivos que carecen de identidad. Los tipos de datos incluyen números, cadenas, y valores enumerados. 
*Niveles de significado*: Las clases pueden existir en varios niveles de significación en un modelo, incluyendo los niveles de análisis, diseño, e implementación.

## Relaciones
Las relaciones entre clasificadores son asociación, generalización, flujo y varias de dependencia, que incluyen la realización y el uso.

## Generalización
La relación de generalización es una relación taxonómica entre una descripción mas general y una descripción mas especifica, que se construye sobre ella y la extiende.

*Propósito de la generalización:* La generalización tiene 2 propósitos. El primero **debe definir las condiciones bajo las cuales una instancia de una clase puede ser utilizado cuando se declara una variable, conteniendo valores de una clase dada**. El otro propósito de la generalización es **permitir la descripción incremental de un elemento que comparte las descripciones de sus antecesores**

## Herencia múltiple
La herencia múltiple dice que si una clase tiene mas de un padre significa que tendrá como propiedades la unión de estas

## Clasificación dinámica
Un objeto puede cambiar su clase directa dinámicamente. Haciendo eso, puede perder o ganar atributos o asociaciones

# Diagrama de colaboración
Un diagrama de Colaboración es un tipo de diagrama de interacción cuyo objetivo es describir el comportamiento dinámico del sistema de información mostrando como interactúan los objetos entre si.

#### Propósitos
- Manejar la comunicación entre los elementos de un sistema 
- Mostrar como será implementada una operación 
- Indicar como deben colaborar los objetos del sistema para llevar a cabo una operación

#### Características
- Muestra como las instancias especificas de las clases trabajan juntas para conseguir un objetivo común 
- Implementa las asociaciones del diagrama de clases mediante el paso de mensajes de un objeto a otro. Dicha implementación es llamada "enlace"

#### Ventajas
1. Permite elegir el orden en que pueden hacerse las cosas 
2. Puede describir proceso o casos de uso 
3. Muestra los aspectos dinámicos de un sistema 
4. Establece las reglas de secuencia a seguir 
5. Ayuda un programador a desarrollar código a través de una descripción lógica de un proceso

![[EX - Diagramad de colaboracion|700]]
# El análisis
El lenguaje que utilizamos en el análisis se basa en un modelo de objetos conceptual que llamamos *modelo de análisis* El modelo de análisis nos ayuda a refinar los requisitos según las líneas que ya hemos mencionado antes y nos permite razonar aspectos internos del sistema, incluidos sus recursos compartidos internos

##### Porque el análisis no es diseño ni implementación
Antes de comenzar a diseñar e implementar deberíamos contar con una comprensión precisa y detallada de los requisitos

## El objeto del análisis

- Un modelo de análisis ofrece una especificación mas precisa de los requisitos que la que tenemos como resultado de la captura de requisitos, incluyendo el modelo de casos de uso 
- Un modelo de análisis describe utilizando el lenguaje de los desarrolladores, y puede por tanto introducir un mayor formalismo y ser utilizado para razonar sobre los funcionamientos internos del sistema
- Un modelo de análisis estructura los requisitos de un modo que facilita su comprensión, su preparación, su modificación, y en general, su mantenimiento 
- Un modelo de análisis puede considerarse como una primera aproximación al modelo de diseño y es por tanto una entrada fundamental cuando se da forma al sistema en el diseño y la implementación

### Clases de análisis
Una clase de análisis representa una abstracción de una o varias clases y/o subsistemas del diseño del sistema. Esta abstracción posee las siguientes características:

- Centra el tratamiento de requisitos funcionales posponiendo los no funcionales 
- El comportamiento es definido mediante una descripción textual de un conjunto cohesivo del comportamiento de una clase 
- Participa en relaciones Encaja en uno de 3 estereotipos: de **interfaz**, de **control** o de **entidad**

#### Clase de interfaz
Es utilizada para modelar las interacciones entre el sistema y sus actores. Esta interacción a menudo implica recibir información y peticiones de los usuarios y los sistemas externos. Las clases de interfaz modelan las partes del sistema que dependen de sus actores, lo cual implica que clasifican y reúnen los requisitos en los limites del sistema
![[imgs/1.png]]


#### Clase entidad
Se utilizan para modelar información que posee una vida larga y que es a menudo persistente. Las clases de entidad modelan la información y el comportamiento asociado a algún fenómeno o concepto

![[imgs/2.png|200]]

#### Clase control
Representan coordinación, secuencia, transacciones y control de otros objetos y se usan con frecuencia para encapsular el control de un caso en concreto. También son utilizadas para representar derivaciones y cálculos complejos
![[imgs/3.png|270]]

### Diagrama de clases
Estos son empleados para visualizar el aspecto estático de los distintos tipos de componentes o bloques de construcción de software y sus relaciones. Además sirven para poder especificar los detalles de un software y después construirlo. Gráficamente es un grafo donde todos los nodos son las clases y los arcos son las asociaciones y generalizaciones entre las clases

#### Clase
Esta representada como un rectángulo que tiene 3 partes esenciales

- Nombre (parte superior) 
- Atributos (parte del medio)
- Operaciones (parte inferior) Podemos representar de distintas maneras las clases 
- Representación de requisitos 
- Representación de Análisis 
- Representación de Diseño

#### Relaciones entre clases
En el dominio de las clases casi nunca vamos a tener clases aisladas: Nosotros trabajaremos con 2 tipos de relaciones:

- **Generalización:**  La generalización denota una relación de herencia si apunta hacia arriba significa es y si apunta hacia abajo significa puede ser
- **Asociación:** Es una relación estructural entre objetos de distintas clases del tipo "necesito-conocer" . Esto funciona para poder especificar de manera precisa el comportamiento y la estructura de una de ellas. Esto funciona para cuando un objeto de una clase A se relaciona en algo con los objetos de la clase B. Solo puede existir una instancia de asociación entre cualquier par de objetos participantes. Entre medio de esta instancia puede existir una clase que sea de asociación y que se encuentre entre medio de estas Existen asociaciones n-arias. Las unarias son las que se asocian a si mismas, las binarias con una clase mas y las n-arias con mas de una clase

##### Tipos de multiplicidad

- 0...1 : Sin instancia o solo una
- 1: Una y siempre una instancia 
- 0...* : Cero o múltiples instancias 
- 1...* : Múltiples instancias pero al menos una

Existe un caso especial de asociación que se emplea para expresar una relación estructural del tipo "todo/parte"(esta formado por) entre un agregado (el todo) y las partes que lo componen llamado Agregación. Esta sucede cuando queremos que la asociación tenga una unidireccionalidad. También existe una forma "fuerte" de agregación

- Una parte pertenece a un único agregado (exclusividad) 
- Si se elimina un agregado se eliminan todas sus partes (dependientes)

### Diagrama de Estado
Un diagrama de estado modela el comportamiento dinámico de los **objetos** como una maquina de estados

- Muestra el ciclo de vida de un objeto en particular 
- Los estados por los que pasa un objeto y como transita de uno a otro 
- Muestra los estados y las transiciones entre los estados dependiendo de los eventos que se producen

![[imgs/4.png|400]]

### Diagrama de interacción
En estos mostramos las interacciones entre los objetos creando enlaces entre ellos y añadiendo mensajes a esos enlaces. El nombre de un mensaje debería denotar el propósito del objeto invocante en la interacción con el objeto invocado.

![[imgs/5.png|400]]

#### Flujo de sucesos-análisis
Texto adicional que explica el diagrama de colaboración, el texto no debería mencionar ninguno de los atributos , responsabilidades y asociaciones del objeto, debido a que cambian con bastante frecuencia y seria difícil mantenerlo.

#### Requisitos especiales
Estos son descripciones textuales que recogen todos los requisitos no funcionales sobre una realización de casos de uso 

#### Paquete de análisis
Los paquetes de análisis proporcionan un medio para organizar los artefactos del modelo de análisis en piezas manejables. Un paquete de análisis puede constar de clases de análisis, de realizaciones de casos de uso y de otros paquetes del análisis

#### Paquete de servicios
Los paquetes de servicio son un conjunto estructurado de funcionalidades y características que un sistema o aplicación proporciona a los usuarios y otras partes interesadas.

#### Mas trabajadores

##### Ingeniero de casos de uso
Este es responsable de la integridad de una o mas realizaciones de casos de uso, garantizando que cumplan los requisitos que recaen sobre ellos

##### Ingeniero de componentes
Define y mantiene las responsabilidad, atributos, relaciones y requisitos especiales de una o varias clases del análisis, asegurándose de que cada clase del análisis cumple con los requisitos que se esperan de ella de acuerdo a las realizaciones de casos de uso en las que participa

# Arquitectura de software
Es el conjunto de decisiones significativas sobre la organización del sistemas de software, la selección de los elementos estructurales y sus interfaces con los que se compone un sistema , junto con su comportamiento tal como se especifica en las colaboraciones entre esos elementos 

Lo principal de la arquitectura de software son las grandes ideas en las influencias, organización, estilos, patrones, responsabilidades, colaboraciones, conexiones y motivación de un sistema 

La investigación arquitectural: Implica la identificación de aquellos requisitos funcionales y no-funcionales que influyen de manera significativa en el diseño del sistema 

El diseño arquitectural: Es la resolución de estas influencias y requisitos con el diseño de software, el hardware y las redes.

## Patrones de arquitectura y sus categorías
Los patrones de arquitectura son practicas bien conocidas en el diseño arquitectural, especialmente en cuanto a la arquitectura lógica a gran escala 

**Patrones de arquitectura**: Relacionados con el diseño a gran escala y de grano grueso y que se aplican típicamente durante las primeras iteraciones 
**Patrones de diseño**: Relacionados con el diseño de los objetos y frameworks de pequeña y mediana escala. Aplicables al diseño de una solución para conectar los elementos de gran escala que se definen mediante los patrones de arquitectura. 
**Estilos** Soluciones de diseño de bajo nivel orientados a la implementación o lenguaje

### Patrón de arquitectura: Capas
Una capa es un elemento de gran escala, a menudo compuesto de varios paquetes o subsistemas Este patrón organiza la estructura lógica de gran escala de un sistema de capas separadas de responsabilidades distintas y relacionadas, con una separación clara y cohesiva de intereses como que las capas "mas bajas" son servicios generales de bajo nivel

# Colaboración
Una colaboración es una descripción de una colección de objetos que interactúan para implementar un cierto comportamiento dentro de un contexto. Describe una sociedad de objetos cooperantes unidos para realizar un cierto propósito . Esta contiene ranuras que son rellenadas por los objetos y enlaces en tiempo de ejecución

## Interacción
Una interacción es un conjunto de mensajes dentro de una colaboración que son intercambiadas por roles de clasificadores a través de roles de asociación. Cuando una colaboración existe en tiempo de ejecución, los objetos ligados a roles de clasificador intercambian instancias con mensajes a través de los enlaces ligados a los roles de asociación

## Diagrama de secuencia
Un diagrama de secuencia representa una interacción como un grafico bidimensional. La dimensión vertical es el eje de tiempo, que avanza hacia abajo de la pagina

## Activación
Una activación es la ejecución de un procedimiento, incluyendo el tiempo que espera a los procedimientos anidados para ejecutarse. Se representa por una lineal doble que sustituye la parte de la line de vida en un diagrama de secuencia.


