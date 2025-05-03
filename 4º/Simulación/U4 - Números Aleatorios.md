# Generación de Números pseudoaleatorios
## Introducción

> [!info] Número aleatorio
> Un número aleatorio es un número obtenido al azar. Tiene la misma probabilidad de ser elegido y la elección de un número no depende de la elección de otro.

Los números aleatorios permiten a los modelos matemáticos representar la realidad.
En general cuando se requiere que determinados datos sean impredecibles se utilizan números aleatorios.

> [!abstract]  Números aleatorios
> Los números aleatorios son la base esencial de la simulación, ya que proporcionan la **variabilidad** necesaria para modelar situaciones reales y generar resultados diversos.
> La **calidad de los resultados** de una simulación depende en gran medida de la calidad de los números aleatorios generados. La precisión y la fiabilidad de los modelos simulados se ven afectadas por la aleatoriedad introducida mediante estos números.

## Definición de números pseudoaleatorios
Los **números pseudoaleatorios** son generados por medio de una **función determinista**, no aleatoria y aparentan ser aleatorios. Estos números pseudoaleatorios se generan a partir de un valor inicial aplicando iterativamente la función.

Tienen que tener las siguientes características:
- Que sean uniformemente distribuidos
- Estadísticamente independientes
- Reproducibles
- Periodo largo
- Generados de manera rápida
- Que no requiera gran capacidad de almacenamiento

## Usos y aplicaciones de números aleatorios
Se puede sintetizar alguna de las aplicaciones de números pseudoaleatorios para:
- Simular las entradas de aquellas variables aleatorias (no determinísticas).
- Juegos o teoría de decisiones.
- Cálculo numérico (por ejemplo en la resolución de integrales).
- Teoría del muestreo (aquellos casos en los que sea demasiado costoso realizar la muestra).
- Programación (generación de entradas para realizar las pruebas de los algoritmos y programas).
- Generadores de números aleatorios en lenguaje C, C++, Delphi o Java, utilizan métodos congruenciales. lineales (como se verá a continuación).
- Muestreo: con el fin de seleccionar una submuestra de una población.
- Programación: la generación de valores aleatorios puede ser útil para poner a prueba la efectividad de un algoritmo. También son útiles en criptología.

## Generación de números pseudoaleatorios

