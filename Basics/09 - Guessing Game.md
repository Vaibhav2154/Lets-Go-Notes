# Guessing Game in Go

Tags: #go #basics #project #random #input

## Overview

A simple number guessing game that demonstrates random number generation, user input, and loop control flow.

## Code Example

```go
import (
    "fmt"
    "math/rand"
    "time"
)

func guessing() {
    source := rand.NewSource(time.Now().UnixNano())
    random := rand.New(source)
    target := random.Intn(100) + 1  // Random number between 1 and 100

    fmt.Println("Welcome to guessing game")
    var guess int

    for {
        fmt.Println("Enter your guess")
        fmt.Scanln(&guess)

        if guess == target {
            fmt.Println("Congrats you have guessed it correctly")
            break
        } else if guess < target {
            fmt.Println("U are behind the number")
        } else {
            fmt.Println("U are ahead of the number")
        }
    }
}
```

## Key Points

- `rand.NewSource(time.Now().UnixNano())` seeds the random number generator with the current time.
- `rand.Intn(100) + 1` generates a number between 1 and 100.
- `fmt.Scanln(&guess)` reads user input from stdin.

## Related Notes

- [[08 - Loops]]
- [[11 - If Else]]
