# Time Formatting in Go

Tags: #go #intermediate #time #formatting

## Overview

Go formats and parses time using a **reference time** instead of format codes like `%Y-%m-%d`.

## Reference Time

```
Mon Jan 2 15:04:05 MST 2006
```

Each component maps to a specific meaning:

| Value | Component |
|-------|-----------|
| `2006` | Year |
| `01` | Month (zero-padded) |
| `02` | Day |
| `15` | Hour (24h) |
| `03` | Hour (12h) |
| `04` | Minute |
| `05` | Second |
| `PM` | AM/PM |
| `MST` or `Z07:00` | Timezone |

## Code Example

```go
// ISO 8601 / RFC 3339
layout := "2006-01-02T15:04:05Z07:00"
str := "2024-07-04T14:30:18Z"
t, _ := time.Parse(layout, str)
fmt.Println(t)

// Custom format
str1 := "Jul 03, 2024 03:18 PM"
layout1 := "Jan 02, 2006 03:04 PM"
t1, _ := time.Parse(layout1, str1)
fmt.Println(t1)
```

## Formatting (time.Time → string)

```go
t.Format("2006-01-02")               // "2024-07-04"
t.Format("Monday, Jan _2 2006")      // "Thursday, Jul  4 2024"
t.Format(time.RFC3339)               // built-in constant
```

## Built-in Layout Constants

```go
time.RFC3339     // "2006-01-02T15:04:05Z07:00"
time.RFC1123     // "Mon, 02 Jan 2006 15:04:05 MST"
time.Kitchen     // "3:04PM"
time.DateOnly    // "2006-01-02"
```

## Related Notes

- [[08 - Time]]
- [[09 - Epoch]]
