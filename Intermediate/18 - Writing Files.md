# Writing Files in Go

Tags: #go #intermediate #files #io #os

## Overview

Go's `os` package provides functions to create and write to files.

## Code Example

```go
import ( "fmt"; "os" )

// Create/overwrite a file
file, err := os.Create("output.txt")
if err != nil {
    fmt.Println("Error creating file:", err)
    return
}
defer file.Close()

// Write bytes
data := []byte("Hello World!\n")
_, err = file.Write(data)
if err != nil {
    fmt.Println("Error writing to file:", err)
    return
}

// Write string
_, err = file.WriteString("Hello Go!\n")
```

## Append to Existing File

```go
file, err := os.OpenFile("output.txt", os.O_APPEND|os.O_CREATE|os.O_WRONLY, 0644)
if err != nil { ... }
defer file.Close()
file.WriteString("Appended line\n")
```

## `os.OpenFile` Flags

| Flag | Meaning |
|------|---------|
| `os.O_RDONLY` | Read only |
| `os.O_WRONLY` | Write only |
| `os.O_RDWR` | Read and write |
| `os.O_APPEND` | Append to file |
| `os.O_CREATE` | Create if not exists |
| `os.O_TRUNC` | Truncate to zero on open |

## Write Entire File at Once

```go
err := os.WriteFile("output.txt", []byte("content"), 0644)
```

## Related Notes

- [[17 - Reading Files]]
- [[15 - Bufio]]
- [[22 - Temp Files]]
