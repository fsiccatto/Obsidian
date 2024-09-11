# Gestión de errores - Excepciones
Hablaremos en principio de tratamiento de errores como tratamiento de Excepciones. Se propone:
1. Modelar los errores o excepciones como **Objetos**. De esta forma cuando se produce el error, se puede instanciar un objeto de la clase de error correspondiente y tratarlo con sus propiedades y métodos correspondientes.
	![[imgs/jerarquia de errores.png]]
	Los `Error` son problemas del sistema, en general de hardware. Los `Exception` son causados por problemas que el programador puede manejar, en general errores en tiempo de ejecución.
2. Utilización de una estructura de control de flujo, que permita detectar un error cuando se produce y transferir el control a otra área de código encargada de manejarlo. `try-catch-finally`
```java
int leerArchivo {
	incializar codError = 0;
	try {
		abrir el archivo;
		determinar su tamaño;
		asignar suficiente memoria;
		leer el archivo a la memoria;
		cerrar el archivo;
	}
	catch (errorAbrirArchivo) {codError = -5;}
	catch (errorDeterminacionLongitud e2) {codError = -3;}
	catch (errorReservarMemoria e3) {codError = -2;}
	//...
}
```
## Cláusulas throws y throw
La cláusula `throws`, que se incorpora en la cabecera de un método, lista las excepciones que eventualmente se pueden producir en dicho método. Es decir, informa o notifica a los bloques que llaman a este método, que en el mismo se puede producir determinados tipos de errores.
```java
class EE extends Exception {
	...
}

void metodoC() throws EE {
	...
	if (?) throw new EE();
	...
}

void metodoB() {
	...
	try {metodoC();}
	catch (EE x) {...}
	...
}
```
La cláusula `throw`, se asocia a la activación del constructor de un determinado tipo de error y se utiliza para construir un objeto de error y lanzarlo. Es decir, throw se utiliza para lanzar explícitamente una excepción, cuando se producen determinadas condiciones.
Es importante el paso de la pelota del método.
# Clasificador `static`
Las variables de clase, que se identifican mediante el calificador static, son atributos que no forman parte de la estructura de cada objeto. Un atributo de clase es una variable única para la clase que se aloja en la región estática de memoria y que es compartida por todos los objetos instanciados de esa clase.
Para acceder a un atributo `static`, no necesitamos que existan objetos de la clase; lo podemos hacer directamente a partir del nombre de la clase.
```java
class A { 
	private byte vinstancia; 
	private static byte vclase; 
}
A.vclase = 20;
```
## Métodos de clases
Un método declarado `static` es un método de clase. Este tipo de métodos no se ejecutan para un objeto en particular, sino que se aplican en general donde se necesiten, lo que impide que puedan acceder a un atributo o variable de instancia. Tampoco pueden activar un método de instancia.
```java
class A {
	private byte vinstancia;
	private static byte vclase;
	 
	public void setVInstancia(byte b) {
		vinstancia = b;
		vclase = b; //Si se puede hacer. No es un error.
	}
	public static void setVClase(byte b) {
		vclase = b;
		//vinstancia = b; ¡¡ERROR!!
		//this.setVInstancia(b); ¡¡ERROR!!
	} 
}

public class UnaClase {
	public static void main (String [] args) {
		A.setVClase((byte) 3);
	}
}
```
El método `setVClase` del ejemplo anterior puede acceder a `vclase` porque es un miembro estático, pero no podría acceder a `vinstancia`, ya que esta no es `static`. Tampoco se puede activar un método no `static`. Un método `static` carece de referencia this.
### Constructor `static`
Un constructor estático es un método anónimo que no tiene parámetros, no retorna ningún valor, y es invocado automáticamente por el sistema cuando se carga la clase.
```java
static {
	//iniciación de los atributos de la clase.
}
```
Esto permite que los atributos de clase tengan un valor aun cuando no se hayan instanciado objetos de la clase.
# Calificador `final`
## Métodos finales
Un método final, es un método que no puede redefinirse.
Esta técnica se conoce como **inclusión de código en línea,** por eso se les llama **métodos inline**. El compilador hace sólo la inclusión de código en línea (si son final) cuando el método es corto y sencillo.
```java
public final void unMetodo () { .... }
```
## Clases finales
Una clase final o constante, es una clase de la que no se pueden derivar subclases. Además, cuando una clase se declara final, todos sus métodos son automáticamente finales.
```java
public final class unaClase () { .... }
```

> [!info] Los métodos declarados como `private` y como `static` son implicitamente finales.

# Persistencia de Objetos