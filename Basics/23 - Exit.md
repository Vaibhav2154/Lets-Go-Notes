# Exit in Go

Tags: #go #basics #exit #os

## Overview

`os.Exit(code)` terminates the program immediately with the given exit code. Deferred functions are **NOT** called.

## Code Example

```go
import (
    "fmt"
    "os"
)

func learningexit() {
    defer fmt.Println("This is a deferred statement")  // will NOT run
    fmt.Println("Starting the main function")

    os.Exit(2)  // exits with code 2

    fmt.Println("This won't be executed")
}
```

## Exit Codes

| Code | Meaning |
|------|---------|
| `0` | Success |
| `1` | General error |
| `2` | Misuse / custom error |
| Non-zero | Failure in general |

## Key Points

- Unlike `panic`, `os.Exit` does **not run deferred functions**.
- `os.Exit(0)` signals success to the shell.
- Use `log.Fatal(...)` which internally calls `os.Exit(1)` after logging.

## Related Notes

- [[20 - Defer]]
- [[21 - Panic]]
