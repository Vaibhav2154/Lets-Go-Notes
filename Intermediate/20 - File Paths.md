# File Paths in Go

Tags: #go #intermediate #filepath #os #path

## Overview

The `path/filepath` package provides utilities for working with file paths in an OS-independent way.

## Code Example

```go
import (
    "fmt"
    "path/filepath"
    "strings"
)

// Join paths
joinedPath := filepath.Join("home", "Documents", "file.zip")
// → "home/Documents/file.zip"

// Normalize (clean) a path
normalized := filepath.Clean("./data/../data/file.txt")
// → "data/file.txt"

// Split into directory and file
dir, file := filepath.Split("/home/user/docs/file.txt")
// dir = "/home/user/docs/", file = "file.txt"

// Base (last element)
filepath.Base("/home/user/docs/")  // "docs"

// Check if absolute
filepath.IsAbs("./relative")   // false
filepath.IsAbs("/absolute")    // true

// Extension
filepath.Ext("file.txt")       // ".txt"
strings.TrimSuffix("file.txt", filepath.Ext("file.txt"))  // "file"

// Relative path between two paths
rel, _ := filepath.Rel("a/b", "a/b/t/file")  // "t/file"

// Convert relative to absolute
absPath, _ := filepath.Abs("./data/file.txt")
```

## Key Points

- `filepath.Join` always uses the OS-appropriate separator (`/` on Unix, `\` on Windows).
- `filepath.Clean` removes redundant separators and `.` / `..` elements.
- Prefer `path/filepath` over `path` for filesystem paths.

## Related Notes

- [[17 - Reading Files]]
- [[18 - Writing Files]]
- [[21 - Directories]]
