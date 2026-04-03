# Line Filter in Go

Tags: #go #intermediate #files #filter #strings

## Overview

A line filter reads a file line by line, filters lines matching a keyword, and processes them.

## Code Example

```go
import (
    "bufio"
    "fmt"
    "os"
    "strings"
)

file, err := os.Open("example.txt")
if err != nil { ... }
defer file.Close()

scanner := bufio.NewScanner(file)
keyword := "important"
lineNumber := 1

for scanner.Scan() {
    line := scanner.Text()
    if strings.Contains(line, keyword) {
        updatedLine := strings.ReplaceAll(line, keyword, "necessary")
        fmt.Printf("%d Filtered line: %v\n", lineNumber, line)
        lineNumber++
        fmt.Printf("%d Updated line: %v\n", lineNumber, updatedLine)
        lineNumber++
    }
}

if err := scanner.Err(); err != nil {
    fmt.Println("Error scanning file:", err)
}
```

## Key Points

- `strings.Contains(line, keyword)` checks if the line contains a keyword.
- `strings.ReplaceAll(s, old, new)` replaces all occurrences.
- `bufio.Scanner` reads line by line without loading the entire file into memory.
- Useful for log processing, grep-like tools, data transformation pipelines.

## Related Notes

- [[17 - Reading Files]]
- [[04 - String Functions]]
