# Methods in Go

Tags: #go #intermediate #methods #receivers #oop

## Overview

Methods are functions with a **receiver** argument. A receiver binds the method to a specific type.

## Syntax

```go
// Value receiver (receives a copy)
func (r Rectangle) Area() float64 {
    return r.length * r.width
}

// Pointer receiver (modifies the original)
func (r *Rectangle) Scale(factor float64) {
    r.length *= factor
    r.width *= factor
}
```

## Code Example

```go
type Rectangle struct {
    length float64
    width  float64
}

rect := Rectangle{length: 10, width: 9}
area := rect.Area()          // 90
rect.Scale(2)                // modifies rect in place
area = rect.Area()           // 360

// Methods on custom types
type MyInt int

func (m MyInt) IsPositive() bool {
    return m > 0
}

func (MyInt) welcomeMessage() string {  // no receiver variable needed
    return "Welcome to MyInt Type"
}

num := MyInt(-5)
fmt.Println(num.IsPositive())    // false
fmt.Println(num.welcomeMessage()) // "Welcome to MyInt Type"
```

## Value vs Pointer Receiver

| | Value Receiver | Pointer Receiver |
|-|----------------|-----------------|
| Modifies original | ❌ No (copy) | ✅ Yes |
| Can call on non-pointer | ✅ Yes | ✅ Yes (auto-deref) |
| Used when | Read-only ops | Mutation needed |

## Related Notes

- [[33 - Structs]]
- [[35 - Interfaces]]
- [[27 - Pointers]]
