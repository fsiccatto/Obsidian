# Máquinas y Lenguajes
## Analizadores Léxicos (Scanner o Lexer)
1. 

| Lexema | Token |
|--------|--------|
| if | KEYWORD |
| ( | LPAREN |
| x | ID |
| > | GT |
| y | ID |
| ) | RPAREN |
| { | LBRACE |
| z | ID |
| = | ASSIGN |
| x | ID |
| * | MUL |
| y | ID |
| ; | SEMICOLON |
| ++ | INCREMENT |
| z | ID |
| ; | SEMICOLON |
| } | RBRACE |

| Lexema | Token     |
| ------ | --------- |
| int    | KEYWORD   |
| main   | KEYWORD   |
| (      | LPAREN    |
| )      | RPAREN    |
| {      | LBRACE    |
| int    | KEYWORD   |
| numero | ID        |
| =      | ASSIGN    |
| 10     | NUMBER    |
| ;      | SEMICOLON |
| float  | KEYWORD   |
| valor  | ID        |
| ;      | SEMICOLON |
| }      | RBRACE    |
## Analizadores Sintácticos (Parser)
### Árboles de análisis sintáctico
2. 

| Lexema | Token |
|--------|--------|
| for | KEYWORD |
| ( | LPAREN |
| i | ID |
| = | ASSIGN |
| 1 | NUMBER |
| ; | SEMICOLON |
| i | ID |
| <= | LE |
| n | ID |
| ; | SEMICOLON |
| i | ID |
| ++ | INCREMENT |
| ) | RPAREN |
| { | LBRACE |
| sum | ID |
| + | PLUS |
| = | ASSIGN |
| i | ID |
| ; | SEMICOLON |
| } | RBRACE |

