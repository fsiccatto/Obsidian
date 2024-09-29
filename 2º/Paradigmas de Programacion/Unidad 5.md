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
![[imgs/nohacen.png]]
![[imgs/nohacen2.png]]

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
En este caso, decimos que `Box <extends Number>` es una clase parametrizada actoda. 
En Java no existe la herencia múltiple, pero si podemos heredar de una clase e implementar varias interfaces distintas con `&`.
```java
public class MiClase <T extends A & B & C> {...}
```
Otra cosa que podemos hacer es utilizar más de un parámetro de tipo, separando los tipos con comas. Supongamos que queremos crear una clase parametrizada que reciba dos tipos diferentes de números
```java
public class Sumador <T1 extends Number, T2 extends Number> {...}
```
También podemos crear clases abstractas e interfaces como clases genéricas. E incluso métodos.
### Métodos parametrizados
Un método que utiliza tipos genéricos en sus parámetros formales se denomina Método parametrizado
```java
public <U extends Comparable> void mostrar (U obj){…}
```
### Parametrización con comodines
cuando las clases parametrizadas se utilizan con jerarquías de clases (herencia), se debe considerar que los tipos genéricos son **invariantes**. Esto es, dada una clase `B`, subtipo de otra clase `A`, luego la clase parametrizada o genérica `List <B>` NO es subtipo del genérico `List <A>`.
![[imgs/parametrizacion con comodines.png]]
,Java ofrece la posibilidad de utilizar **el tipo comodín (?)** que nos ayuda en el trato con los tipos genéricos y que significa, ni más ni menos, «cualquier tipo de objeto».
Los **tipos comodines o wildcard** se utilizan en las clases parametrizadas para indicar un tipo desconocido, que puede ser de cualquier clase y será superclase o subclase para todas las demás.
```java
static void imprimirColeccion (<Collection<?> c) {
	for (Object e: c) {
		System.out.println(e);
	}
}
```
- `<?extends xClase>`
	- Establece un límite superior
	- Cualquier clase que sea sublcase xClase
	- Para la semántica $\ll in\gg$ de datos en métodos
- `<? super xClase>`
	- Establece un límite inferior
	- Cualquier clase que sea super de xClase
	- Para la semántica $\ll out\gg$ de datos en métodos
Los comodines pueden utilizarse tanto con la palabra `extends` (upper bounds) como con la palabra `super` (lower bounds), para limitar el rango de objetos aceptados a un subtipo concreto, o a un supertipo respectivamente.
![[imgs/parametrizacion con comodines ejemplo.png]]
#### Diferencias entre el uso de comodines y parámetros
Un comodín solo puede tener un límite (superior o inferior), mientras que un parámetro de tipo puede tener varios límites (Ejempo: `T extends Object & Comparable`).
Un comodín puede tener un límite inferior o superior, mientras que no existe un límite inferior para un parámetro de tipo.

En síntesis, podemos decir que el uso de clases y métodos parametrizados aporta mayor potencia a la POO. De hecho, todas las clases de Java que manejan contenedores usan tipos genéricos.
Sin embargo, y a diferencia de otros lenguajes, el uso de `generics` en Java sólo se implementa a alto nivel y no a nivel de bytecode. El compilador de Java sustituye los tipos genéricos por tipos concretos en tiempo de compilación. A esta técnica se la llama **Borrado de tipo**.