# Relaciones entre clases y objetos
Relaciones en POO: 
- **Dependecias**: representan ***relaciones de uso*** entre clases. Es decir, clases que usan los servicios de otras.
- **Asociaciones**: repesentan relaciones estructurales entre objetos.
- **Generalizaciones/Especializaciones**: que conectan clases más genrales con otras más especializadas en lo que se conoces como relaciones padre/hijo. Es decir, **Herencia**.
## Relaciones de Uso
Una relación de uso es un tipo de ***relación débil*** entre dos clases. Una relación débil es aquella que se da entre dos objetos que intercambian mensajes entre sí, pero en la cual la vida útil de uno de los objetos no depende de la vida del otro.
## Relaciones de Asociación
Una asociación es una relación estructural que especifica que los objetos de una clase están conectados con los objetos de otra clase.
Una asociación normal entre dos clases representa una relación estructural **entre iguales**, es decir, clases que están conceptualmente al mismo nivel, en la misma jerarquía, sin que ninguna parte sea más importante que la otra.
## Agregación y Composición
Sirven para modelar relaciones del tipo **todo/parte** en donde una clase representa un todo que está formado o compuesto de elementos más pequeños que forman las partes.
La Composición (relación fuerte) que implica que el tiempo de vida del objeto *parte* depende del tiempo de vida del objeto *todo*.
La Agregación (relación más débil) es independiente el tiempo de vida del objeto *parte* del tiempo de vida del objeto *todo*.
# Paquetes
Un paquete es un conjunto de clases, lógicamente relacionadas entre sí, agrupadas bajo un nombre. Ayudan a organizar las clases en grupos para facilitar el acceso.
Las clases en un paquete, que son **públicas** (o exportables) constituyen la **interfase** del paquete hacia fuera o su parte pública. Aquellas que no lo son, y sólo brindan servicios dentro del propio paquete, constituyen su **implementación** o parte privada. Esto implica que la organización de clases en paquetes supone también, un nivel más de protección o **encapsulamiento** para las mismas.
## Protección de clases
La protección de una clase determina la relación que tiene con otras clases de otros paquetes. Distinguimos dos niveles de protección:
- de paquete $\to$ Una clase con nivel de protección de paquete solo puede ser utilizada por las clases de su paquete. No está disponible para otros paquetes, ni siquiera para los subpaquetes 
- público $\to$ Una clase pública puede ser utilizada por cualquier otra clase de otro paquete. Por defecto, una clase, tiene el nivel de protección de paquete (friendly).
	``` java
	import mipaquete.Modelo1.clases.*
	```
	![[import paquete.png]]
	Estos `.class` son clases públicas o exportables, son a las que se tiene acceso.
Toda clase Java perteneces a un paquete. Si no es uno que indicamos explícitamente, pertenece al paquete "predeterminado" por defecto.
## Crear un paquete
1. Elegimos el nombe que queremos darle al paquete
	El nombre supone una organización jerárquica para las clases
2. Creamos la estructura jerárquica de carpetas en el disco duro
	La ruta de la caprtea raíz de esta estructura jerárquica tiene que estar apuntada por la variable de entorno **CLASSPATH**. Es decir, CLASSPATH $\to$ `mipaquete`. 
3. Especificar el paquete al que pertence la clase
	Cuando se define una clase, se debe especificar a qué paquete pertenece utilizando la sentencia $package \space mipaquete.Modelo1.clases;$

