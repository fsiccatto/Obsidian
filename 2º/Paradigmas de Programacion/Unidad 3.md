# Relaciones entre Clases
## Herencia
El concepto de herencia propone que cada clase tiene propiedades y comportamientos específicos, que les son propios; y otros que heredan de una clase superior que incluye las propiedades y comportamientos que son comunes también a otras clases.
La herencia se vincula así a un tipo de relación entre clases del tipo **superclase/subclase** o padre/hijo, en la cual cada clase hijo (o subclase) tiene sus propios atributos y métodos específicos y hereda otros más generales de su clase padre (o superclase).
### Relaciones de Generalizción/Especialización
La generalización y la especialización son diferentes perspectivas del mismo concepto, la **generalización es una perspectiva ascendente** (bottom-up), mientras que la **especialización es una perspectiva descendente** (top-down).
### Herencia y Encapsulamiento
Tanto los atributos como métodos podían ser calificados con alguno de los siguientes atributos:
- *public*
- *private*
- *protected*
- *friendly*
Un atributo declarado como *protected*, podrá ser accedido directamente desde el interior de su clase (como si fuera *private*) y también desde cualquier subclase que herede de la clase a la que pertenece.
Los atributos calificados como amigables (*friendly*) tienen alcance de paquete. Es decir, son visibles desde cualquier otra clase en el mismo paquete; y están encapsulados para cualquier otra clase que no pertenezca al paquete donde la clase fue definida.
## Clases Abstractas
> [!info] Clase abstracta
> Una clase abstracta es una clase de la que no se pueden instanciar objetos.

Por ejemplo el concepto de vehículo es un concepto abstracnto que para materializarse debe concretarse en un tipo de vehiculo particular.
Luego las clases `Auto, Frigorífico y Remolque` serán **clases concretas**.
### Métodos Abstractos
Un método abstracto es un método que no tiene implementación, sólo se coloca la signatura del método en su declaración, precedido por la palabra *abstract*.
Una clase puede ser abstracta aún cuando no contenga métodos abstractos; pero toda clase que contenga al menos un método abstracto debe ser abstracta.
#### super()
`super(marca, titulo, ruedas, motor, chofer, nro_chasis);`
Activa el constructor con parámetros de la clase `Vehículo`, se construye el subobjeto del tipo `Vehículo` dentro del tipo `Auto`.
En nuestro ejemplo, `super(...)` estaría activando el método constructor que incluimos en la clase `Vehículo`, aunque esta sea abstracta.
Siempre se construye el subobjeto y luego el objeto. De hecho, por esto siempre el método super debe estar colocado en la primera línea del constructor de la subclase.
## Polimorfismo
Sugiere que un mismo mensaje puede vincularse a distintos métodos en tiempo de ejecución tomando así distintas formas.
El uso de polimorfismo favorece la reutilización de código y la escalabilidad ordenada de los desarrollos.