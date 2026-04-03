# Type Conversions in Go

Tags: #go #intermediate #type-conversion #casting

## Overview

Go requires **explicit type conversions** — there is no implicit casting. The syntax is `Type(value)`.

## Code Example

```go
var a int = 32
b := int32(a)      // int → int32
c := float64(b)    // int32 → float64

e := 3.14
f := int(e)        // float64 → int  (truncates, not rounds) → 3

// String ↔ []byte
g := "Hello @ こんにちは 🧑 привет"
var h []byte
h = []byte(g)      // string → []byte (UTF-8 bytes)

i := []byte{255, 120, 72}
j := string(i)     // []byte → string
```

## Common Conversions

| From | To | Syntax |
|------|----|--------|
| `int` | `float64` | `float64(x)` |
| `float64` | `int` | `int(x)` (truncates) |
| `int` | `string` | `strconv.Itoa(x)` or `string(rune(x))` |
| `string` | `int` | `strconv.Atoi(x)` |
| `string` | `[]byte` | `[]byte(x)` |
| `[]byte` | `string` | `string(x)` |

> **Note:** `string(65)` gives `"A"` (rune conversion), NOT `"65"`. Use `strconv.Itoa(65)` for numeric string.

## Key Points

- Numeric conversion between compatible types is safe.
- Float → int truncates toward zero, not rounding.
- String ↔ `[]byte` conversions make a copy of the data.

## Related Notes

- [[12 - Number Parsing]]
- [[28 - Strings and Runes]]
