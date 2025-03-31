# Programación Orientada a Objetos
## Clases y Objetos
Una clase es un TAD (tipo abstracto de datos) definido por el programador, que encapsula datos (atributos) y métodos (comportamientos). Estos describen los objetos de nuestro ámbito de estudio.
![[Clase| center ]]
Luego de definirse la clase, podemos definir dos objetos ejemplos:
![[ejemploClase.png| center ]]

``` java
public class Camion { 
	/* Atributos */
	public final String marca;
	private int carga;
	private String propietario;
	
	/* Métodos o comportamientos */ 
	/* Constructor */
	public Camion(String marca, int carga, String propietario){
		this.marca = marca;
		this.carga = carga;
		this.prop = propietario;
	}
	public void setCarga(int kg){
		if(kg>0) this.carga = kg;
	}
	public int getCarga(){
		return carga;
	}
	public void setProp(String prop){
		this.prop=prop;
	}
	public String getProp(){
		return this.prop;
	}
	public void arrancar(){
		System.out.println("arranca camión" + marca);
	}
	public void parar(){
		System.out.println("detiene camión");
	}
	public void cargarCombustible(){
		System.out.println("carga combustible");
	}
	public void registrarPropietario(String prop){
		propietario = prop; System.out.println("registra propietario" + propietario);
	} 
}
```
### Encapsulamiento
Tanto los atributos como los métodos que son miembro de una clase pueden estar calificados por **Calificadores de Acceso a los Miembros**:
- `public`: estará accesible en cualquier punto del programa que tenga acceso a un objeto de la clase.
- `private`: sólo será accesible desde los métodos de la clase.
- `protected`
- `friendly`
Calificar atributos y métodos permite encapsular u ocultar los detalles de la implementación de la clase hacia fuera. Una persona puede manejar un camión sin necesidad de conocer en detalle cómo funciona un motor.
### Instanciar una clase
Vamos a construir dos instancias:
``` java
Camion camionCocaCola = new Camion("Scania", 1.5f, "Juan Perez")
Camion otroCamion = new Camion("Ford",1.3f,"Maria Gomez")
```
El resultado de activar el constructor es construir un **objeto**, es decir, mapearlo en la memoria.
Por lo tanto, como resultado de la activación del constructor, `new` devuelve una referencia, un puntero, al objeto que el constructor mapeó en el Heap. Las variables `camionDeCocaCola` y `otroCamion` son variables locales en el Stack que apuntan al objeto que está en zona de Heap.
![[stackheap.png| center ]]
### Constructores
Un constructor es un método que tiene el mismo nombre de la clase y aunque puede recibir parámetros, no debe ser calificado con ningún tipo de devolución, ni siquiera `void`.
``` java
	/* Constructor */
	public Camion(String marca, int carga, String propietario){
		this.marca = marca;
		this.carga = carga;
		this.prop = propietario;
	}
```
La llamadadel constructor de una clase, mapea un objeto de dicha clase en la memoria dinámica y devuelve una referencia a dicho objeto. En general los constructores se utilizan también para inicializar los valores de los atributos de la clase.
#### Constructores por defecto
Si el programador no implementa un constructor, el compilador proveerá uno por defecto cuando compile el código de la clase.
El constructor por defecto es un constructor sin parámetros que inicializa a cero los atributos numéricos, a false los booleanos y con null los que sean referencia a otros objeto.
Para activar el constructor por defecto, se deberá utilizar `new NombreDeLaClase();`.
#### Sobrecarga de Constructores
Una clase puede tener más de un constructor, el cual debe diferenciarse en cantidad, orden y/o tipo de parámetros de los otros constructores definidos.
``` java
public class Camion {
	...
	/* Constructor */
	public Camion(String marca, int carga, String propietario){
		this.marca = marca;
		this.carga = carga;
		this.prop = propietario;
	}
	/* Constructor que solo inicializa el atributo propietario */
	public Camion(String propietario){
		this.prop = propietario;
	}
	/* Constructor de copia construye un objeto como una copia de otro */ 
	public Camion(Camion obj){
		this.marca = obj.marca;
		this.carga = obj.carga;
		this.prop = obj.propietario;
	}
	...
}
```
Los constructores, que se diferencian por su signatura (cantidad, tipo u orden de los parámetros formales), se llaman **constructores sobrecargados**.
Un constructor, que recibe como argumento un objeto del mismo tipo que se está construyendo, y lo utiliza para copiar los valores de sus atributos se llama **Constructor de Copia**. Veamos como se utiliza:
``` java
1. Camion camionDeCocaCola = new Camion("Scania", 1.5f,"Juan Perez");
2. Camion otroCamion = new Camion("Ford",1.3f,"Maria Gomez");
3. Camion tercerCamion = new Camion(otroCamion);
4. Camion cuartoCamion = camionDeCocaCola;
```
![[constructor de copia.png| center ]]
3. Usar el constructor de copia para crear un nuevo objeto en memoria (`tercerCamion`) que copia el estado del objeto `otroCamion` prexistente.
4. Asigna la referencia guardada en la variable `camionDeCocaCola` a la variable `cuartoCamion`. De esta forma, ahora tenemos dos punteros al mismo objeto en el heap; pero **no se creó ningún objeto nuevo**.
### Finalizadores
Toda clase Java cuenta con un método finalizador predefinido en el lenguaje, que devuelve explícitamente los recursos al sistema. Este método llamado `finalize()`, único por cada clase, es un método sin argumentos y que no recibe parámetros.
### Referencia this
En Java, cada objeto o ejemplar de una clase tiene acceso a una referencia a sí mismo, llamada referencia `this`. De este modo, `this` es un apuntador al objeto activo, es decir, el objeto desde el que se activa un método de instancia o se accede a un atributo.
### Método set/get
Es común que las clases ofrezcan métodos `public` que permitan a los clientes de la clase (los que usan sus servicios) asignar (o setear - _set_) valores a los atributos privados de la clase; u obtener (_get_) valores de dichos atributos.
Se llaman, por convención, métodos _set_/_get_ seguidos del nombre del atributo que se quiere acceder.
Esto lo hacemos para poder hacer validaciones y que el usuario no agregue cualquier cosa al atributo (que es privado).
### Atributos constantes o finales
El calificador final indica que un atributo es una constante simbólica, es decir, que el valor que toma el atributo en al construirse una instancia del objeto no se puede modificar mientras el objeto esté vivo (mapeado en la memoria). Los miembros constantes o finales de una clase no pueden modificar su valor una vez inicializados.
Es buena práctica **declarar finales a los atributos públicos** de una clase.
Tenemos que inicializar la constante en el constructor de la clase o en la declaración. Si no lo hacemos, tendremos un error de sintaxis.
```
<calificador ctte> <identificador> <valor>
```
