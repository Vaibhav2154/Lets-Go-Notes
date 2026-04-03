# Directories in Go

Tags: #go #intermediate #directories #os #filepath

## Overview

Go's `os` and `path/filepath` packages provide functions to create, list, and walk directories.

## Common Operations

```go
import (
    "os"
    "path/filepath"
)

// Create a directory
os.Mkdir("mydir", 0755)

// Create nested directories
os.MkdirAll("a/b/c", 0755)

// Remove directory (must be empty)
os.Remove("mydir")

// Remove directory and all contents
os.RemoveAll("a")

// List directory contents
entries, _ := os.ReadDir(".")
for _, e := range entries {
    fmt.Println(e.Name(), e.IsDir())
}

// Walk a directory tree
filepath.WalkDir(".", func(path string, d fs.DirEntry, err error) error {
    if err != nil {
        return err
    }
    fmt.Println(path)
    return nil
})
```

## File Path Utilities (same as File Paths note)

```go
filepath.Join("home", "Documents", "file.zip")  // cross-platform path join
filepath.Clean("./data/../data/file.txt")        // normalize
filepath.Abs("./relative")                       // get absolute path
```

## Key Points

- File permissions in Go are specified as octal: `0755` = `rwxr-xr-x`.
- `os.ReadDir` is the modern replacement for `ioutil.ReadDir` (deprecated).
- `filepath.WalkDir` visits all files and directories recursively.

## Related Notes

- [[20 - File Paths]]
- [[22 - Temp Files]]
- [[17 - Reading Files]]
