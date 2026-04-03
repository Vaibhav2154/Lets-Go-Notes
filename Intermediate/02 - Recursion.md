# Recursion in Go

Tags: #go #intermediate #recursion

## Overview

Recursion is when a function calls itself to solve a smaller sub-problem. It requires a **base case** to terminate.

## Code Example

```go
// Sum of first n natural numbers (note: this sums 1..n)
func fact(n int) int {
    if n == 0 {
        return 0
    }
    return n + fact(n-1)
}

// Sum of digits
func sumOfDigits(n int) int {
    if n < 10 {
        return n
    }
    return n%10 + sumOfDigits(n/10)
}

fmt.Println(fact(5))        // 15  (5+4+3+2+1+0)
fmt.Println(sumOfDigits(81)) // 9  (8+1)
```

## Key Points

- Always define a **base case** to stop recursion (avoid infinite recursion / stack overflow).
- Go does **not** optimize tail recursion — deep recursion can cause a stack overflow.
- For very deep recursion, prefer iterative solutions or use a **trampoline** pattern.

## When to Use

- Tree traversal
- Divide-and-conquer algorithms (merge sort, quicksort)
- Parsing nested structures
- Mathematical sequences (Fibonacci, factorials)

## Related Notes

- [[01 - Closures]]
- [[17 - Functions (Basics)]]
