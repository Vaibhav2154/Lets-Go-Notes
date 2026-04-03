# Variables in Go

Tags: #go #basics #variables

## Overview

Go supports multiple ways to declare variables. The `:=` short declaration is the most commonly used inside functions.

## Code Example

```go
// Full declaration with type
var age int
age = 2

// Short declaration (only inside functions)
name := "Hello"
fmt.Printf("%T", name) // prints: string

// Package-level variable
var firstname = "Michael"
```

## Declaration Methods

| Syntax | Scope | Type Inference |
|--------|-------|----------------|
| `var x int` | Anywhere | No |
| `var x = 10` | Anywhere | Yes |
| `x := 10` | Functions only | Yes |

## Scope

- Variables declared at **package level** are accessible from any function within the package.
- Variables declared inside a function are **local** to that function.

## Default Values

- Numeric: `0`
- Boolean: `false`
- String: `""`
- Pointers, slices, maps, functions, structs: `nil`

## Related Notes

- [[03 - Data Types]]
- [[05 - Naming Conventions]]
- [[06 - Constants]]
