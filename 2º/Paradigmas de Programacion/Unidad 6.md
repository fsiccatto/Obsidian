# Clases Anidadas
Una clase anidada es una clase que se define dentro de otra clase
![[imgs/clases anidadas.png | center]]
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
> [!info] Clases anónimas
> Las clases anónimas son un caso particular de clases internas en las que la implementación de la clase se define al mismo tiempo que se instancia un objeto. Esto se basa en que sólo se necesita un único objeto de la clase interna, y entonces, se puede evitar el nombre la clase, logrando así un mayor nivel de encapsulamiento.
> Es más confuso, por lo que debe estar muy justificado su uso.

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
> [!info] Clase miembro
> - Clase interna que es miembro de otra clase
> - Pueden clasificarse públicas, privadas o protegidas
> 	- No impide su acceso desde la clase externa
> - Cada instancia de una clase miembro
> 	- Se asocia a una instancia de la clase contenedora
> 	- Tiene acceso completo y directo a la clase externa
> 	- No puede tener miembros estáticos
> 	- No puede tener el mismo nombre que la externa
> 

---
Las variables locales al método deben declararse `final`. De esta manera se garantiza que la variable local y la copia que se mantiene en la clase siempre tienen el mismo valor.
![[imgs/clases anidadas ejemplo.png | center]]
### Clases anidadas internas anónimas
![[imgs/clases anonimas.png| center]]
### Clases anidadas estáticas
> [!info] Clases e interfaces de alto nivel
> - Clases estáticas **anidadas** (*nested*) dentro de otra clase
> - Deben calificarse `static`
> - Solo se pueden anidar dentro de clases normales o de clases internas de alto nivel
> - No es necesario un objeto de la clase externa para crear un nuevo objeto de la clase interna estática
> - Modo de referenciarlas
> 	- `NombreClaseExterna.NombreClaseInterna`
> - Desde la clase estática interna sólo se pueden acceder a los miembros estáticos de la clase externa
> - Al compilar el `.class` se genera
> 	- `NombreClaseExterna$NombreClaseInterna`

Una clase anidada estática no puede hacer referencia directamente a variables de instancia o métodos de instancia definidos en la clase contenedora. De lo contrario, estaríamos permitiendo llamar a un atributo o método de instancia cuando aún no existe ningún ejemplar de la clase.
Pueden acceder de manera directa a los miembros estáticos de su clase contenedora, incluso si son privados al igual que sucede en todos los casos de clases anidadas.
```java
public class ClaseExterna {

    public void metodoNoEstaticoExterno() {
        System.out.println("metodoNoEstatico de la " + ClaseExterna.class.getName());
    }

    public static void metodoEstaticoExterno() {
        System.out.println("metodoEstatico de la " + ClaseExterna.class.getName());
    }

    private static class ClaseAnidadaEstatica {
        private static int i;
        private int j;

        private static void metodoEstatico() {
            // ERROR: no se puede invocar un método no estático de la clase contenedora
            // metodoNoEstaticoExterno(); 

            System.out.print("metodoEstatico de la " + ClaseAnidadaEstatica.class.getName());
            metodoEstaticoExterno(); // OK
        }
    }
}

```
Una clase anidada estática solo puede declararse dentro de una clase normal o dentro de otra clase anidada estática o de alto nivel.
Lo que estudiamos en este apartado respecto de las clases anidadas, también es válido para las **interfaces anidadas**. Recordemos que las interfaces son implícitamente públicas y estáticas.
Las clases anidadas estáticas, admiten todos los modificadores de acceso, como cualquier miembro de una clase.
Para crear un objeto para la clase anidada estática, se usa la siguiente sintáxis:
```java
ClaseExterna.ClaseAnidadaStatic nested_object = new ClaseExterna.ClaseAnidadaStatic();
```
Un uso común de las clases internas estáticas es como clase auxiliar pública, cuya utilidad sólo sirve a su clase contenedora. Podrían ser declaradas como externas (ya que su uso es el mismo), sin embargo, suelen anidarse para vincular su nombre al espacio de nombres de la clase contenedora o para que la traducción del mundo real al modelo resulte más natural.
```java
public class Calculo {
	private double x;
	private double y;
	private Operacion tipo;
	
	private static class Operacion {
		int suma = 0; int resta = 1;
		int producto = 2;
		int division = 3;
	}
}
```
![[imgs/sintaxis.png | center]]
