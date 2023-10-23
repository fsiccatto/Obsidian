# Archivos y Registros
## Registros
Un registro es una **colección finita y ordenada de elementos, posiblemente heterogéneos** que se tratan como una unidad. Los elementos de un registro se llaman *campos*. Un campo es un área específica de un registro utilizado para una clase particular de información.
El registro es una estructura de datos simple. Está compuesto por otras estructuras de datos. Son los componentes básicos de los Archivos y de las Bases de Datos.
### Formación de registros
La estructura de datos registro permite que un conjunto de elementos de información, lógicamente relacionados, se pueda agrupar explícitamente. Deriva de las relaciones con otra información.

| tarea | numEmpl | sueldo | domicilio | codProyecto |
| ----- | ------- | ------ | --------- | ----------- |
```
TIPO
Domicilio= REGISTRO
calle: CADENA
nro: ENTERO
localidad: CADENA
FINREGISTRO

TIPO
Empleado = REGISTRO
tarea: CADENA
numEmpl: ENTERO
sueldo: REAL
dom: Domicilio
codProyecto[6]: ENTERO
FIN REGISTRO
```
#### Operaciones
El principal propósito es agrupar campos lógicamente para ejecutar sobre ellos operaciones de entrada/salida.
Los elementos de registro se pueden referenciar de forma individual o bien en grupo de manera colectiva para las operaciones de entrada/salida.
Las operaciones que se pueden ejecutar sobre los elementos son de acuerdo con sus tipos de datos individuales.
## Archivos
Un archivo es una colección de ocurrencias de registros lógicamente relacionados que se tratan como una unidad. Todos los registros del archivo son del **mismo formato**. Las operaciones que pueden realizarse dependen de los registros y de los tipos de datos de los elementos.
#### Clasificiación de archivos
Por función
1. *Maestro*: Representa una visión estática del negocio. Contiene datos relativamente permanentes o datos históricos. Ej clientes, productos, personal.
2. *De transacciones*: Representa eventos o actividades del negocio que implican por lo general agregar un registro, modifcar o eliminar. Ej ventas, liquidación de haberes.
3. *De reporte*: Datos formateados para ser representados al usuario. El archivo enviado puede ser enviado a cola de impresión o pantalla.
4. *De trabajo*: Es temporal en el sistema. No es de largo plazo, ni tiene entradas/salidas. Se usa por lo general para pasar datos de un programa a otro.
5. *De programa*: Contiene instrucciones para procesar datos. Pueden ser de código fuente o el resultado de una compilación.
6. *De texto*: Contiene datos alfanuméricos y gráficos ingresados a través de un editor de textos.
#### Maneras de Acceder
1. Entrada: cuando el programa solamente lo lee.
2. Salida: es escrito por el programa.
3. Entrada/salida: es leído y escrito durante la ejecución de un programa.
#### Organizaciones de archivos
Es la técnica utilizada para representar y **almacenar registros en archivos**.
1. Secuencial
2. Relativa
3. Secuencial indexado
4. Multi-llave
Corresponde a la ordenación física de los registros almacenados. La organización más apropiada está dada por las características del medio de almacenamiento y por el tipo de operaciones a ejecutar.
- Acceso directo: cuando se pretende acceder a un registro en particular sin tener que accesar a todos los anteriores.
- Acceso secuencial: para acceder a un registro debemos accesar a todos los anteriores.
#### Operaciones sobre archivos
- Creación
- Actualización
	- Inserción
	- Modificación
	- Supresión
- Recuperación
	- Consulta
	- Generación de reportes
- Mantenimiento
	- Estructuración
	- Reorganización
###### Creación
- Es la *carga del archivo*, la captura de datos inicial
- Por lo general primero se asigna el espacio y luego se cargan los datos
###### Actualización
- Permite *cambiar el contenido* para tener un imagen de la realidad.
- Se puede insertar registros, modifcar los datos de los ya existentes, suprimir, borrar un registro.
###### Recuperación
- Es el acceso a un archivo con el propósito de *extraer información significativa*. Se diferencia en que la consulta puede tener menor cantidad de datos y ser más interactiva, mientras que la generación de reportes es un proceso en lotes más planificado.
- La recuperación puede ser comprensiva (todos los registros), o selectiva (recuperar algunos registros según determinados criterios).
###### Mantenimiento
- Es lo que realiza para *mejorar la eficiencia* de los programas que acceden al archivo.
- La reestructuración implica *hacer cambios estructurales*, como cambiar longitud de campos o agregar campos.
- La reorganización implica *cambiar la organización del archivo* a otro tipo.
#### Archivos Secuenciales
Es la manera básica de organizar un conjunto de registros que forman un archivo. Los registros se graban cuando se crea el archivo consecutivamente y se accesan de igual manera cuando el archivo se usa como entrada.
##### Estructura de archivos secuenciales
Los registros de un archivo secuencial quedan ordenados de acuerdo con el valor de algún campo. Se dice que este archivo es ordenado y este campo se conoce como llave de ordenamiento.
- Almacenamiento: existen 2 clases de dispositivos secundarios
	- Acceso serial (cintas magnéticas)
	- Acceso directo (discos)

---
![[Registros]]