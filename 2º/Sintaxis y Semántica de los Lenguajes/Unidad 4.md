# Compiladores e Intérpretes
![[compilador vs interprete | center ]]
Diseñar un lenguaje de programación implica definir su sintaxis y su semántica. Respecto de la **sintaxis** es necesario definir su alfabeto, su léxico (conjunto de palabras válidas) y las reglas de buena formación de sentencias o frases en el lenguaje. 

El **léxico** de los lenguajes de programación puede ser definido por Gramáticas Regulares (G3 o ER) y las reglas de buena formación de sentencias o frases pueden ser definidas mediante Gramáticas Independientes del Contexto (G2, BNF o EBNF). 

Luego, para **ejecutar** un programa (escrito en un lenguaje de alto nivel) en un ordenador, se necesita previamente traducirlo a código binario. Esta tarea la realiza un **Traductor** que toma el código fuente como entrada y produce código binario en su salida. 

La primera tarea que realiza el traductor, es analizar el código fuente para reconocer si las palabras y frases están correctamente escritas en el lenguaje de partida. Para ello se emplea un conjunto de **autómatas**: de estados finitos para el léxico (AEF) y de pila para las sentencias, bloques y estructuras (AP). Estos autómatas son en definitiva algoritmos que integran el traductor en sus fases de reconocimiento y análisis de código.

![[proceso de traduccion.png | center]]

## Etapas
1. **Análisis Léxico** (*Scanner*)
	Se ocupa de agrupar esta serie secuencial de caracteres en sus constituyentes elementales: identificadores, espacios en blanco, palabras clave o reservadas, delimitadores, comentarios, etc.
	
	Estos constituyentes elementales se llaman elementos o componentes léxicos (**Lexemas**) y a su categorización en una categoría de elementos específicos se les llama **Tokens**.
	
	Token -> Es la unidad de programa más pequeña a la que puede asociarse un significado.

	Dado que todo componente léxico en un lenguaje, puede ser descripto por una **G3**, o lo que es equivalente, dado que los tokens se especifican usando expresiones regulares, la implementación de un revisor o analizador léxico (Scanner) dentro de un compilador se hace a través de los Autómatas de Estado Finito (AEF).
	
2. **Análisis Sintáctico** (*Parser*)
	Se identifican las estructuras sintácticas del programa: enunciados, declaraciones, expresiones, etc.; y se verifica que sean válidas.

	Dado que las estructuras sintácticas en un lenguaje pueden ser descriptas por **G2** (Gramáticas Independientes del Contexto), la implementación de un analizador sintáctico (o Parser) dentro de un compilador se hace a través de los Autómatas de Pila (AP).

	Así el resultado de la etapa de análisis sintáctico son los árboles de sintaxis concreta, correspondientes a ese programa.

3. **Análisis Semántico**
	- Semántica estática -> puede ser verificada en tiempo de compilación
	- Semática dinámica -> son verificadas en tiempo de ejecución del programa

	El proceso de análisis sintáctico alterna con el análisis semántico. Primero, el analizador sintáctico identifica una serie de elementos léxicos que forman una unidad sintáctica, como una expresión, un enunciado, llamada de subprograma o declaración. Se llama entonces a un analizador semántico que procese esta unidad, para ir generando entonces la traducción de código, desde el código fuente al objeto.

	El analizador semántico, es el puente entre las partes de **Análisis** (Reconocimiento de Código Fuente) y **Síntesis** (Generación de Código Objeto) de la traducción. 
	
	En la etapa de Análisis Semántico, ocurren también otras tareas complementarias importantes como el mantenimiento de la tabla de símbolos, la mayor parte de la detección de errores, la expansión de macros, etc. que veremos luego en detalle.
	
	 Por lo común, el analizador sintáctico y el semántico se comunican usando una pila. El analizador sintáctico introduce en la pila los diversos elementos de la unidad sintáctica hallada, y el analizador semántico los recupera y los procesa.

4. **Generación de Código**
	El código objeto es ya una versión del programa en código de máquina, pero aún no es ejecutable porque falta su enlace con librerías dinámicas u otros bloques de código. Recién cuando todo el programa se enlaza y se carga en memoria estará disponible para su ejecución.
### Compilador Nativo


