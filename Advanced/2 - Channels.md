# 2 - Channels

Tags: #go #advanced #channels


## Overview

***Channels are typed conduits used by goroutines to communicate and synchronize***.

They help avoid shared-memory coordination by passing data explicitly.

## Code Example
```Go
package main

"fmt"
"time"
	"fmt"
	"time"

// variable := make(chan type)
greeting := make(chan string)
	greeting := make(chan string)

	go func() {
		defer close(greeting)

		greeting <- "Hello"
		greeting <- "Vaibhav"

		for _, e := range "ABCDE" {
			greeting <- string(e)
		}
	}()

	for msg := range greeting {
		fmt.Println("Received:", msg)


	time.Sleep(20 * time.Millisecond)
```


## Key Points
- They are blocking because they continuously try to receive values, i.e. they are ready to receive continuous flow of data
- Main function/thread is also a go routine.
- Channels are blocking by default:
  - send blocks until a receiver is ready (for unbuffered channels)
  - receive blocks until data is available
- `main` also runs as a goroutine.
- Close a channel when no more values will be sent.
- Use `for value := range ch` to receive until closed.



## Related Notes

[[1 - Goroutines]]
[[3 - Unbuffered Channels]]
[[4 - Buffered Channels]]
[[5 - Channel Synchronization]]

