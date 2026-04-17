# 4 - Buffered Channels

Tags: #go #advanced #channels 


## Overview
Buffered channels doesn't need an immediate receiver at the end all the time. It acts as non blocking until it's completely full upto it's capacity.

## Code Example
```Go
package main


import (
	"fmt"
	"time"
)

  

func main() {

// =========== BLOCKING ON SEND ONLY WHEN THE BUFFER IS FULL
// make(chan Type, capacity)


ch := make(chan int, 2)
ch <- 1
ch <- 2
fmt.Println("Receiving from buffer")

go func() {
	fmt.Println("Go routing 2 second timer started")
	time.Sleep(1 * time.Second)
	fmt.Println(<-ch)
}()

fmt.Println("Blocking starts")
ch <- 3
fmt.Println("Blocking ends")
// fmt.Println(<-ch)
// fmt.Println(<-ch)
// No immediate receiver

fmt.Println("Buffered channel")

// =========== BLOCKING ON SEND ONLY WHEN THE BUFFER IS FULL
// ch := make(chan int, 2)
// go func() {
	// time.Sleep(2*time.Second)
	// ch <- 1
// }()
// fmt.Println(<-ch)

}

```

## Key Points

- They offer asynchronous communication.
- Used when handling bursts of data.
- They block on send only if the buffer is full, they block on receive only if the buffer is empty.

## Related Notes
[[2 - Channels]]
[[3 - Unbuffered Channels]]

