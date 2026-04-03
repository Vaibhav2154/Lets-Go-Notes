# CLI Sub Commands in Go

Tags: #go #intermediate #cli #flag #subcommands

## Overview

CLI sub-commands let you build tools like `git commit` or `docker run` — a main command with distinct sub-commands, each with their own flags.

## Code Example

```go
import (
    "flag"
    "fmt"
    "os"
)

func learningCLISubCommands() {
    subcommand1 := flag.NewFlagSet("firstSub", flag.ExitOnError)
    subcommand2 := flag.NewFlagSet("secondSub", flag.ExitOnError)

    firstFlag := subcommand1.Bool("processing", false, "Processing status")
    secondFlag := subcommand1.Int("bytes", 1024, "Byte length")

    flagsc2 := subcommand2.String("language", "Go", "Language")

    if len(os.Args) < 2 {
        fmt.Println("Requires a subcommand")
        os.Exit(1)
    }

    switch os.Args[1] {
    case "firstSub":
        subcommand1.Parse(os.Args[2:])
        fmt.Println("processing:", *firstFlag)
        fmt.Println("bytes:", *secondFlag)
    case "secondSub":
        subcommand2.Parse(os.Args[2:])
        fmt.Println("language:", *flagsc2)
    default:
        fmt.Println("unknown subcommand!")
        os.Exit(1)
    }
}
```

**Usage:**
```bash
./app firstSub -processing=true -bytes=2048
./app secondSub -language=Python
```

## Key Points

- `flag.NewFlagSet(name, errorHandling)` creates an isolated flag set for each sub-command.
- Pass `os.Args[2:]` to the sub-command's `Parse()` (skip program name and sub-command itself).
- `flag.ExitOnError` causes the program to exit if flag parsing fails.

## Related Notes

- [[24 - CLI Arguments]]
