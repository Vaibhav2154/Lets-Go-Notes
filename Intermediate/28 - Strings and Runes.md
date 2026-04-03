# Strings & Runes in Go

Tags: #go #intermediate #strings #runes #unicode #utf8

## Overview

Go strings are **immutable byte sequences** encoded in UTF-8. A `rune` is an alias for `int32` and represents a Unicode code point.

## Code Example

```go
import "unicode/utf8"

message := "Hello Go!\n"       // interpreted string (escape sequences processed)
rawMessage := `Hello\n vaibhav` // raw string (backslash NOT interpreted)

// String indexing returns bytes (not runes)
fmt.Println(message[0])  // 72 (ASCII for 'H')

// Rune count (not byte count)
greeting := "Hello "
fmt.Println(utf8.RuneCountInString(greeting))  // 6

// String comparison uses Unicode code points
"Apple" < "banana"  // true (A=65, a=97)
"app" < "Apple"     // false

// Iterate over runes
for idx, val := range "Apple" {
    fmt.Printf("%d\t %c\n", idx, val)
}
```

## Rune Literals

```go
var ch rune = 'a'    // 97
kch := 'ಕ'          // Kannada letter Ka (Unicode code point)

fmt.Printf("%c, %c\n", ch, kch)

cstr := string(ch)   // "a"
kstr := string(kch)  // "ಕ"
```

## Key Points

- `len(str)` → number of **bytes** (not characters).
- `utf8.RuneCountInString(str)` → number of **runes** (characters).
- `range` on a string iterates over **runes**, yielding `(byte index, rune)`.
- Go source files are UTF-8; single-quoted literals `'a'` are rune literals.

## Related Notes

- [[04 - String Functions]]
- [[05 - String Formatting]]
