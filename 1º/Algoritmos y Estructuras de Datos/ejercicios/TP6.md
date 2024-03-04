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

```C
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void cargarJugada(char vector[], const char *nombre);
void llenarTesoro(char vector[]);
void llenarVector(char vector[]);
void mostrarVector(char vector[]);

void juegoComplementario(const char *nom1, const char *nom2, char vec1[], char vec2[], int *puntos1, int *puntos2);

void puntos(char tesoro[], char jugador1[], char jugador2[], const char *nom1, const char *nom2, int *puntos1, int *puntos2);

int main() {
    char nom1[50], nom2[50];
    char vec1[5] = {'0', '0', '0', '0', '0'};
    char vec2[5] = {'0', '0', '0', '0', '0'};
    char tesoro[5];
    int puntos1 = 0;
    int puntos2 = 0;

    printf("Jugador 1, introduzca su nombre:\n");
    scanf("%s", nom1);
    printf("------------------------------------------------\n");
    printf("Jugador 2, introduzca su nombre:\n");
    scanf("%s", nom2);
    printf("------------------------------------------------\n");
    llenarVector(vec1);
    llenarVector(vec2);
    cargarJugada(vec1, nom1);
    cargarJugada(vec2, nom2);
    llenarTesoro(tesoro);
    juegoComplementario(nom1, nom2, vec1, vec2, &puntos1, &puntos2);
    printf("%s: \n", nom1);
    mostrarVector(vec1);
    printf("------------------------------------------------\n");
    printf("%s: \n", nom2);
    mostrarVector(vec2);
    printf("------------------------------------------------\n\n");
    mostrarVector(tesoro);
    printf("------------------------------------------------\n");
    puntos(tesoro, vec1, vec2, nom1, nom2, &puntos1, &puntos2);
    return 0;
}

  

void cargarJugada(char vector[], const char *nombre) {
    int num, jugada = 1;
    
    do {
        printf("%s, ingresa un numero entre el 1 y el 5, para ubicar la hormiga ", nombre);
        printf("%d: ", jugada);
        scanf("%d", &num);
        if (num >= 6 || num <= 0) {
            printf("numero no valido\n");
        } else if (vector[num - 1] == '1') {
            printf("Lugar ya ocupado\n");
            num = 6;
        } else {
            vector[num - 1] = '1';
            jugada++;
        }
    } while (jugada <= 3);
}
  
void llenarTesoro(char vector[]) {
    for (int i = 0; i < 5; i++) {
        vector[i] = '-';

    }
    int num1 = rand() % 5;
    int num2;
    
    vector[num1] = 'L';
    do {
        num2 = rand() % 5;
    } while (num2 == num1);
    vector[num2] = 'A';
}

  

void llenarVector(char vector[]) {
    for (int i = 0; i < 5; i++) {
        vector[i] = '0';
    }
}

  

void mostrarVector(char vector[]) {
    for (int i = 0; i < 5; i++) {
        printf("[%c]", vector[i]);
    }
    printf("\n");
}

  

void juegoComplementario(const char *nom1, const char *nom2, char vec1[], char vec2[], int *puntos1, int *puntos2) {
    int num1 = 0;
    int num2 = 0;
    
    do {
        printf("%s: Ingresa una posicion valida para sumar puntos si es que acierta una hormiga en la posicion del enemigo\n", nom1);
        scanf("%d", &num1);
    } while (num1 <= 0 || num1 >= 6);
    do {
        printf("%s: Ingresa una posicion valida para sumar puntos si es que acierta una hormiga en la posicion del enemigo\n", nom2);
        scanf("%d", &num2);
    } while (num2 <= 0 || num2 >= 6);
    if (vec1[num2 - 1] == '1') {
        printf("%s: has acertado en tu rival\n", nom2);
        *puntos2 = 2 + *puntos2;
    }
    if (vec2[num1 - 1] == '1') {
        printf("%s: has acertado en tu rival\n", nom1);
        *puntos1 = 2 + *puntos1;
    }
}

void puntos(char tesoro[], char jugador1[], char jugador2[], const char *nom1, const char *nom2, int *puntos1, int *puntos2) {
    for (int i = 0; i < 5; i++) {
        if (tesoro[i] == 'L') {
            if (jugador1[i] == '1' && jugador2[i] == '1') {
                *puntos1 = 2 + *puntos1;
                *puntos2 = 2 + *puntos2;
            } else if (jugador1[i] == '1') {
                *puntos1 = 6 + *puntos1;
            } else if (jugador2[i] == '1') {
                *puntos2 = 6 + *puntos2;
            }
        }
        if (tesoro[i] == 'A') {
            if (jugador1[i] == '1' && jugador2[i] == '1') {
                *puntos1 = 3 + *puntos1;
                *puntos2 = 3 + *puntos2;
            } else if (jugador1[i] == '1') {
                *puntos1 = 5 + *puntos1;
            } else if (jugador2[i] == '1') {
                *puntos2 = 5 + *puntos2;
            }
        }
    }
    printf("%s: tuviste %d puntos\n", nom1, *puntos1);
    printf("%s: tuviste %d puntos\n", nom2, *puntos2);
}
```

#### Ejercicio 2
Agregue alguna “variante” al juego anterior (nuevas reglas, dimensión de la matriz, valores de la matriz, configuración del juego, puntaje, niveles, información adicional para el jugador 2) para particularizarlo.