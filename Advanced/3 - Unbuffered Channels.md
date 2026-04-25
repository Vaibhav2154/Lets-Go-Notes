# 3 - Un-buffered Channels

Tags: #go #advanced #channels


## Overview

***Unbuffered channels have zero capacity, so each send waits for a matching receive***.

This gives strict synchronization between goroutines.


## Code Example

```go
package main

import "fmt"

func main() {
	ch := make(chan int)

	go func() {
		ch <- 1
	}()

	receiver := <-ch
	fmt.Println(receiver)
}
```

## Key Points
- Unbuffered channels synchronize sender and receiver at the handoff point.
- Great for signaling and strict ordering.
- Missing sender/receiver pairs can cause deadlocks.

## Related Notes

[[1 - Goroutines]]
[[2 - Channels]]
[[4 - Buffered Channels]]
