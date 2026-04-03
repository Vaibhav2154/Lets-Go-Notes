# Recover in Go

Tags: #go #basics #recover #panic #error-handling

## Overview

`recover` stops a panicking goroutine from crashing. It must be called **inside a deferred function**.

## Code Example

```go
func recover1() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered:", r)
        }
    }()

    fmt.Println("Start the process")
    panic("Something went wrong")
}

func learningrecover() {
    recover1()
    fmt.Println("Returned from process")  // this still executes
}
```

## How It Works

1. `panic("...")` is called inside `recover1()`.
2. The deferred function runs.
3. `recover()` captures the panic value and **stops the propagation**.
4. Execution continues after the call to `recover1()` in the caller.

## Key Points

- `recover()` returns `nil` if there's no panic.
- Only works when called **directly inside a deferred function**.
- After recovery, execution does NOT resume inside the panicking function — it resumes in the calling function.

## Related Notes

- [[20 - Defer]]
- [[21 - Panic]]
