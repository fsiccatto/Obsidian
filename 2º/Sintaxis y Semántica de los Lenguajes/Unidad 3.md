# Etapas de Análisis
![[imgs/codigo fuente.png| center]]
1. Analizar que el léxico que estamos usando sea válido, es decir, verificar que la frase está formada por palabras válidas en el lenguaje castellano (**Análisis Léxico**).
2. Lo siguiente es verificar que la frase está bien formada de acuerdo a la sintáxis del lenguaje (**Análisis Sintáctico**).
3. El último paso es el Análisis Semántico donde se define con exactitud qué significa la frase (**Análisis Semántico**).
## Análisis Léxico

> [!success] Funciones de un *scanner*
> 1. Recibir caracteres de entrada
> 2. Agruparlos según la G3 para reconocer lexemas y generar tokens
> 3. Detectar algunos significados y errores
> 	1. Identificar tokens y evaluarlos
> 4. Introducir información adicional descriptiva
> 5. Eliminar separadores innecesarios
> 6. Sustituir macros

Inicialmente el código fuente de un programa que es entregado al traductor, es un flujo de bytes sin estructura ni sentido alguno. Este flujo de bytes es entregado como input al analizador léxico (o scanner). El scanner deberá entonces estructurar y reconocer en los caracteres de entrada un flujo de código tokenizado (léxicamente válido o en su defecto encontrar errores léxicos).
![[imgs/analisis lexico.png| center]]

El primer trabajo que realiza el *scanner* es reconocer qué palabras o cadenas están presentes en la sentencia. Así individualiza las palabras “index”, “=”, “2”, “\*”, “count”, “+”, “17” y “;” a las que llamaremos **Lexemas**.

Un ***token*** es una categoría léxica en un lenguaje (un tipo de palabra válida en un lenguaje). En el ejemplo son "identifier", "equal_sign", etc.

Teniendo en cuenta que el léxico de los lenguajes de programación está definido por un G3 (expresiones regulares), y que para cada G3 es posible definir un $AFD_{minimo}$; entonces, podemos contar con un autómata para cada categoría léxica o token del lenguaje, capaz de reconocer si una palabra o cadena de entrada (lexema) pertenece o no a esa categoría (token).

El scanner, compuesto de un conjunto de AFD, tomará los lexemas, los agrupará según G3 y los evaluará para convertir el código en un flujo, no ya de palabras sin sentido, sino en un flujo de tokens (código tokenizado).

## Análisis Sintáctico
La sintaxis en los lenguajes de programación se especifica mediante gramáticas de tipo 2 (G2 o independientes del contexto). La función básica del *parser* o analizador sintáctico es utilizar los tokens suministrados por el scanner para **reconocer frases o estructuras sintácticamente válidas en un lenguaje independiente del contexto**, produciendo como resultado final los árboles de análisis sintáctico.

> [!done] Funciones de un *parser*
> 1. Recibir tokens suministrados por el scanner
> 2. Agrupar tokens
> 	1. de acuredo a producciones especificads por la G2 para reconocer frases
> 	2. determinar si son sintácticamente correctas
> 	3. establecer la estructura subyacente
> 3. Detectar errores sintácticos
> 4. Generar árboles sintácticos

![[imgs/analisis sintactico.png| center]]

Un parser (o analizador sintáctico) se puede implementar mediante un Autómata de Pila que reconozca lenguajes independientes del contexto (G2).

Para gramáticas **BNF no ambiguas** se han descubierto técnicas sencillas de análisis sintáctico que permiten construir parsers que reconocen en un tiempo lineal. Estos son los llamados **Analizadores Recursivos** -> proponen construir el árbol basándose en el reconocimiento de la cadena de entrada de <mark style="background: #FFB86CA6;">izquierda a derecha</mark>; y decidiendo en cada paso la regla gramatical que conviene elegir para continuar con la derivación.

> [!question] ¿Cómo se implementa este proceso?
> **Analizadores recursivos**
> - cada no-terminal tiene asociada una rutina de análisis creada a partir de las reglas gramaticales
> - scan de izquierda a derecha
> 
> **Estrategia de análisis**
> - DESCENDENTE (*Top-Down*)
> 	- construye el árbol desde la raíz (S) hacia las hojas
> 	- problemas con recursividad a izquierda (LL)
> - ASCENDENTE (*Bottom-Up*)
> 	- construye el árbol desde las hojas hacia la raíz (S)
> 	- se basa en encontrar una derivación por derecha (LR)

### Parser LL(1) Top-Down o Predictivos
Construyen el árbol desde la raíz hacia las hojas, determinando en cada paso que producción es más conveniente para expandir el nodo actual, basándose en el próximo token disponible en la cadena de entrada, de izquierda a derecha.

Habitualmente, un parser recursivo descendente se implementa mediante un algoritmo que tiene: 
✔ Una subrutina para cada no terminal en la gramática.
✔ Un mecanismo para solicitar el input del próximo token proporcionado por el scanner.
✔ Una rutina para consumir ese token en la medida que se encuentra una regla de producción con la que empata o matchea.

> [!error] Error Sintáctico
> Si el token proporcionado no es uno de los esperados de acuerdo a las reglas de producción de la gramática, la rutina de matcheo anunciará un error sintáctico.

Los analizadores recursivos top-down resultan más fáciles de comprender e implementar, pero no son aplicables a un gran número de gramáticas. Los obstáculos son:
- Las producciones recursivas a izquierdas, y
- Los prefijos comunes.

![[imgs/analizador por izquieda.png| center | 200]]
Si bien la cadena pertenece al lenguaje descripto por la gramática, la estrategia LL(1) se traba en el paso (3), no encuentra una regla de producción para el no terminal A que comience con b y por lo tanto no sabe cuál de las dos reglas escoger para seguir.
Se puede resolver utilizando un **retroceso**. Los reconocedores Top-Down con retroceso son más lentos y difíciles de programar.
![[imgs/analizador por izquierda con retroceso.png| center | 200]]
En definitiva, si la gramática presenta producciones recursivas a izquierda, un analizador Top-Down/LL(1) **no** puede procesarla, por lo que es deseable buscar una gramática equivalente sin recursividad a izquierda.

El segundo tipo de obstáculo que enfrentan los analizadores recursivos descendentes, son las producciones con prefijos comunes:
![[imgs/problema del retroceso.png | center | 400]]
Cuando en el input se proporciona el token d; el analizador top-down no tiene forma de predecir que regla de producción aplicar, puesto que d, es un prefijo común de dos reglas de producción diferentes. Lo mismo sucede con el token b.

### Parser LL(k)
Una solución alternativa y más eficiente a la implementación de reconocedores Top-Down con retroceso para estos casos, son los traductores **LL(k)** que proponen un análisis anticipado de **k-tokens** en la entrada antes de decidir que regla de producción aplicar.
✅ LL(1) traductores top-down con un análisis anticipado de 1 caracter 
✅ LL(k) traductores “top-down” con Un análisis anticipado de k caracteres

> [!info] Características de los analizadores LL
> Permiten el análisis descendente sin retroceso usando un subconjunto de las G2.
> - **L** = reconocimiento de la cadena de entrada de izquierda a derecha  
> - **L** = toman las derivaciones más hacia la izquierda ("Leftmost") _con sólo mirar los k tokens_ situados a continuación de donde se halla, donde si k=1 se habla de gramáticas LL(1). 
> Posibilitan la construcción de analizadores deterministas descendentes (_sólo examinan el símbolo actual de la cadena de entrada para saber qué producción aplicar_).

  Aun así, algunos problemas no se pueden resolver de forma descendente. Es decir, existen muchos lenguajes que no son LL(k), para los cuáles no existe una gramática LL que los describa.

### Parser LR(1) Bottom-Up o Desplazamiento-Reducción
Construyen el árbol desde las hojas hacia la raíz, utilizando una técnica llamada
desplazamiento-reducción (*Shift-Reduce*) que coincide con encontrar una derivación por derecha.
![[bottom-up.png | center]]
El **parser bottom-up** comienza por tomar la hoja más a la izquierda del árbol (tal como lo lee en la cadena de entrada, de izquierda a derecha) y buscar si la puede reemplazar por la parte derecha de una regla de producción en la gramática. Como no puede, sigue leyendo y agrupando los símbolos en la cadena de entrada (hojas del árbol) hasta que puede reemplazarlos por el lado derecho de una regla de producción en la gramática. El proceso de agrupar un símbolo tras otro sin hacer nada más, se llama **desplazamiento**, cuando se junta un grupo de símbolos que se puede sustituir por un no terminal a la derecha de una regla de producción se hace una **reducción**.

> [!info] Características de los analizadores LR
> - Eficiente análisis ascendente sin retroceso
> - Detectan errores sintácticos rápidamente
> - L = lee entrada *left-to-right*
> - R = aplican derivaciones *rightmost* en sentido inverso
> 	- k = número de símoblos de entrada por delante (*lookaheads*) que lee el analizador (gramática LR(k))
> - Pueden construirse para la mayoría de las G2
> - Complicados de construir

---
A continuación se ilustra comparativamente los procesos de derivación **MI** (más a la izquierda) y **MD** (más a la derecha) para expresiones aritméticas. La cadena se lee siempre de izquierda a derecha. En MI, se deriva siempre el **no terminal más a la izquierda**, mientras que en MD se deriva siempre el **no terminal más a la derecha**.
![[MD y MI.png | center | 300]]
<mark style="background: #BBFABBA6;">En cuanto hayan entrado suficientes token para detectar la parte derecha de una regla de producción, sustituirlos (reducirlos) por su parte izquierda.</mark>

## Semánticas del Lenguaje
La Semántica define el significado de las expresiones, enunciados
y unidades de un programa.
> [!info] Semánticas
> Utilidad de las semánticas
> 1. Definir "qué deben hacer" los enunciados de un lenguaje
> 2. Implementar correctamente el lenguaje
> 3. Desarrollar técnicas y herramientas de
> 	1. Análisis y optimización, depuración, verificación, etc.
> 4. Ayudar a "razonar sobre el funcionamiento" de los programas

La implementación de la semántica puede ser de dos tipos:
- **Semántica Estática**: reúne a todos aquellos aspectos semánticos de un
lenguaje que se calculan, se resuelven o se deciden en tiempo de compilación.
	- Correspondencia de la signatura de funciones
	- Accesos a variables consistentes con su declaración
	- Que identificadores y expresiones sean evaluables
	- Que el *left-side* sea asignable
	- Compatibilidad de expresiones y operadores
	- Accesibilidad de las variables según su alcance
	- Uso de identificadores únicos
- **Semántica Dinámica**: reúne a todos aquellos aspectos semánticos de un
lenguaje que se calculan, se resuelven o se deciden en tiempo de ejecución.
	- Punteros con referencias nulas
	- Valores límites de subíndices de arreglos
	- Consistencia en el pasaje de argumentos
	- Errores de lógica que cambian la semántica de un enunciado no son detectables $x:=\frac{z}{y}, \text{ ¿y == 0?}$

---

> [!attention] Especificaciones de la semántica
> Es deseable satisfacer características como:
> - **No ambigüedad**: facilitar la creación de descripciones rigurosas
> - **Demostración**: permitir la posterior demostración de propiedades de los programas escritos en el lenguaje especificado
> - **Prototipado**: posibilitar obtener prototipos ejecutables de los lenguajes que se diseñan de forma automática
> - **Modularidad**: realizar la especificación de forma incremental
> - **Reusabilidad**: facilitar la reutilización de descripciones para diferentes lenguajes
> - **Legibilidad**: ser legibles por personas con formaciones heterogéneas
> - **Flexibilidad**: adaptarse a la variedad de lenguajes existentes
> - **Experiencia**: ser capaz de describir lenguajes reales no sólo aquellos sencillos o experimentales
## Arquitecturas de Traducción
![[compilador vs interprete | center ]]