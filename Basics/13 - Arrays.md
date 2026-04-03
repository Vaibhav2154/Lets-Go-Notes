# Arrays in Go

Tags: #go #basics #arrays #collections

## Overview

Arrays in Go have a **fixed size** determined at compile time. They are value types — assigning an array copies it.

## Syntax

```go
var arrayName [size]elementType          // zero-valued
arrayName := [size]elementType{...}     // initialized
```

## Code Example

```go
// Zero-valued array
var numbers [5]int       // [0 0 0 0 0]
numbers[4] = 20          // set last element

// Initialized array
arr := [5]int{1, 2, 3, 4, 100}

// Copy (value semantics)
copied := arr
copied[0] = 5
fmt.Println("Original:", arr)   // unchanged
fmt.Println("Copied:", copied)  // modified

// Iteration
for i := 0; i < len(arr); i++ {
    fmt.Println(i, arr[i])
}
for idx, val := range arr {
    fmt.Println(idx, val)
}
```

## Pointer to Array (Avoid Copy)

```go
originalArray := [3]int{1, 2, 3}
var copiedArray *[3]int
copiedArray = &originalArray
copiedArray[0] = 100  // modifies the original

fmt.Println(originalArray)   // [100 2 3]
```

## Key Points

- Size is part of the type: `[3]int` ≠ `[5]int`.
- Use `len(arr)` to get the length.
- Prefer **slices** over arrays for most use cases.

## Related Notes

- [[14 - Slices]]
- [[16 - Range]]
