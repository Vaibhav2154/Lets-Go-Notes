# Structs in Go

Tags: #go #intermediate #structs #oop #types

## Overview

Structs are composite types that group together fields of different types. They are the primary way to model data in Go.

## Code Example

```go
// Define at package level
type Person struct {
    firstName string
    lastName  string
    age       int
    address   Address
    Phone                  // embedded struct (anonymous field)
}

type Address struct {
    city    string
    country string
}

type Phone struct {
    cell     string
    provider string
}

// Value receiver method
func (p Person) fullName() string {
    return p.firstName + " " + p.lastName
}

// Pointer receiver method (modifies the struct)
func (p *Person) incrAge() {
    p.age++
}
```

## Creating a Struct

```go
p := Person{
    firstName: "John",
    lastName:  "Doe",
    age:       30,
    address:   Address{city: "Mysuru", country: "India"},
    Phone:     Phone{cell: "9900450852", provider: "JIO"},
}

fmt.Println(p.fullName())
p.incrAge()
fmt.Println(p.age)  // 31
```

## Anonymous Struct

```go
user := struct {
    username string
    email    string
}{
    username: "john",
    email:    "john@example.com",
}
```

## Key Points

- Fields starting with **uppercase** are exported (accessible outside package).
- Structs are **value types** — assigning copies the entire struct.
- Use pointer receiver `*T` to modify the struct in a method.
- Anonymous fields allow **struct embedding** (promotes fields/methods).

## Related Notes

- [[34 - Methods]]
- [[35 - Interfaces]]
- [[36 - Struct Embedding]]
- [[27 - Pointers]]
