# Random Numbers in Go

Tags: #go #intermediate #random #math/rand

## Overview

Go's `math/rand` package provides pseudo-random number generation. As of Go 1.20+, the default source is automatically seeded.

## Code Example

```go
import "math/rand"

// Integer: [0, n)
dice := rand.Intn(6) + 1        // 1 to 6

// Float: [0.0, 1.0)
f := rand.Float64()

// Old style: explicit seed (pre-Go 1.20)
src := rand.NewSource(time.Now().Unix())
rng := rand.New(src)
val := rng.Intn(101)
```

## Practical Example — Dice Game

```go
die1 := rand.Intn(6) + 1
die2 := rand.Intn(6) + 1
fmt.Printf("You rolled a %d and a %d.\n", die1, die2)
fmt.Println("Total:", die1+die2)
```

## Key Points

- `rand.Intn(n)` → random int in `[0, n)`.
- `rand.Float64()` → random float in `[0.0, 1.0)`.
- In Go 1.20+, the global source is auto-seeded — no need for manual seeding in production.
- For cryptographically secure random numbers, use `crypto/rand`.

## Related Notes

- [[09 - Guessing Game (Basics)]]
- [[16 - Crypto]]
