# Struct Embedding in Go

Tags: #go #intermediate #structs #embedding #composition

## Overview

Struct embedding allows one struct to include another, **promoting** its fields and methods. It's Go's way of achieving composition over inheritance.

## Code Example

```go
type person struct {
    name string
    age  int
}

type Employee struct {
    employeeInfo person  // Named field (explicit access)
    empId        string
    salary       float64
}

func (p person) introduce() {
    fmt.Printf("Hi, I'm %s and I'm %d years old.\n", p.name, p.age)
}

func (e Employee) introduce() {
    fmt.Printf("Hi, I'm %s, ID: %s, salary: %.2f.\n",
        e.employeeInfo.name, e.empId, e.salary)
}

emp := Employee{
    employeeInfo: person{name: "John", age: 30},
    empId: "E001",
    salary: 50000,
}

// Accessing embedded struct fields
fmt.Println(emp.employeeInfo.name)  // "John"
fmt.Println(emp.employeeInfo.age)   // 30
emp.introduce()                     // calls Employee's introduce
```

## Anonymous Embedding (Promotes Fields/Methods)

```go
type Shape struct {
    Rectangle  // Anonymous embed — fields and methods promoted
}

s := Shape{Rectangle: Rectangle{length: 10, width: 9}}
fmt.Println(s.Area())           // promoted from Rectangle
fmt.Println(s.Rectangle.Area()) // explicit access
```

## Named vs Anonymous Embedding

| | Named Field | Anonymous (Embedded) |
|-|-------------|----------------------|
| Field access | `emp.employeeInfo.name` | `emp.name` (promoted) |
| Method access | `emp.employeeInfo.Intro()` | `emp.Intro()` (promoted) |
| Overriding | N/A | Define same method on outer struct |

## Related Notes

- [[33 - Structs]]
- [[34 - Methods]]
- [[35 - Interfaces]]
