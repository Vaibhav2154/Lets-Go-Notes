# Imports in Go

Tags: #go #basics #imports

## Overview

Go uses `import` to include packages. Unused imports cause a **compile error**.

## Code Example

```go
import (
    "fmt"
    "net/http"
)

func importDemo() {
    fmt.Println("Hello from FMT library")

    resp, err := http.Get("https://google.com")
    if err != nil {
        fmt.Println("Error", err)
        return
    }
    defer resp.Body.Close()

    fmt.Println("HTTP Response status: ", resp.Status)
}
```

## Key Points

- Group imports with parentheses `( )`.
- Use `_` as alias to import a package only for its side effects.
- `net/http` provides HTTP client/server functionality.
- `defer` ensures `resp.Body.Close()` runs after the function returns.

## Related Notes

- [[01 - Hello World]]
- [[20 - Defer]]
