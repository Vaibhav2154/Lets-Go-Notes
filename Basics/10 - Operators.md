# Operators in Go

Tags: #go #basics #operators

## Overview

Go operators are similar to other C-family languages.

## Logical Operators

| Operator | Meaning |
|----------|---------|
| `!` | Logical NOT |
| `\|\|` | Logical OR |
| `&&` | Logical AND |

## Bitwise Operators

| Operator | Meaning |
|----------|---------|
| `&` | Bitwise AND |
| `\|` | Bitwise OR |
| `^` | Bitwise XOR |
| `&^` | Bitwise AND NOT (bit clear) |
| `<<` | Left shift |
| `>>` | Right shift |

## Comparison Operators

| Operator | Meaning |
|----------|---------|
| `==` | Equal |
| `!=` | Not equal |
| `<` | Less than |
| `<=` | Less than or equal |
| `>` | Greater than |
| `>=` | Greater than or equal |

## Key Points

- Go does **not** have ternary operator (`?:`).
- `^` is XOR between two values, but also **unary bitwise complement** (`^x`).
- Comparison operators return `bool`.

## Related Notes

- [[07 - Arithmetic Operations]]
- [[11 - If Else]]
