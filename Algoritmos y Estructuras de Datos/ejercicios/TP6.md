#### Ejercicio 1
Realizar un juego que consiste en que cada jugador ubica 3 hormigas (cada uno) en su vector de 5 posiciones. Se cuenta con:
- Nom1: CADENA //nombre jugador 1
- Nom2: CADENA //nombre jugador 2 
- Vec1\[5]: ENTERO //las hormigas del jugador 1 se indican con 1 y las posiciones vacías con 0.
- Vec2\[5]: ENTERO //las hormigas del jugador 2 se indican con 1 y las posiciones vacías con 0.  
Además se cuenta con un vector Tesoros\[5] que se completa en forma aleatoria indicando: 
- "A": indica terrón de azúcar. Solo hay uno en el vector. 
- "L": indica bombón con licor. Solo hay uno en el vector. 
La jugada consiste en ver los datos de los vectores y decidir considerando las posiciones de las hormigas de ambos jugadores: 
- si ambas hormigas se encuentran en la misma posición que un terrón de azúcar, lo comparten y cada jugador suma 3 puntos. 
- si solo una de las hormigas se encuentra en la misma posición que un terrón de azúcar, se lo come y ese jugador suma 5 puntos. 
- si ambas hormigas se encuentran en la misma posición que un bombón con licor, lo comparten, se emborrachan y cada jugador suma 2 puntos. 
- si solo una hormiga se encuentra en la misma posición que un bombón con licor, se lo come, se emborracha, se duerme y ese jugador suma 6 puntos. 
- en el caso de que la/s hormiga/s no encuentre nada en la misma posición del vector Tesoros, no ocurre nada.

```
PROGRAMA juegoHormigas
VAR nom1, nom2: CADENA
	vec1[5], vec[2], terron[5]: ENTERO
	INICIO
		
```

#### Ejercicio 2
Agregue alguna “variante” al juego anterior (nuevas reglas, dimensión de la matriz, valores de la matriz, configuración del juego, puntaje, niveles, información adicional para el jugador 2) para particularizarlo.
