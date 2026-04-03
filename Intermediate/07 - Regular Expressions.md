# Regular Expressions in Go

Tags: #go #intermediate #regex #regexp

## Overview

Go's `regexp` package provides regular expression support using RE2 syntax.

## Common Functions

```go
import "regexp"

// Compile a regex (panics on error)
re := regexp.MustCompile(`\d+`)

// Match check
fmt.Println(re.MatchString("abc123"))       // true

// Find first match
fmt.Println(re.FindString("price: 42"))     // "42"

// Find all matches
matches := re.FindAllString("1 2 3", -1)    // ["1","2","3"]

// Replace
result := re.ReplaceAllString("a1b2", "X") // "aXbX"

// Named groups and submatches
re2 := regexp.MustCompile(`(\w+)@(\w+)\.(\w+)`)
sub := re2.FindStringSubmatch("user@example.com")
// sub[0] = full match, sub[1] = "user", sub[2] = "example", etc.
```

## Key Points

- Use backtick raw strings for regex patterns to avoid double-escaping.
- `regexp.Compile` returns an error; `regexp.MustCompile` panics on bad pattern.
- Go uses **RE2 syntax** — no look-aheads or look-behinds.
- Compiled `*regexp.Regexp` objects are safe for concurrent use.

## Related Notes

- [[04 - String Functions]]
- [[06 - Text Templates]]
