# Análisis de Sistema
Es importante el modelo de análisis por varios motivos:
- ofrece una especificación más precisa de los requisitos,
- se decribe utilizando el lenguaje de los desarrolladores,
- estructura los requisitos de un modo que facilita si comprensión y su mantenimiento,
- puede considerarse como una aproximación al modelo de diseño.
## Artefactos

## POO
Orientacion a objetos = objeto + clasificación + herencia + comunicación
### Clases y Objetos
> [!note] Clase
> Una **clase** es una descripción generalizada que describe una colección de objetos similares. Todos los objetos que existen dentro de una clase heredan sus atributos y métodos disponibles para la manipulación de los atributos.
> Se aplica ***abstracción*** en este proceso de extraer lo esencial de que se estudia e intenta modelar.

Los <mark style="background: #FF5582A6;">atributos</mark> son caracterísiticas estables, que es una relación binaria entre una clase y cierto dominio.
Los <mark style="background: #ADCCFFA6;">métodos</mark> representan los comportamientos del objeto.
Los <mark style="background: #BBFABBA6;">mensajes</mark> son el medio a través del cual los objetos interactúan. Los mensajes proporcionan una visión interna del comportamiento de objetos individuales, y del sistema OO como un todo.
	**mensaje: \[destino, operacion, parámetros]**
	El  destino define el objeto receptor (es estimulado por el mensaje), operación se refiere al método que recibe el mensaje y parámetros proporciona infomación requerida para el éxito.
	 Tipos:
	- Constructores -> construyen un objeto
	- Destructores -> eliminar un objeto
	- Selectores -> consultar un objeto
	- Modificadores -> modifica un objeto 
	- Iteradores -> 

> [!note] Objeto
> Un **objeto** es una entidad de la vida real. Puede ser tangible o no, de existencia real (una persona) o de existencia ideal (una cuenta de banco).
> 	Objeto -> ID + Atributos + Operaciones
### Encapsulamiento, herencia y polimorfismo
#### Encapsulamiento
Es el proceso de almacenar en una misma sección los elementos de una abstracción que constituyen su estructura y su comportamiento; sirve para separar el interfaz contractual de una abstracción y su implantación.
- Público -> todos pueden acceder a los datos o métodos de una clase
- Protegido -> no son de acceso público, solamente son accesibles dentro de su clase y por sublcases.
- Privado -> se pueden declara miembros accesible sólo para la propia clase.
#### Herencia
Mecansimo por el cual una clase permite heredar las características (atributos y métodos) de otra clase.
![[herencia.png]]
#### Polimorfismo
Habilidad de una clase para implementar métodos con el mismo nombre pero con comportamientos distintos.
## Clasificadores
### Asociación
Las asociaciones llevan la información sobre relaciones entre objetos en un sistema. La propiedad más importante es la de la **multiplicidad**: cuantas instancias de una clase  se pueden relacionar con una instancia de otra clase.
La notación para una asociación binaria es una línea o una trayectoria que conecta las clases que participan. El nombre  de la asociacion se pone a lo largo de la línea, con el nobre de rol y la multiplicidad en cada extremo.
- <mark style="background: #FFB8EBA6;">Agregación</mark>: es una asociación que representa un todo-parte. Está dado por un **diamante hueco** en el extremo de la trayectoria unida a la clase agregada.
	![[agregacion.png]]
- <mark style="background: #FFB8EBA6;">Composicion</mark>: es una asociación más fuerte de asociación, el compuesto es el responsable único de gestionar sus partes. Se muestra con un **diamante relleno** en el extremo compuesto.
	![[composicion.png]]
### Generalización
Es una relacion taxonómica entre una descripción más general y una descripción más específica, que se construye sobre ella y la extiende. Se dibuja como una flecha desde hijo al padre, con un triángulo hueco en el extremo conectado con el padre.
![[generalizacion.png]]
## Diagrama de Colaboración
Un Diagrama de Colaboración describe en forma de gráfico cómo se comunican los objetos para ejecutar las acciones específicas de un caso de uso. Es un tipo de diagrama de interacción cuyo objetivo es describir el comportamiento dinámico del sistema de información mostrando cómo interactúan los objetos clase entre sí.
Ventajas:
1. Permite elegir el orden en que pueden hacerse las cosas.
2. Puede describir procesos o casos de uso.
3. Muestra los aspectos dinámicos de un sistema.
4. Establece las reglas de secuencia a seguir.
5. Ayuda a un programador a desarrollar código a través de una descripción lógica de un proceso.
Elementos: 
- Actor
- Objeto
- Mensaje
![[diagrama de colaboracion.png]]
## 