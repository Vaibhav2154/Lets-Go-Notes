# Hello World in Go

Tags: #go #basics #hello-world

## Overview

Every Go program belongs to a **package**. The entry point is the `main()` function inside `package main`.

## Code Example

```go
package basics

import (
    "fmt"
)

func main() {
    fmt.Println("Hello Go")
}
```

## Key Points

- `package` declaration is mandatory at the top of every file.
- `import` is used to bring in external or standard library packages.
- `fmt.Println` prints text followed by a newline.
- Go programs are compiled, not interpreted.

## Related Notes

- [[02 - Imports]]
- [[03 - Data Types]]
