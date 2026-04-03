# Panic in Go

Tags: #go #basics #panic #error-handling

## Overview

`panic` stops normal execution of the current goroutine and begins **unwinding the stack**, running deferred functions as it unwinds.

## Code Example

```go
func process1(input int) {
    defer fmt.Println("Defer 2")
    defer fmt.Println("Defer 1")
    defer fmt.Println("Defer 0")

    if input < 0 {
        panic("Input must be a non-negative number")
    }
    fmt.Println("Processing input")
}
```

- If `input < 0`, panic fires → all deferred functions run → program exits with a stack trace.

## Key Points

- **Deferred functions still run** after a panic.
- Panic prints the goroutine stack trace to stderr.
- Only use panic for truly unexpected, unrecoverable conditions.
- Use `recover()` inside a deferred function to catch a panic.
- Prefer returning `error` over calling `panic` in most situations.

## Related Notes

- [[20 - Defer]]
- [[22 - Recover]]
- [[23 - Exit]]
