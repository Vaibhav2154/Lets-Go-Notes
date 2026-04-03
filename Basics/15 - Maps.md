# Maps in Go

Tags: #go #basics #maps #collections

## Overview

Maps are Go's built-in key-value data structure (like a dictionary or hash map). They are reference types.

## Creation

```go
// Using make
map2 := make(map[string]int)

// Using a map literal
map1 := map[string]int{
    "1": 3,
    "2": 4,
}
```

## Common Operations

```go
// Set
map2["key"] = 1

// Get (safe check)
value, ok := map1["key"]
if ok {
    fmt.Println("Found:", value)
}

// Delete
delete(map1, "2")

// Clear all entries
clear(map2)

// Iteration
for k, v := range map1 {
    fmt.Println(k, "-->", v)
}

// Equality (requires "maps" package)
import "maps"
if maps.Equal(map1, map2) { ... }
```

## Nested Maps

```go
map5 := make(map[string]map[string]int)
map5["key1"] = anotherMap
```

## Key Points

- Accessing a missing key returns the **zero value** for the value type, not an error.
- Use the two-value assignment `val, ok := m[key]` to distinguish missing vs zero-valued.
- Must initialize with `make` before assigning values to a `var`-declared map.
- Nil maps can be read but **not written** to.

## Related Notes

- [[13 - Arrays]]
- [[14 - Slices]]
- [[16 - Range]]
