# String Formatting in Go

Tags: #go #intermediate #strings #formatting #raw-strings

## Overview

Go supports both **interpreted** and **raw** string literals, and printf-style width/alignment formatting.

## Code Example

```go
// Width and alignment
num := 424
fmt.Printf("%05d\n", num)         // "00424"  (zero-padded, width 5)

message := "Hello"
fmt.Printf("|%10s|\n", message)   // "|     Hello|"  (right-aligned)
fmt.Printf("|%-10s|\n", message)  // "|Hello     |"  (left-aligned)
```

## Interpreted vs Raw Strings

```go
// Interpreted string: escape sequences ARE processed
message1 := "Hello \nWorld!"
// output:
// Hello
// World!

// Raw string (backtick): escape sequences are NOT processed
message2 := `Hello \nWorld!`
// output: Hello \nWorld!

// Useful for multi-line text, SQL, regex patterns
sqlQuery := `SELECT * FROM users WHERE age > 30`
```

## Width/Precision Formatting

| Format | Meaning |
|--------|---------|
| `%5d` | Width 5, right-justified |
| `%-5d` | Width 5, left-justified |
| `%05d` | Width 5, zero-padded |
| `%.2f` | Precision 2 for floats |
| `%8s` | Width 8, right-justified string |
| `%-8s` | Width 8, left-justified string |

## Related Notes

- [[03 - fmt Package]]
- [[32 - Formatting Verbs]]
