# Clases parametrizadas
## Generics
Gracias a los generics podemos especificar el tipo de objeto con que trabajará una clase, de forma que el compilador conozca a priori, el tipo de objeto que vamos a utilizar, evitándonos así la necesidad de casteo.
Para utilizarlo solo debemos añadir el tipo parámetro después del nombre de la clase, y utilizar el nombre de este tipo genéroco donde usaríamos un tipo concreto. Se suele utilizar ina sola letra mayúscula para el tipo genérico.

Los generics nos permiten crear una clase que pueda operar con cualquier tipo de dato, pero este tipo no se especifica hasta que se instancie la clase. Por eso la clase es genérica o parametrizada.
- E elemento
- K clave
- N numero
- T tipo
- S, U, etc (otros tipos)
- V valor
```java
class Box <T> { // especificación de clase generica
	private T objM
	public void add(T obj) {this.obj = obj;}
	public T get() {return this.obj}
}
public class Ejemplo {
	public static void main(String[] args) {
	Box<String> p = new Box(); // Solo se pueden agregar objetos String
	p.add(new String("Hola"));
	String s = p.get(); // No requiere 'cast'
	System.out.println(s);
	}
}
```
Declaramos la clase `Box`, como una clase parametrizada o generic. El argumento que se envíe al parámetro `T`, cuando se instancian objetos de la clase, definirá el tipo de dato para el miembro `obj` de `Box`. Por lo que cada vez que usemos `p` no tendremos que castearlo.
### Generalidades
- ⚔Clases que operan con cualquier tipo de dato, donde el tipo:
	- No se conoce hasta que se instancie la clase
	- Es un parámetro de tipo formal
	- No puede ser un tipo primitivo
- ⚔Principal utilidad en el uso de colecciones
- ⚔Se aplican reglas estáticas de verficiación de tipos
- ⚔No es necesario usar "cast"
- ⚔Se peuden parametrizar los métodos estáticos
- ⚔No se pueden:
	- ☠Crear isntancias de tipos genéricos
	- ☠Usar genéricos declarados externamente en miembros estáticos
	- ☠Heredar de `Throwable`
No solo se pueden parametrizar las clases, sino también los métodos de una clase (incluso si son estáticos), de forma que puedan recibir argumentos de tipos genéricos. Sobre esto profundizaremos más adelante.
Cosas que NO se pueden hacer:
![[nohacen.png]]
![[nohacen2.png]]

Usos de clases parametrizadas y sus estructuras sintácticas
- Cualqueir tipo T que herede A y de B
	`public class Divisor<T extends A&B>{...}`
- Los tipos T1 y T2 heredan de Number
	```java
	public class Sumador<T1 extends Number, T2 extends Number> {
		public T1 imprimir(T2 objeto) { ... }
	}
	```
- Metodo parametrizado
	`public<T extends Comparable> void impirmir(T objeto){...}`
- Creación de una instancia de tipo genérico
	`T otro = (T)obj.getClass().newInstance();`
### Parametrización acotada
