# fmt Package in Go

Tags: #go #intermediate #fmt #printing #scanning

## Overview

The `fmt` package provides functions for formatted I/O, similar to C's `printf`/`scanf`.

## Printing Functions

| Function | Description |
|----------|-------------|
| `fmt.Print(...)` | Prints without newline |
| `fmt.Println(...)` | Prints with newline |
| `fmt.Printf(format, ...)` | Formatted print |

## Formatting Functions (return string)

| Function | Description |
|----------|-------------|
| `fmt.Sprint(...)` | Returns formatted string |
| `fmt.Sprintln(...)` | Returns formatted string with newline |
| `fmt.Sprintf(format, ...)` | Returns formatted string |

## Scanning Functions (read input)

| Function | Description |
|----------|-------------|
| `fmt.Scan(...)` | Reads space-separated values |
| `fmt.Scanln(...)` | Reads space-separated values, stops at newline |
| `fmt.Scanf(format, ...)` | Reads formatted input |

## Error Formatting

```go
func checkAge(age int) error {
    if age < 18 {
        return fmt.Errorf("Age %d is too young to drive.", age)
    }
    return nil
}
```

## Code Example

```go
name := "John"
age := 25
fmt.Printf("Name: %s, Age: %d\n", name, age)

sf := fmt.Sprintf("Name: %s, Age: %d", name, age)
fmt.Println(sf)

var inputName string
fmt.Scanf("%s %d", &inputName, &age)
```

## Related Notes

- [[32 - Formatting Verbs]]
- [[05 - String Formatting]]
