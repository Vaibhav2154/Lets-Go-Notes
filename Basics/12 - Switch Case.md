# Switch Case in Go

Tags: #go #basics #switch #control-flow

## Overview

Go's `switch` automatically breaks after each case (no `break` needed). Use `fallthrough` to continue to the next case explicitly.

## Basic Syntax

```go
switch expression {
case value1:
    // code
case value2:
    // code
    fallthrough  // continue to next case
case value3:
    // code
default:
    // fallback
}
```

## Examples

### Simple Switch
```go
fruit := "pineapple"
switch fruit {
case "apple":
    fmt.Println("It's an apple.")
case "banana":
    fmt.Println("It's a banana.")
default:
    fmt.Println("Unknown Fruit!")
}
```

### Multiple Conditions Per Case
```go
switch day {
case "Monday", "Tuesday", "Wednesday", "Thursday", "Friday":
    fmt.Println("It's a weekday.")
case "Sunday":
    fmt.Println("It's a weekend.")
}
```

### Expressionless Switch (like if-else)
```go
switch {
case number < 10:
    fmt.Println("Less than 10")
case number >= 10 && number < 20:
    fmt.Println("Between 10 and 19")
default:
    fmt.Println("20 or more")
}
```

### Type Switch
```go
func checkType(x interface{}) {
    switch x.(type) {
    case int:
        fmt.Println("It's an integer")
    case float64:
        fmt.Println("It's a float")
    case string:
        fmt.Println("It's a string")
    default:
        fmt.Println("Unknown Type")
    }
}
```

> **Note:** Cannot use `fallthrough` in a type switch.

## Related Notes

- [[11 - If Else]]
