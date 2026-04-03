# Formatting Verbs in Go

Tags: #go #intermediate #fmt #formatting #printf

## Overview

`fmt.Printf` uses **verbs** (format specifiers) to control how values are printed.

## General Verbs

| Verb | Description |
|------|-------------|
| `%v` | Default format |
| `%#v` | Go-syntax representation |
| `%T` | Type of the value |
| `%%` | Literal `%` sign |

## Integer Verbs

| Verb | Output |
|------|--------|
| `%b` | Base 2 (binary) |
| `%d` | Base 10 (decimal) |
| `%+d` | Always show sign |
| `%o` | Base 8 (octal) |
| `%O` | Base 8 with `0o` prefix |
| `%x` | Base 16, lowercase hex |
| `%X` | Base 16, uppercase hex |
| `%#x` | Hex with `0x` prefix |
| `%4d` | Width 4, right-justified |
| `%-4d` | Width 4, left-justified |
| `%04d` | Width 4, zero-padded |

## String Verbs

| Verb | Output |
|------|--------|
| `%s` | Plain string |
| `%q` | Double-quoted string |
| `%8s` | Width 8, right-justified |
| `%-8s` | Width 8, left-justified |
| `%x` | Hex dump of bytes |

## Float Verbs

| Verb | Output |
|------|--------|
| `%e` | Scientific notation |
| `%f` | Decimal, no exponent |
| `%.2f` | Precision 2 |
| `%6.2f` | Width 6, precision 2 |
| `%g` | Shortest representation |

## Boolean Verbs

| Verb | Output |
|------|--------|
| `%t` | `true` or `false` |

## Code Example

```go
flt := 9180000.00
fmt.Printf("%e\n", flt)    // 9.180000e+06
fmt.Printf("%f\n", flt)    // 9180000.000000
fmt.Printf("%.2f\n", flt)  // 9180000.00

t := true
fmt.Printf("%t\n", t)      // true
fmt.Printf("%v\n", t)      // true
```

## Related Notes

- [[03 - fmt Package]]
- [[05 - String Formatting]]
