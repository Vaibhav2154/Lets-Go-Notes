# Defer in Go

Tags: #go #basics #defer #cleanup

## Overview

`defer` schedules a function call to execute **after the surrounding function returns**. Multiple deferred calls run in **LIFO** (Last In, First Out) order.

## Code Example

```go
func process(i int) {
    defer fmt.Println("Deferred value 1", i)     // runs 4th
    defer fmt.Println("Defer statement")          // runs 3rd
    defer fmt.Println("Defer statement 3")        // runs 2nd
    defer fmt.Println("Defer statement 2")        // runs 1st (LIFO)
    fmt.Println("Normal statement")
    i++
    fmt.Println("Value of i", i)
}
```

**Output order:**
1. `Normal statement`
2. `Value of i 11`
3. `Defer statement 2`
4. `Defer statement 3`
5. `Defer statement`
6. `Deferred value 1 10`  ← uses value of `i` at defer time, not at execution

## Key Points

- Arguments to deferred functions are **evaluated immediately** (at the `defer` statement), not when executed.
- Deferred calls still run even when the function **panics**.
- Common use cases:
  - Closing files/connections: `defer file.Close()`
  - Releasing mutex locks: `defer mu.Unlock()`
  - Logging function exit

## Related Notes

- [[21 - Panic]]
- [[22 - Recover]]
- [[02 - Imports]]
