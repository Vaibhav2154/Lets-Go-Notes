# Closures in Go

Tags: #go #intermediate #closures #functions

## Overview

A **closure** is a function that captures variables from its enclosing scope. The captured variables persist across multiple calls.

## Code Example

```go
func add() func() int {
    i := 0
    return func() int {
        i++
        return i
    }
}

adder := add()
fmt.Println(adder())  // 1
fmt.Println(adder())  // 2
fmt.Println(adder())  // 3

// Reassigning closure resets the captured state
adder = add()
fmt.Println(adder())  // 1

// Inline closure with immediate invocation
subtractor := func() func(int) int {
    countdown := 99
    return func(x int) int {
        countdown -= x
        return countdown
    }
}()

fmt.Println(subtractor(1))  // 98
fmt.Println(subtractor(2))  // 96
```

## Key Points

- Closures **close over** (capture) variables by reference, not by value.
- Each call to the outer function creates a **new, independent closure**.
- Reassigning the closure to a new call of the outer function **resets** the captured variable.
- Common use cases: counters, middleware, memoization, callbacks.

## Related Notes

- [[17 - Functions (Basics)]]
- [[02 - Recursion]]
