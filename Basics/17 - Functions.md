# Functions in Go

Tags: #go #basics #functions #first-class

## Overview

Functions are **first-class citizens** in Go — they can be assigned to variables, passed as arguments, and returned from other functions.

## Syntax

```go
func functionName(param1 type1, param2 type2) returnType {
    // body
    return value
}
```

## Code Example

```go
func add(a, b int) int {
    return a + b
}

// Anonymous function (closure)
greet := func() {
    fmt.Println("Hello from anonymous function")
}
greet()

// Assign function to variable
operation := add
result := operation(2, 3)

// Passing function as argument
func applyOperation(x int, y int, op func(int, int) int) int {
    return op(x, y)
}
result = applyOperation(5, 3, add)

// Returning a function
func createMultiplier(factor int) func(int) int {
    return func(i int) int {
        return i * factor
    }
}
multiplyBy2 := createMultiplier(2)
fmt.Println(multiplyBy2(3))  // 6
```

## Key Points

- Functions starting with **uppercase** are exported (public).
- When two or more consecutive parameters share the same type, the type can be written once: `func add(a, b int)`.

## Related Notes

- [[18 - Multiple Return Values]]
- [[19 - Variadic Functions]]
- [[01 - Closures (Intermediate)]]
