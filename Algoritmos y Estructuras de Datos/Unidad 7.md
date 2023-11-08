# Recursión
La recursión es un método, un recurso que permite definir un objetivo en términos de sí mismo. Un subprograma que en lugar de llamar a otro subprograma, se llama a sí mismo se dice que es *Recursivo*.
Todo aquello que pueda resolverse con una estructura repetitiva se puede plantear con una recursión.
- Caracterísiticas
	- Se deben considerar dos componentes:
		- Una o varias condiciones de salida
		- Una o varias partes recursivas
	- Cuando se ejecuta el subprograma recursivo en algún momento se debe pasar por la/s condición/es de salida ya que sino quedaría en un lazo infinito.
	- Siempre se debe detectar la/s condición/es de salida.
- Definición de la recursividad
	- Hay dos etapas en el proceso de definición recurrente.
		- Identificar el **estado base** o condición/es de salida del proceso recursivo, o sea la solución sin aplicar recurrencia.
		- Encontrar una **relación recurrente** que exprese el modo de obtener un conjunto de valores genéricos representativos del proceso.

---
![[ejercicios/Recursión]]