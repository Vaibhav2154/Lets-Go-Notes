# Range in Go

Tags: #go #basics #range #iteration

## Overview

`range` iterates over arrays, slices, maps, strings, and channels.

## Syntax

```go
for index, value := range collection { ... }
```

## Code Example

```go
message := "Hello World"

for i, v := range message {
    fmt.Printf("Index: %d, Rune: %c\n", i, v)
}
```

## Key Points

- `range` operates on a **copy** of the data structure, not the original.
- For strings, `range` iterates over **Unicode code points** (runes), not bytes.
- Use `_` to discard unused index or value:
  ```go
  for _, v := range slice { ... }
  for i := range slice { ... }
  ```
- For maps, iteration order is **not guaranteed**.

## Range on Different Types

| Type | Index | Value |
|------|-------|-------|
| Array/Slice | integer index | element value |
| String | byte index | rune (Unicode code point) |
| Map | key | value |
| Channel | — | element |

## Related Notes

- [[13 - Arrays]]
- [[14 - Slices]]
- [[15 - Maps]]
- [[08 - Loops]]
