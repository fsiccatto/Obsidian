# Memorias Electrónicas
Son los dispositivos de almacenamiento de datos e instrucciones en una computadora. Llamamos sistema de memoria al conjunto de estos dispositivos y los algoritmos de hardware y/o software de control de los mismos.
Clasificación funcional de las memorias: 
1. Memoria interna: consituida por los registros internos de la CPU.
2. Memoria central: almacena programas y datos.
3. Memoria secundaria: se usa para almacenamiento de programas del sistema y grandes archivos.
Se pueden definir algunos parámetros generales aplicables a todas las memorias:
1) Unidad de almacenamiento: bit.
2) Capacidad de almacenamiento: cantitad de bits que puede almacenarse. 1Kb = 1024 bytes.
3) Tiempo de acceso (ta): es lo que tarda en leer o escribir una palabra en la memoria desde el momento que se direcciona.
4) Tipo de acceso:
	- Acceso aleatorio
	- Acceso serie
5) Tiempo de ciclo (tc): mínimo tiempo entre dos accesos sucesivos a la memoria. tc > ta.
6) Medio físico
	- Electrónicas
	- Magnéticas
	- Ópticas
7) Estabilidad
   - Volatilidad: el contenido de la memoria se pierde cuando se saca la alimentación eléctrica.
   - Almacenamiento dinámico: la información se pierde cuando el capacitor se descarga, es necesario un refresco periódico para restaurar el contenido antes que se deteriore.
   - Lectura destructiva (DRO): se pierde información al efectuar la lectura, debe acompañarse de una restauración.
## Clasificación de las Memorias Electrónicas
Las memorias electrónicas pueden considerarse como un sistema digital mixto (combinacional y secuencial) capaz de almacenar información binaria que se puede acceder (introducir o extraer información) sólo parcialmente en un momento dado.
En función del tipo de acceso, estas memorias se clasifican en:
1. **Memorias de acceso aleatorio** (*RAM*) en las que `ta` es similar para cualquier posición.
	- Memorias de lectura/escritura. Se caracterizan por tener los `ta` de lectura y escritura similares, presentan volatilidad, pierden su contenido cuando dejan de estar alimentadas.
		- Memorias estáticas (SRAM)
		- Memorias dinámicas (DRAM)
	- Memorias sólo lectura (*ROM*). Se caracterizan por tener el `ta` de escritura mucho mayor que el de lectura, no presentan volatidad, no pierden su contenido sin alimentación. Se subdividen:
		- ROM
		- PROM
		- EPROM
		- EEPROM
		- FLASH
2. **Memorias de acceso serie**
