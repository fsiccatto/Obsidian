Está integrada por los siguientes componentes:
1. Decodificador de instrucciones: es un sistema combinacional. Un deco de 4:16, que se utiliza para determinar qué instrucción contiene el IR. Por lo tanto, sus entradas serán IR12 a IR15.
2. Secuenciador: es un sistema secuencial. Consta de: 
	- 2 biestables para definir los estados RUN (biestable SR) y STATE (biestable D)
	- 1 biestable relacionado con E/S
	- 1 biestable para tareas relacionadas con los pulsadores EXA y DEP
	- 1 reloj externo de 8MHz
3. Lógica de Control: sistema combinacional que consiste en un conjunto de compuertas que generan las señales de control.
![[Unidad de control cableada.png|500]]
