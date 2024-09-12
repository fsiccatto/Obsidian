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
Los datos mantenidos en archivos se conocen como **datos persistentes**. 
En Java necesitamos importar el paquete `java.io`. 
## Archivos Secuenciales
Para manipular archivos secuenciales, Java provee las siguientes clases:

- La clase `File` que nos permitirá definir un puntero a un archivo físico en disco, existente o por crearse.
- La clase `FileInputStream` que nos permitirá procesar el flujo de entrada desde un archivo.
- La clase `FileOutputStream` que nos permitirá administrar el flujo de salida hacia un archivo.
- Las clases `DataInputStream` y `DataOutputStream` para E/S respectivamente, nos permiten definir flujos de datos, dentro de los flujos definidos para archivos, los cuales proveen métodos específicos para manejar distintos tipos de datos primitivos: `byte, byte [], char, String, int, boolean`, etc.
```java
package archivos;

import java.io.*;

public class ArchivoSecuencial {
    private File archivo;

    public ArchivoSecuencial(String file) {
        this.archivo = new File(file);
    }

    public void grabar(String s) {
        FileOutputStream fos = null;
        DataOutputStream dos = null;
        try {
            // true indica que se quiere abrir el archivo en modo append
            fos = new FileOutputStream(archivo, true);
            dos = new DataOutputStream(fos);
            dos.writeBytes(s + "\n");
        } catch (FileNotFoundException e) {
            System.out.println("No se encontró el archivo");
        } catch (IOException e) {
            System.out.println("Error al escribir el archivo");
        } finally {
            try {
                if (dos != null) dos.close();
                if (fos != null) fos.close();
            } catch (IOException e) {
                System.out.println("Error al cerrar los streams");
            }
        }
    }

    public void leer() {
        FileInputStream fis = null;
        DataInputStream dis = null;
        try {
            fis = new FileInputStream(archivo);
            dis = new DataInputStream(fis);
            System.out.println(dis.readLine());
        } catch (FileNotFoundException e) {
            System.out.println("No se encontró el archivo");
        } catch (IOException e) {
            System.out.println("Error al leer el archivo");
        } finally {
            try {
                if (dis != null) dis.close();
                if (fis != null) fis.close();
            } catch (IOException e) {
                System.out.println("Error al cerrar los streams");
            }
        }
    }

    public static void main(String[] argv) {
        ArchivoSecuencial miarchivo = new ArchivoSecuencial("archivo.txt");
        miarchivo.grabar("Hola mundo");
        miarchivo.leer();
    }
}
```
## Archivos de Acceso Aleatorio
Java utiliza la clase `AccessRandomFile` para manipular archivos de acceso aleatorio.
```java
package archivos;

import java.io.*;

class Persona {
    int dni;
    String nombre;
    int edad;
    char sexo;

    public Persona(int doc, String n, int e, char s) {
        dni = doc;
        nombre = n;
        edad = e;
        sexo = s;
    }
}

public class ArchivoAleatorio {
    private static File archivo;
    private static RandomAccessFile datos;
    private Persona registro;

    static {
        archivo = new File("archivo.dat");
        try {
            datos = new RandomAccessFile(archivo, "rw");
        } catch (FileNotFoundException e) {
            System.out.println("Error: No se encontró el archivo");
        }
    }

    public void grabar(Persona per) {
        try {
            registro = new Persona(per.dni, per.nombre, per.edad, per.sexo);
            datos.seek(datos.length());
            datos.writeInt(registro.dni);
            datos.writeUTF(registro.nombre);
            datos.writeInt(registro.edad);
            datos.writeChar(registro.sexo);
        } catch (IOException e) {
            System.out.println("Error de escritura en archivo");
        }
    }

    public void recuperar(int dni) {
        int doc;
        try {
            datos.seek(0);
            do {
                doc = datos.readInt();
                if (doc == dni) {
                    System.out.println(doc + " " +
                            datos.readUTF() + " " +
                            datos.readInt() + " " +
                            datos.readChar());
                }
            } while (datos.getFilePointer() < datos.length());
        } catch (IOException e) {
            e.printStackTrace(); // para facilitar depuracion en caso de error
            System.out.println("Error de lectura de archivo");
        }
    }

    public static void main(String[] arg) {
        ArchivoAleatorio arch = new ArchivoAleatorio();
        Persona per = new Persona(1234, "Luis", 20, 'm');
        arch.grabar(per);
        per = new Persona(5678, "Juan", 19, 'm');
        arch.grabar(per);
        arch.recuperar(1234);
        arch.recuperar(5678);
    }
}
```
## Serialización de Objetos
> [!info] Importante
> Normalmente, la operación de enviar una serie de objetos a un archivo persistente  recibe el nombre de **serialización**, y la operación de leer su estado desde un archivo para reconstruir los objetos en memoria, recibe el nombre de **deserialización**.

Para realizar estas operaciones, el paquete `java.io` proporciona las clases:
- `ObjectOutputStream` → con su método `writeObject()`
- `ObjectInputStream` → con su método `readObject()`

La clase `ObjectOutputStream` se encarga de convertir los atributos de un objeto  (excepto las variables estáticas) más el tipo de clase y el prototipo de la misma, en una  secuencia o **flujo de bytes**. Este flujo de bytes debe ser pasado luego cómo parámetro a alguna clase que se encargue de escribirlo a disco; por ejemplo, la clase `FileOutputStream` que ya conocemos.
La clase `ObjectInputStream`, toma un flujo de bytes leídos desde un fichero en disco, por ejemplo: a partir de la clase `FileInputStream` y hace el proceso inverso, es decir, reconstruye el objeto en la memoria.
![[imgs/serializacion.png]]
Para poder serializar los objetos de una clase, ésta debe implementar la interfase `Serializable`. Es una interfaz vacía.
```java
import java.io.*;

class Una implements Serializable {
	...
}
```

> [!warning] Importante
>  Si un atributo en una clase es una referencia a objetos de otra clase, para poder serializarla, la clase asociada, también debe implementar la interfase `Serializable`
>  
-  Escribir a fichero
```java
FileOutputStream fos = new FileOutputStream(“archivo.dat”);
ObjectOutputStream oos = new ObjectOutputStream (fos);
oos.writeObject(new Una(...));
oos.close();
```
- Leer desde fichero
```java
FileInputStream fis = new FileInputStream(“archivo.dat”);
ObjectInputStream ois = new ObjectOutputStream (fis);
Una obj = (Una) ois.readObject();
ois.close();
```
- Ejemplo de persistir objetos de una clase asociativa
```java
package legal;

import java.io.*;

public class Titulo implements Serializable {
    public final String prop;

    public Titulo(String propietario) {
        this.prop = propietario;
    }

    public void persistir() {
        try {
            FileOutputStream fos = new FileOutputStream("c:/" + prop + ".dat");
            ObjectOutputStream oos = new ObjectOutputStream(fos);
            oos.writeObject(this);
            oos.close();
            fos.close();
        } catch (FileNotFoundException ex) {
            System.out.println("No se encontró el archivo");
        } catch (IOException ex) {
            System.out.println("Se produjo un error de E/S");
        }
    }

    public static Titulo leerTitulo(String propietario) {
        Titulo titulo = null;
        try {
            FileInputStream fis = new FileInputStream("c:/" + propietario + ".dat");
            ObjectInputStream ois = new ObjectInputStream(fis);
            titulo = (Titulo) ois.readObject();
            ois.close();
            fis.close();
        } catch (FileNotFoundException ex) {
            System.out.println("No se encontró el archivo");
        } catch (IOException ex) {
            System.out.println("Se produjo un error de E/S");
        } catch (ClassNotFoundException ex) {
            System.out.println("Error de conversión de clase");
        }
        return titulo;
    }
}

```
## Calificador `transient`
El calificador `transient` aplicado sobre una variable de instancia, indica que la variable  no es una parte persistente del estado del objeto, por lo tanto, no será tomada en cuenta  en la serialización/descerialización del mismo. Es decir, todo atributo calificado con `transient` no será persistido.
# Interfases
Una interfase, es una estructura sintáctica que consta de dos partes: su **nombre**, precedido por la palabra reservada `interface`, y el **cuerpo de la interfaz**, encerrado entre llaves
```java
interface XX {
    int a = 10;
    int b = 20;
    byte c = 30;
    char d = 'a';

    void unMetodo(int x, float y);
    int otroMetodo();
}
```
Características:
- Los atributos no se califican ya que son por defecto **públicos**, **finales** y **estáticos**.
- Los métodos tampoco se califican ya que son por defecto **públicos** y **abstractos**.
- No tiene constructor.
- Una interface tiene niveles de protección público y de paquete.
- Cualquier clase, puede tener acceso a las constantes (atributos) de una interfaz a través su nombre (`XX.b`).
Las interfaces se usan para definir características muy generales o patrones de conducta para un determinado tipo de clases. Estas son las clases que implementan la interfaz.
```java
class B {
	... 
} 
class A extends B implements XX {
	... 
}
```
Si una clase implementa una interfaz, estamos obligados a implementar todos los métodos declarados en la misma. De lo contrario, la subclase seguirá teniendo métodos abstractos y deberá ser abstracta.
> [!info] Interfaz
> Una interface Java, es entonces un dispositivo que define un conjunto de mensajes (métodos) que se pueden aplicar a muchas clases de objetos (aquellas que implementen la interface), a los que cada una de ellas debe responder de la forma adecuada (a partir de la aplicación de polimorfismo). Por eso, una interfaz recibe también el nombre de **protocolo**.
## Herencia mútltiple
La herencia múltiple es la capacidad de un objeto de ser de más de un tipo a la vez. En términos estáticos, es cuando una clase hereda de más de una clase a la vez.
![[imgs/herencia multiple.png]]
<mark style="background: #BBFABBA6;">JAVA NO PERMITE HERENCIA MÚLTIPLE.
</mark>
### Pseudo-Herencia Múltiple en Java
Una clase Java puede heredar de una sola clase; pero de una o más interfaces.
```java
interface A { 
	... 
} interface B { 
	... 
} class Z { 
	... 
} class X extends Z implements A,B { 
	... 
}
```