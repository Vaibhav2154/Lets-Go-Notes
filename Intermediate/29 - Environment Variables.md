# Environment Variables in Go

Tags: #go #intermediate #env #os #configuration

## Overview

Go provides `os` package functions to get, set, and unset environment variables at runtime.

## Code Example

```go
import (
    "fmt"
    "os"
)

// Get env var
user := os.Getenv("USER")
home := os.Getenv("HOME")
fmt.Println("User:", user)
fmt.Println("Home:", home)

// Set env var
err := os.Setenv("FRUIT", "APPLE")
fmt.Println("FRUIT:", os.Getenv("FRUIT"))

// Unset env var
err = os.Unsetenv("FRUIT")
fmt.Println("FRUIT after unset:", os.Getenv("FRUIT"))  // ""

// List all env vars
for _, e := range os.Environ() {
    pair := strings.SplitN(e, "=", 2)
    fmt.Println(pair[0], "=", pair[1])
}
```

## `strings.SplitN` Reminder

```go
strings.SplitN("a=b=c=d", "=", 2)   // ["a", "b=c=d"]
strings.SplitN("a=b=c=d", "=", 3)   // ["a", "b", "c=d"]
strings.SplitN("a=b=c=d", "=", -1)  // ["a", "b", "c", "d"]  (all)
```

## Key Points

- `os.Getenv` returns `""` for missing variables — use `os.LookupEnv` to distinguish missing vs empty:
  ```go
  val, exists := os.LookupEnv("FRUIT")
  ```
- Env vars set with `os.Setenv` only affect the **current process** and its children.
- For configuration, prefer `.env` files with a library like `godotenv` in applications.

## Related Notes

- [[24 - CLI Arguments]]
- [[30 - Logging]]
