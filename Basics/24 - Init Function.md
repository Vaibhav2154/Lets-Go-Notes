# Init Function in Go

Tags: #go #basics #init #package-lifecycle

## Overview

`init()` is a special function that runs **automatically before `main()`**. Multiple `init()` functions can exist in the same file or package.

## Code Example

```go
func init() {
    fmt.Println("Initializing the package 1")
}
func init() {
    fmt.Println("Initializing the package 2")
}
func init() {
    fmt.Println("Initializing the package 3")
}

func learninginit() {
    fmt.Println("This is main function")
}
```

**Execution order:** All `init()` functions run in declaration order, before any other code.

## Package Initialization Order

1. Package-level variable declarations are evaluated.
2. All `init()` functions in the package run (in source order).
3. `main()` runs.

## Key Points

- Cannot call `init()` explicitly — it's called by the Go runtime.
- Multiple `init()` in multiple files: executed in the order the files are compiled (alphabetical by filename).
- Common uses: setup configuration, register drivers, validate state.
- Avoid side-effecting `init()` — prefer explicit initialization in `main()`.

## Related Notes

- [[01 - Hello World]]
- [[04 - Variables]]
