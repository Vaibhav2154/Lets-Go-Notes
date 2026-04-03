# Interfaces in Go

Tags: #go #intermediate #interfaces #polymorphism #duck-typing

## Overview

An interface defines a **set of method signatures**. Any type that implements all methods implicitly satisfies the interface — there is no `implements` keyword.

## Code Example

```go
type geometry interface {
    area() float64
    perimi() float64
}

type Rectangle1 struct { width, height float64 }
type Circle struct { radius float64 }

func (r Rectangle1) area() float64   { return r.height * r.width }
func (r Rectangle1) perimi() float64 { return 2 * (r.height + r.width) }
func (c Circle) area() float64       { return math.Pi * c.radius * c.radius }
func (c Circle) perimi() float64     { return 2 * math.Pi * c.radius }

// Function accepting any geometry
func measure(g geometry) {
    fmt.Println(g.area())
    fmt.Println(g.perimi())
}

r := Rectangle1{height: 10, width: 20}
c := Circle{radius: 5}
measure(r)  // works
measure(c)  // works
```

## Empty Interface

```go
// interface{} (or any in Go 1.18+) accepts any type
func myPrinter(i ...interface{}) {
    for _, v := range i {
        fmt.Printf("%v : %T\n", v, v)
    }
}

myPrinter(1, "Hii", false)
```

## Key Points

- Go interfaces are **implicitly satisfied** — no explicit declaration needed.
- The empty interface `interface{}` (alias `any`) holds any value.
- Use type assertions to extract the concrete type: `val, ok := g.(Rectangle1)`.
- Use type switches for multiple type checks: `switch x.(type) { case int: ... }`.
- Interface values are `nil` if both the type and pointer are nil.

## Related Notes

- [[33 - Structs]]
- [[34 - Methods]]
- [[36 - Struct Embedding]]
- [[12 - Switch Case (Basics)]]
