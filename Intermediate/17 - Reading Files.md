# Reading Files in Go

Tags: #go #intermediate #files #io #os

## Overview

Go's `os` package opens files, and `bufio.Scanner` makes it easy to read line by line.

## Code Example

```go
import (
    "bufio"
    "fmt"
    "os"
)

file, err := os.Open("output.txt")
if err != nil {
    fmt.Println("Error opening file:", err)
    return
}
defer func() {
    fmt.Println("Closing file")
    file.Close()
}()

fmt.Println("File opened successfully.")

// Read line by line with Scanner
scanner := bufio.NewScanner(file)
for scanner.Scan() {
    line := scanner.Text()
    fmt.Println("Line:", line)
}

if err := scanner.Err(); err != nil {
    fmt.Println("Error reading file:", err)
}
```

## Reading Entire File at Once

```go
import "os"

data, err := os.ReadFile("output.txt")
if err != nil { ... }
fmt.Println(string(data))
```

## Key Points

- `os.Open` opens for reading only. Use `os.OpenFile` for more control.
- Always `defer file.Close()` immediately after a successful open.
- `bufio.Scanner` is idiomatic for line-by-line reading.
- `os.ReadFile` reads the entire file into memory in one call (Go 1.16+).

## Related Notes

- [[18 - Writing Files]]
- [[15 - Bufio]]
- [[20 - File Paths]]
