# Máquinas y Lenguajes
## Analizadores Léxicos (Scanner o Lexer)
1. Hacer

| Token    |                 |
| -------- | --------------- |
| `<Expr>` | `x>y`           |
| Id       | `x`             |
| Id       | `y`             |
| `<Block` | `{z=x*y; ++z;}` |
| `z=x*y`  | `<Expr>`        |
| `++z`    | `<Op>`          |

| Token       |     |
| ----------- | --- |
| `<Func Id>` |     |

## Analizadores Sintácticos (Parser)
### Árboles de análisis sintáctico
