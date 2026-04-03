# Base64 Encoding in Go

Tags: #go #intermediate #base64 #encoding

## Overview

Base64 encodes binary data into ASCII characters. Commonly used for transmitting binary data in text-based protocols (email, JSON, HTTP).

## Code Example

```go
import "encoding/base64"

data := []byte("He~lo, Base64 Encoding")

// Standard encoding (uses + and /)
encoded := base64.StdEncoding.EncodeToString(data)
fmt.Println(encoded)

// Decode
decoded, err := base64.StdEncoding.DecodeString(encoded)
if err != nil {
    fmt.Println("Error:", err)
    return
}
fmt.Println("Decoded:", string(decoded))

// URL-safe encoding (replaces + with - and / with _)
urlSafe := base64.URLEncoding.EncodeToString(data)
fmt.Println("URL Safe:", urlSafe)
```

## Encoding Types

| Type | Uses | Purpose |
|------|------|---------|
| `StdEncoding` | `+`, `/` | Standard Base64 |
| `URLEncoding` | `-`, `_` | URL/filename safe |
| `RawStdEncoding` | No `=` padding | Raw standard |
| `RawURLEncoding` | No `=` padding | Raw URL-safe |

## Key Points

- Base64 increases data size by ~33%.
- Use `URLEncoding` when embedding in URLs to avoid issues with `+` and `/`.
- `EncodeToString` → `string`; `DecodeString` → `[]byte`.

## Related Notes

- [[16 - Crypto]]
- [[13 - URL Parsing]]
