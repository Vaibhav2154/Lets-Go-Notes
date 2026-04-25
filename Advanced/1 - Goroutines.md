# 1 - Goroutines

Tags: #go #advanced #goroutines


## Overview

***Goroutines are lightweight concurrent functions managed by the Go runtime scheduler***.

They are useful when tasks can run independently (I/O, background jobs, concurrent processing), but they should be coordinated to avoid leaks and race conditions.

## Code Example

```go
package main

import (
	"fmt"
	"sync"
	"time"
)

func main() {
	fmt.Println("Program started")

	var wg sync.WaitGroup
	wg.Add(3)

	go sayHello(&wg)
	go printNumbers(&wg)
	go printAlphabets(&wg)

	wg.Wait()
	fmt.Println("All goroutines finished")
}

func sayHello(wg *sync.WaitGroup) {
	defer wg.Done()
	time.Sleep(300 * time.Millisecond)
	fmt.Println("Hello from goroutine")
}

func printNumbers(wg *sync.WaitGroup) {
	defer wg.Done()
	for i := 0; i < 5; i++ {
		fmt.Println("Number:", i)
		time.Sleep(100 * time.Millisecond)
	}
}

func printAlphabets(wg *sync.WaitGroup) {
	defer wg.Done()
	for _, ch := range "abcde" {
		fmt.Println("Alphabet:", string(ch))
		time.Sleep(120 * time.Millisecond)
	}
}
```


## Key Points

- Goroutines are non-blocking from the caller side.
- The Go scheduler multiplexes goroutines over OS threads (M:N model).
- Prefer proper coordination (`sync.WaitGroup`, channels, context) over `time.Sleep` in production logic.
- Always design cancellation/exit paths to prevent goroutine leaks.

## Related Topics

[[2 - Channels]]

