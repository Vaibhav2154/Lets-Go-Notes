# Slices in Go

Tags: #go #basics #slices #collections

## Overview

Slices are **dynamic, flexible views** into an underlying array. They are reference types.

## Creation Methods

```go
// Nil slice
var numbers []int

// Literal
n1 := []int{1, 2, 3}

// From an array
a := [5]int{11, 12, 13, 14, 15}
slice1 := a[1:4]  // [12 13 14]

// Using make
slice := make([]int, length, capacity)
```

## Common Operations

```go
// Append
slice1 = append(slice1, 3, 4, 5, 6)

// Copy
slice1Copy := make([]int, len(slice1))
copy(slice1Copy, slice1)

// Equality check (requires "slices" package)
import "slices"
if slices.Equal(slice1, slice1Copy) { ... }

// 2D slice (matrix)
matrix := make([][]int, 3)
for i := 0; i < 3; i++ {
    matrix[i] = make([]int, i+1)
}
```

## Capacity vs Length

```go
fmt.Println(len(slice1))  // number of elements
fmt.Println(cap(slice1))  // allocated capacity
```

## Key Points

- Slices share the underlying array — modifying a slice modifies the original.
- `append` may allocate a new array if capacity is exceeded.
- Slicing syntax: `slice[low:high]` (low inclusive, high exclusive).
- Use `copy()` to get an independent copy.

## Related Notes

- [[13 - Arrays]]
- [[16 - Range]]
- [[15 - Maps]]
