# Constants in Go

Tags: #go #basics #constants

## Overview

Constants are immutable values declared with `const`. They must be assigned at declaration time.

## Code Example

```go
// Package-level constants
const PI float64 = 3.14
const GRAVITY = 9.8

func constants() {
    const DAYS int = 7

    // Constant block
    const (
        MONDAY    = 1
        TUESDAY   = 2
        WEDNESDAY = 3
    )
}
```

## Key Points

- Cannot use `:=` to declare a constant.
- Can be declared at package level or inside a function.
- Go supports **`iota`** for auto-incrementing constants in a `const` block:

```go
const (
    Sunday = iota  // 0
    Monday         // 1
    Tuesday        // 2
)
```

- Constants are **typed** or **untyped**. Untyped constants are more flexible in expressions.

## Related Notes

- [[04 - Variables]]
- [[05 - Naming Conventions]]
