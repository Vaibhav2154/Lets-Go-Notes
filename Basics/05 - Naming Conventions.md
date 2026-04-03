# Naming Conventions in Go

Tags: #go #basics #naming-conventions

## Overview

Go has specific naming conventions that also affect **visibility** (exported vs unexported).

## Conventions

| Style | Usage | Examples |
|-------|-------|---------|
| `PascalCase` | Structs, interfaces, exported names | `CalculateArea`, `UserInfo`, `NewHTTPRequest` |
| `camelCase` | Variables, unexported identifiers | `javaScript`, `htmlDocument`, `employeeID` |
| `UPPER_CASE` / `ALLCAPS` | Constants | `PI`, `MAXRETRIES` |
| `snake_case` | File names (convention) | `user_service.go`, `http_handler.go` |

## Visibility Rule

- **Uppercase first letter** → Exported (public, accessible from other packages)
- **Lowercase first letter** → Unexported (private, package-local only)

## Code Example

```go
type Employee struct {   // Exported struct
    FirstName string     // Exported field
    LastName  string     // Exported field
    Age       int
}

const MAXRETRIES = 5     // Constant (UPPER)
var employeeID = 1001    // camelCase variable
```

## Related Notes

- [[04 - Variables]]
- [[06 - Constants]]
