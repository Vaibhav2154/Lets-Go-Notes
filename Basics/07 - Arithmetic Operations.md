# Arithmetic Operations in Go

Tags: #go #basics #arithmetic #math 

## Overview

Go supports standard arithmetic operators. It also uses the `math` package for advanced operations.

## Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `+` | Addition | `a + b` |
| `-` | Subtraction | `a - b` |
| `*` | Multiplication | `a * b` |
| `/` | Division (integer) | `a / b` |
| `%` | Remainder (modulo) | `a % b` |

## Code Example

```go
a := 10
b := 3
result = a + b  // 13
result = a - b  // 7
result = a * b  // 30
result = a / b  // 3  (integer division, truncates)
result = a % b  // 1

const p float64 = 22 / 7.0  // 3.142857...
```

## Overflow & Underflow

```go
// int64 max: 9223372036854775807
var maxnt int64 = 9223372036854775807
maxnt + 1  // overflows → wraps around to negative

// uint64 max: 18446744073709551615
var uMaxInt uint64 = 18446744073709551615
uMaxInt + 1  // overflows → wraps to 0

// Float underflow
var smallFloat float64 = 1.0e-323
smallFloat / math.MaxFloat64  // produces 0 (underflow)
```

## Key Points

- Integer division **truncates** toward zero.
- Use `float64` literals for floating-point division: `22 / 7.0`.
- Import `"math"` for `math.MaxFloat64`, `math.Sqrt`, etc.

## Related Notes

- [[03 - Data Types]]
- [[10 - Operators]]
