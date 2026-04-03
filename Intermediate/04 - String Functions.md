# String Functions in Go

Tags: #go #intermediate #strings #string-functions

## Overview

The `strings` package provides a rich set of functions for working with strings.

## Common Functions

```go
import "strings"

str := "Hello Go!"

// Length
len(str)                        // 9

// Concatenation
result := "Hello" + " " + "World"

// Indexing and slicing
str[0]                          // 72 (byte value of 'H')
str[1:7]                        // "ello G"

// Split & Join
parts := strings.Split("a,b,c", ",")         // ["a","b","c"]
joined := strings.Join([]string{"a","b"}, "-") // "a-b"

// Contains / Replace
strings.Contains(str, "Go")                  // true
strings.Replace(str, "Go", "World", 1)

// Trim
strings.TrimSpace("  hello  ")               // "hello"
strings.ToLower(str)
strings.ToUpper(str)

// Misc
strings.Repeat("foo ", 3)       // "foo foo foo "
strings.Count("Hello", "l")    // 2
strings.HasPrefix("Hello", "He") // true
strings.HasSuffix("Hello", "lo") // true
```

## strings.Builder (Efficient Concatenation)

```go
var builder strings.Builder
builder.WriteString("Hello")
builder.WriteString(", world!")
builder.WriteRune(' ')
result := builder.String()   // "Hello, world! "

builder.Reset()              // clear the builder
```

> **Use `strings.Builder`** instead of `+` in loops — avoids repeated allocations.

## Related Notes

- [[05 - String Formatting]]
- [[28 - Strings & Runes]]
