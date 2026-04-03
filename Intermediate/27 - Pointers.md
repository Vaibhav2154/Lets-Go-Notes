# Pointers in Go

Tags: #go #intermediate #pointers #memory

## Overview

A pointer stores the **memory address** of a value. Go supports pointers but has **no pointer arithmetic**.

## Code Example

```go
a := 10

ptr := &a       // ptr is *int, holds the address of a
ptr2 := &ptr    // ptr2 is **int, pointer to pointer

fmt.Println(ptr)   // memory address
fmt.Println(a)     // 10
fmt.Println(ptr2)  // address of ptr

// Dereference to modify the original value
func modifyValue(ptr *int) {
    *ptr++
}

modifyValue(ptr)
fmt.Println(a)  // 11
```

## Key Points

- `&variable` → gets the address (creates a pointer).
- `*pointer` → dereferences (accesses the value at the address).
- Default value of a pointer is `nil`.
- Go has **no pointer arithmetic** (unlike C/C++).
- Pointers allow functions to modify caller's variables.
- Use pointer receivers on methods when you need to modify struct fields.

## When to Use Pointers

| Situation | Use pointer? |
|-----------|-------------|
| Modify a value in a function | ✅ Yes |
| Large struct (avoid copying) | ✅ Yes |
| Nullable / optional value | ✅ Yes |
| Small value types (int, bool) | ❌ Usually not needed |

## Related Notes

- [[33 - Structs]]
- [[34 - Methods]]
