# Loops in Go

Tags: #go #basics #loops #for

## Overview

Go has **only one loop keyword**: `for`. It can act as a traditional for-loop, a while-loop, or an infinite loop.

## Variants

### Classic For Loop
```go
for i := 1; i <= 5; i++ {
    fmt.Println(i)
}
```

### While-Style Loop
```go
i := 0
for i <= 5 {
    fmt.Println(i)
    i++
}
```

### Infinite Loop
```go
for {
    fmt.Println("runs forever")
}
```

### Iterator with `range`
```go
numbers := []int{1, 2, 3, 4, 5}
for index, value := range numbers {
    fmt.Printf("Index %d, Value %d\n", index, value)
}

// Range over integer (Go 1.22+)
for i := range 10 {
    fmt.Println(10 - i)
}
```

### Break & Continue
```go
sum := 0
for {
    sum += 7
    if sum >= 50 {
        break
    }
    fmt.Println(sum)
}
```

## Key Points

- Use `break` to exit a loop early.
- Use `continue` to skip to the next iteration.
- Use `_` (blank identifier) to ignore the index in range: `for _, v := range nums`.

## Related Notes

- [[09 - Guessing Game]]
- [[16 - Range]]
