# Autómatas
## Teoría de autómatas
Un autómata es una máquina **abstracta** (es decir un modelo que simula el comportamiento de una máquina real) que se utiliza para procesar información.
- La información se codifica en cadenas de símbolos
- Procesan cadenas de **entrada** y producen cadenas de **salida**
- Reciben símbolos de entrada **secuencialmente**
- El símbolo de salida en un instante dado depende de:
	- el último símbolo de entrada
	- la secuencia o cadena que ha recibido hasta ese instante
	- el **estado** en que se encuentra
- En un instante dado sólo pueden estar en un estado
- Formas de descripción: *gráfica matricial funcional*
La importancia del uso de los autómatas en la lingüistica computacional, radica en que este tipo de máquinas abstractas puede ser utilizada para implementar diversas tareas, tales cómo traducir una cadena de entrada en otra de salida o reconocer si una cadena pertenece o no a un lenguaje. Además, el comportamiento de estos modelos abstractos puede ser fácilmente descripto por un algoritmo, por lo que es muy fácil programar autómatas para incorporarlos a un compilador (o traductor).
## Autómatas traductores
Traducen una cadena de entrada en otra cadena de salida. Para esto, trabajan con **dos alfabetos**, que pueden o no ser iguales. Un **alfabeto de entrada** al cual pertenecen los símbolos de la cinta de entrada a la máquina; y un **alfabeto de salida** al cuál pertenecen los símbolos del patrón de salida que produce la máquina abstracta en función de lo que lee en la cinta de entrada.