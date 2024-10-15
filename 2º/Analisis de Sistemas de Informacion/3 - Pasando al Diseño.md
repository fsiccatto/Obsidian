# Diagrama de clases del diseño

>[!Note] 
>El Diagrama de Clases del Diseño se construye a partir de los requisitos del sistema y proporciona una visión detallada de la estructura del software. Este diagrama es crucial para la transición del análisis al diseño de sistemas, asegurando que el sistema sea mantenible y funcional.

Utiliza los requisitos del análisis como base para modelar el sistema completo, incluyendo su arquitectura. Y su objetivo es crear una representación detallada y mantenible del sistema, no solo describir requisitos.
![[imgs/6.png]]

## Componentes claves del diagrama de clases del diseño

- Clases: Definición detallada de las entidades del software. 
- Asociaciones: Relaciones entre clases. 
- Atributos: Propiedades de cada clase. 
- Interfaces: Operaciones y constantes. 
- Métodos: Funciones que las clases pueden realizar. 
- Navegabilidad: Cómo se accede a las clases y sus relaciones. 
- Dependencias: Relaciones entre clases que indican el uso y la influencia mutua.


## Comparación entre el modelo conceptual y los diagramas de clases del análisis

**Modelo Conceptual**: Abstracción de conceptos del mundo real (e.g., una “Venta” representa un concepto). 

**Modelo de Diseño**: Representación detallada de clases de software basadas en conceptos del análisis, donde una “Venta” se convierte en una clase de software.

![[imgs/7.png|center]]
1. A partir del *Modelo Conceptual*: Se empieza con el Diagrama de Clases del Análisis, que incluye: 
	1. Clases 
	2. Relaciones estructurales 
2. Adiciones y Detalles en el *Diseño*: 
	1. Métodos: Especificar las funciones que las clases realizarán. 
	2. Tipos y Visibilidad de Atributos: Definir el tipo de datos y la accesibilidad de cada atributo. 
	3. Dependencias y Navegabilidad: Incluir las relaciones de dependencia y la dirección del acceso entre clases.

## Secuencia de pasos para crear un D. de clases del diseño

Los pasos a llevar a cabo para crear un diagrama de clases en la etapa del diseño son:

1. Identificar las clases a partir del diagrama dinámico o modelo conceptual. 
2. Dibujar el Diagrama de Clases. 
3. Completar los atributos de cada clase. 
4. Agregar nombres de los métodos. 
5. Incorporar información sobre tipos de atributos y métodos. 
6. Añadir asociaciones necesarias para visibilidad de atributos. 
7. Incorporar flechas de navegabilidad para indicar el acceso entre clases. 
8. Agregar líneas de dependencia (si es necesario) para mostrar relaciones entre clases y atributos. 

Basado en el análisis de diagramas de colaboración e interacción. Produce un diagrama de clases que refleja la estructura detallada del sistema, incluyendo las asociaciones y la navegabilidad necesarias.

## Asociaciones

**Asociaciones**: Dar nombre de papel al final de una asociación. 

**Navegabilidad**: Adornada con una “Flecha de Navegabilidad”. Indica visibilidad desde la clase fuente hacia la clase destino.

![[imgs/8.png|center]]

## Navegabilidad 

La navegabilidad refleja la visibilidad de los atributos y métodos de una clase desde otra, determinando si una clase puede acceder a los datos y funciones de otra.

Situaciones Comunes 
- La flecha de navegabilidad se define en los siguientes casos: 
	- Envió de Mensajes: Clase A envía un mensaje a clase B. 
	- Creación de Instancias: Clase A crea instancias de clase B. 
	- Conexión Continua: Clase A mantiene una conexión con clase B. 

La navegabilidad se interpreta como la visibilidad de atributos de una clase a otra. En programación orientada a objetos, refleja cómo se almacenan y acceden los datos persistentes.

