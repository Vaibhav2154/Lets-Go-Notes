# Multiple Return Values in Go

Tags: #go #basics #functions #error-handling #multiple-return

## Overview

Go functions can return **multiple values**. This is most commonly used for returning a result alongside an error.

## Syntax

```go
func functionName(p1 type1) (returnType1, returnType2) {
    return val1, val2
}
```

## Named Return Values

```go
// Named returns are automatically returned (naked return)
func divide(a, b int) (q int, r int) {
    q = a / b
    r = a % b
    return  // returns q and r implicitly
}
```

## Error Handling Pattern

```go
func compare(a, b int) (string, error) {
    if a > b {
        return "A is greater", nil
    } else if b > a {
        return "B is greater", nil
    } else {
        return "", errors.New("Unable to compare")
    }
}

result, err := compare(3, 2)
if err != nil {
    fmt.Println(err)
} else {
    fmt.Println(result)
}
```

## Key Points

- Use `errors.New("message")` to create a simple error.
- Use `fmt.Errorf("format %v", val)` to create a formatted error.
- Convention: **last return value is the error**.
- Use `_` to discard unwanted return values: `result, _ := divide(10, 3)`.

## Related Notes

- [[17 - Functions]]
- [[19 - Variadic Functions]]
