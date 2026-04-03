# Embed Directive in Go

Tags: #go #intermediate #embed #go:generate

## Overview

The `//go:embed` directive embeds files or directories into the compiled binary at build time, using the `embed` package.

## Code Example

```go
import (
    "embed"
    "fmt"
    "io/fs"
    "log"
)

//go:embed example_.txt
var content string  // embed as string

//go:embed basics
var basicsFolder embed.FS  // embed as file system

func learningEmbedDirective() {
    fmt.Println("Embedded content:", content)

    // Read a specific file from embedded FS
    data, err := basicsFolder.ReadFile("basics/hello.txt")
    if err != nil { ... }
    fmt.Println("File content:", string(data))

    // Walk embedded directory
    fs.WalkDir(basicsFolder, "basics", func(path string, d fs.DirEntry, err error) error {
        fmt.Println(path)
        return nil
    })
}
```

## Key Points

- The `//go:embed` directive must immediately precede the variable declaration (no blank line).
- Embed targets must be **relative paths** within the module.
- Supports embedding as:
  - `string` — single file as a string
  - `[]byte` — single file as bytes
  - `embed.FS` — one or more files/dirs as a virtual filesystem
- Embedded files become part of the binary — no external files needed at runtime.
- Cannot embed paths starting with `.` or `_` by default (use `all:` prefix to include hidden files).

## Related Notes

- [[17 - Reading Files]]
- [[21 - Directories]]
