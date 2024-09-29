# Clases Anidadas
Una clase anidada es una clase que se define dentro de otra clase
![[imgs/clases anidadas.png]]
Las clases anidadas (*nested class* en Java) se descomponen en clases anidadas estáticas, que sirven en general para abordar problemas del tipo del contexto global, y las clases internas o clases anidadas no estáticas, que es el caso más típico, en donde una clase existe sólo con fines de brindar servicio a su clase contenedora.
Las clase anidadas pueden utilizarse para:
1. Aumentar el encapsulamiento
2. Mejorar la legibilidad del código y facilitar su mantenimiento posterior
## Clases anidadas internas *inner class*
Una clase interna se debe definir dentro de otra sólo cuando tenga sentido en el contexto de la clase que la incluye, **Clase Contenedora**, o cuando depende de la función que desempeña la clase que la incluye.
Diferenciamos entre:
- Locales: son clases definidas dentro de un bloque de código de la clase contenedora. Por ejemplo, dentro de un método.
```java
class A { // clase contenedora
	...
	public void unMetodo() {
		...
		class B { // clase local
			...
		}
		...
		B = obj = new B();
	}
}
```
> [!info] Clases anidades: locales
> - Clase interna definida en un bloque de código
> - Sólo visibles y usables dentro del bloque
> - No pueden
> 	- Incluir un modificador de acceso
> 	- Ser estáticas
> - Utilidad
> 	- Claridad de código, evita el exceso de clases pequeñas
> 	- Encapsulamiento y ocultamiento en paquetes
> 	- Agrupamiento de clases relacionadas
> 		- Proximidad entre la definción y el uso de las clases
> - Aplicación: tratamiento de eventos, creación de clases de ayuda o adaptación, wrappers, ...
- Anónimas: son clase locales “sin nombre”, que se utilizan para crear una única instancia u objeto. Este objeto se crea en la misma expresión donde se define la clase.
```java
class A { // Clase Contenedora 
	...
	public void unMetodo() { 
		...
		OtraClase obj = new OtraClase () { // Clase Anónima 
			...
		}; 
	...
	} 
	...
}
```
- Miembro: son clases internas que se definen en el área de declaraciones de la clase externa y en general se usan para tipar un atributo de la clase contenedora.
```java
class A { // Clase Contenedora
	...
	class B { // Clase Local
		...
	} 
	...
	//Atributos de A
	private B unMiembro; // atributo de la clase miembro
	...
}
```
Una clase miembro, es una clase anidada que se define en la zona de declaración de la clase externa y por lo tanto tiene un nombre propio. En general se utilizan para declarar un miembro o atributo de la clase contenedora.
Una clase miembro, es un elemento más de la clase que la contiene, y cómo tal se le aplican las mismas reglas que para el resto de los miembros. De este modo, pueden calificarse como públicas, privadas, protegidas o friendly. El hecho de que una clase miembro sea privada no impide que se pueda acceder y usar desde la clase contenedora.

---
Las variables locales al método deben declararse final. De esta manera se garantiza que la variable local y la copia que se mantiene en la clase siempre tienen el mismo valor.
![[imgs/clases anidadas ejemplo.png]]
