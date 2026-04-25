# 6 - Channel Directions

Tags: #go #advanced #channels #concurrency


## Overview

***Channel direction in Go lets you restrict how a function can use a channel***. 
##### This improves safety and readability in concurrent code.

- `chan<- T` means send-only channel (can only send values)
- `<-chan T` means receive-only channel (can only receive values)
- `chan T` means bidirectional channel (send and receive both)

In this pattern:
- `producer` only sends values and closes the channel.
- `consumer` only reads values from the channel.

## Code Example
```go
package main

import "fmt"

func main() {
	ch := make(chan int)
	producer(ch)
	consumer(ch)
}

// producer can only send values to ch.
func producer(ch chan<- int) {
	go func() {
		for i := 0; i < 5; i++ {
			ch <- i
		}
		close(ch)
	}()
}

// consumer can only receive values from ch.
func consumer(ch <-chan int) {
	for v := range ch {
		fmt.Println(v)
	}
}
```

## Key Points

- Directional channels are a compile-time safety feature.
- They prevent accidental misuse, like reading in a sender function.
- `range ch` keeps receiving until the channel is closed.
- Only the sender side should close the channel.
- A bidirectional channel can be passed to directional parameters.


## Related Notes

[[2 - Channels]]
[[3 - Unbuffered Channels]]
[[4 - Buffered Channels]]
[[5 - Channel Synchronization]]
