# Bufio Package in Go

Tags: #go #intermediate #bufio #buffered-io #stdin

## Overview

`bufio` wraps an `io.Reader` or `io.Writer` with buffering, improving I/O efficiency and providing convenient methods.

## Buffered Writer

```go
import (
    "bufio"
    "os"
)

writer := bufio.NewWriter(os.Stdout)

data := []byte("Hello, bufio package!\n")
n, err := writer.Write(data)
if err != nil { ... }
fmt.Printf("Wrote %d bytes\n", n)

// IMPORTANT: Flush to ensure data is actually written
writer.Flush()

// WriteString
writer.WriteString("This is a string.\n")
writer.Flush()
```

## Buffered Reader

```go
reader := bufio.NewReader(os.Stdin)

// Read until delimiter
line, err := reader.ReadString('\n')
line = strings.TrimSpace(line)

// Read fixed bytes
data := make([]byte, 20)
n, err := reader.Read(data)
```

## Scanner (Line-by-Line Reading)

```go
scanner := bufio.NewScanner(file)
for scanner.Scan() {
    line := scanner.Text()
    fmt.Println(line)
}
err := scanner.Err()
```

## Key Points

- Always call `Flush()` on `bufio.Writer` or data may not be written.
- `bufio.Scanner` is the idiomatic way to read files line by line.
- Default scanner buffer size is 64KB; use `scanner.Buffer()` to increase it.

## Related Notes

- [[17 - Reading Files]]
- [[18 - Writing Files]]
- [[26 - IO]]
