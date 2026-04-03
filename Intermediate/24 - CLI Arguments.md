# CLI Arguments in Go

Tags: #go #intermediate #cli #flag #os.Args

## Overview

Go provides two ways to access CLI arguments: raw `os.Args` and the `flag` package for structured flags.

## `os.Args` — Raw Arguments

```go
import "os"

fmt.Println("Command:", os.Args[0])  // program name

for i, arg := range os.Args {
    fmt.Println("Argument", i, ":", arg)
}
```

## `flag` Package — Named Flags

```go
import "flag"

var name string
var age int
var male bool

flag.StringVar(&name, "name", "John", "Name of the user")
flag.IntVar(&age, "age", 18, "Age of the user")
flag.BoolVar(&male, "male", true, "Gender")

flag.Parse()

fmt.Println("Name:", name)
fmt.Println("Age:", age)
fmt.Println("Male:", male)
```

**Usage:**
```bash
./myapp -name=Alice -age=25 -male=false
```

## `flag.String` (Pointer Returns)

```go
namePtr := flag.String("user", "Guest", "Name of the user")
flag.Parse()
fmt.Println(*namePtr)
```

## Key Points

- `os.Args[0]` is always the program name.
- `flag.Parse()` must be called after all flags are defined.
- Default values are used if a flag is not provided.
- Use `flag.Usage` to customize the help output.

## Related Notes

- [[25 - CLI Sub Commands]]
- [[29 - Environment Variables]]
