# Time in Go

Tags: #go #intermediate #time #datetime

## Overview

Go's `time` package provides time types and functions for working with dates, durations, and time zones.

## Code Example

```go
import "time"

// Current time
fmt.Println(time.Now())

// Specific date
specificTime := time.Date(2024, time.July, 30, 12, 0, 0, 0, time.UTC)

// Parsing time (Go's reference time: Mon Jan 2 15:04:05 MST 2006)
parsedTime, _ := time.Parse("2006-01-02", "2020-05-01")

// Formatting
t := time.Now()
fmt.Println(t.Format("Monday 06-01-02 15-04-05"))

// Arithmetic
oneDayLater := t.Add(time.Hour * 24)
t.Round(time.Hour)     // round to nearest hour
t.Truncate(time.Hour)  // truncate to hour

// Time zones
loc, _ := time.LoadLocation("America/New_York")
tInNY := time.Now().In(loc)

// Duration between two times
t1 := time.Date(2024, time.July, 4, 12, 0, 0, 0, time.UTC)
t2 := time.Date(2024, time.July, 4, 18, 0, 0, 0, time.UTC)
duration := t2.Sub(t1)  // 6h0m0s

// Compare
t2.After(t1)   // true
t1.Before(t2)  // true
```

## Go's Reference Time

Go uses **January 2, 2006, 15:04:05** (Mon Jan 2 15:04:05 MST 2006) as the reference for format strings.

| Component | Reference value |
|-----------|----------------|
| Year | `2006` |
| Month | `01` |
| Day | `02` |
| Hour | `15` |
| Minute | `04` |
| Second | `05` |

## Related Notes

- [[09 - Epoch]]
- [[10 - Time Formatting]]
