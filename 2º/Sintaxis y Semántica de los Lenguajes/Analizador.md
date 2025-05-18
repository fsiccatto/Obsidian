## 📌 **Resumen de la Tarea**

Tenés que:

1. **Diseñar la gramática EBNF** que ya te fue dada.
    
2. Usar **ANTLR4** para generar:
    
    - el **léxico** (tokens)
        
    - el **parser** (análisis sintáctico)
        
3. Crear un **programa en JavaScript** que:
    
    - lea un archivo `input.txt`
        
    - use el parser generado
        
    - genere un **árbol de sintaxis**
        
    - imprima una **tabla de tokens**
        
    - **interprete el código** y lo ejecute como si fuera JavaScript
    
---
## 🧠 **EBNF Dada (Resumen estructurado)**

```ebnf
<programa> ::= <funcion>+

<funcion> ::= "funcion" <identificador> "(" [<parametros>] ")" "{" [<instrucciones>]* "}"

<parametros> ::= <identificador> ("," <identificador>)*

<instrucciones> ::= <leer> | <escribir> | <asignacion>

<leer> ::= "leer" "(" <identificador> ")"

<escribir> ::= "escribir" "(" <expresion> ")"

<asignacion> ::= <identificador> "=" <expresion> ";"

<expresion> ::= <numero> | <cadena> | <identificador>

<identificador> ::= [a-zA-Z] [a-zA-Z0-9]*

<numero> ::= [0-9]+

<cadena> ::= "\"" [^"]* "\""
```

---
## 🎯 **Objetivos concretos del analizador**
1. **Análisis léxico y sintáctico**
    
    - Detectar errores (por línea y tipo)
        
    - Usar ANTLR para generar el lexer y parser
        
2. **Tabla de tokens (lexemas)**
    
    - Mostrar: tipo de token, valor y línea
        
3. **Árbol sintáctico**
    
    - Representación visual (texto o gráfico)
        
4. **Interpretación a JavaScript**
    
    - Traducir el lenguaje dado al equivalente en JS
        
    - Ejecutarlo si querés (simularlo con `eval`, por ejemplo)
        

---

## 🛠️ ¿Qué necesitás hacer?

### 1. **Crear el archivo de gramática ANTLR4**

Será algo como `MiLenguaje.g4`. Por ejemplo:

```antlr
grammar MiLenguaje;

programa: funcion+ ;
funcion: 'funcion' ID '(' parametros? ')' '{' instrucciones* '}' ;

parametros: ID (',' ID)* ;
instrucciones: leer | escribir | asignacion ;

leer: 'leer' '(' ID ')' ';' ;
escribir: 'escribir' '(' expresion ')' ';' ;
asignacion: ID '=' expresion ';' ;

expresion: NUMERO | CADENA | ID ;

ID: [a-zA-Z][a-zA-Z0-9]* ;
NUMERO: [0-9]+ ;
CADENA: '"' (~["\r\n])* '"' ;

WS: [ \t\r\n]+ -> skip ;
```

Este sería tu punto de partida para generar el lexer y el parser.

---

### 2. **Generar código con ANTLR**

Con Node.js y ANTLR, vas a usar algo como:

```bash
antlr4 -Dlanguage=JavaScript MiLenguaje.g4
```

Eso genera los archivos `.js` necesarios.

---

### 3. **Leer `input.txt` y analizar**

Usás los archivos generados para leer el código fuente y:

- mostrar tokens
    
- construir el árbol
    
- traducirlo a JS
    

---

### 4. **Interpretar**

Vas a escribir un **visitor o listener** en JavaScript que:

- convierta instrucciones del lenguaje a código JavaScript
    
- las ejecute si querés
    

---
