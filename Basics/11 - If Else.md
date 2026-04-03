# If / Else in Go

Tags: #go #basics #conditionals #if-else

## Overview

Go's `if/else` works similarly to other languages but does **not** require parentheses around the condition.

## Syntax

```go
if condition {
    // block
} else if condition {
    // block
} else {
    // block
}
```

## Code Example

```go
score := 95

if score >= 90 {
    fmt.Println("Grade A")
} else if score >= 80 {
    fmt.Println("Grade B")
} else if score >= 70 {
    fmt.Println("Grade C")
} else {
    fmt.Println("Grade D")
}
```

## Logical Operators in Conditions

```go
// OR
if 10%2 == 0 || 6%2 == 0 {
    fmt.Println("Either 10 or 6 are even.")
}

// AND
if 10%2 == 0 && 6%2 == 0 {
    fmt.Println("Both 10 and 6 are even.")
}
```

## Nested If

```go
if num%2 == 0 {
    if num%3 == 0 {
        fmt.Println("Divisible by both 2 and 3.")
    }
}
```

## Key Points

- No parentheses needed around the condition.
- Curly braces `{}` are **mandatory**.
- `if` can include an initialization statement: `if x := compute(); x > 0 { ... }`.

## Related Notes

- [[10 - Operators]]
- [[12 - Switch Case]]
