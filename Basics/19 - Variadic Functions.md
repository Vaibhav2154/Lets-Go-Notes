# Variadic Functions in Go

Tags: #go #basics #functions #variadic

## Overview

Variadic functions accept a **variable number of arguments** using the `...` (ellipsis) syntax.

## Syntax

```go
func functionName(param1 type1, params ...typeN) returnType {
    // params is a slice inside the function
}
```

> **Rule:** The variadic parameter must be the **last parameter**.

## Code Example

```go
func sum(returnString string, nums ...int) (string, int) {
    total := 0
    for _, num := range nums {
        total += num
    }
    return returnString, total
}

// Calling with individual args
statement, total := sum("Sum is", 1, 2, 3, 4, 5)

// Passing a slice
numbers := []int{1, 2, 3, 4, 5, 6}
statement, total := sum("Sum of slice", numbers...)  // unpack with ...
```

## Key Points

- Inside the function, the variadic parameter behaves like a **slice**.
- To pass a slice as variadic argument, use `slice...` to unpack it.
- `fmt.Println`, `fmt.Printf` etc. use variadic parameters.

## Related Notes

- [[17 - Functions]]
- [[18 - Multiple Return Values]]
