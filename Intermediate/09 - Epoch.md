# Epoch (Unix Time) in Go

Tags: #go #intermediate #time #epoch #unix

## Overview

Unix time (epoch) is the number of seconds since **January 1, 1970 00:00:00 UTC**.

## Code Example

```go
import "time"

now := time.Now()

// Get Unix timestamp (seconds)
unixTime := now.Unix()
fmt.Println("Current Unix Time:", unixTime)

// Convert Unix timestamp back to time.Time
t := time.Unix(unixTime, 0)
fmt.Println(t)
fmt.Println("Date:", t.Format("2006-01-02"))
```

## Functions

| Function | Returns |
|----------|---------|
| `t.Unix()` | Seconds since epoch |
| `t.UnixMilli()` | Milliseconds since epoch |
| `t.UnixMicro()` | Microseconds since epoch |
| `t.UnixNano()` | Nanoseconds since epoch |
| `time.Unix(sec, nsec)` | `time.Time` from epoch seconds |

## Key Points

- Use `time.Now().UnixNano()` as a high-resolution seed for random number generation.
- Epoch is timezone-independent (always UTC-based).

## Related Notes

- [[08 - Time]]
- [[10 - Time Formatting]]
