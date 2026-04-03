# Number Parsing in Go

Tags: #go #intermediate #strconv #parsing #numbers

## Overview

The `strconv` package provides functions to convert between strings and numeric types.

## Code Example

```go
import "strconv"

// String → int
num, err := strconv.Atoi("12345")       // int

// String → int64 (base 10, 32-bit)
n, err := strconv.ParseInt("12345", 10, 32)

// String → float64
f, err := strconv.ParseFloat("3.14", 64)
fmt.Printf("%.2f\n", f)                // "3.14"

// Binary string → decimal
decimal, err := strconv.ParseInt("1010", 2, 64)  // 10

// Hex string → decimal
hex, err := strconv.ParseInt("FF", 16, 64)         // 255

// int → string
s := strconv.Itoa(42)                  // "42"
```

## `ParseInt(s, base, bitSize)` Parameters

| Parameter | Description |
|-----------|-------------|
| `s` | Input string |
| `base` | Number base: 2=binary, 8=octal, 10=decimal, 16=hex |
| `bitSize` | Bit size of result: 0, 8, 16, 32, or 64 |

## Key Points

- Always check `err != nil` after parsing — invalid strings return an error.
- `strconv.Atoi` is shorthand for `strconv.ParseInt(s, 10, 0)`.
- `strconv.FormatInt(n, base)` converts an integer to a string in a given base.

## Related Notes

- [[03 - Data Types (Basics)]]
- [[31 - Type Conversions]]
