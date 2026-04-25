# 4 - Buffered Channels

Tags: #go #advanced #channels 


## Overview
Buffered channels have capacity, so sends can proceed without an immediate receiver until the buffer becomes full.

```go
package main

import (
	"fmt"
)

func main() {
	ch := make(chan int, 2)

	ch <- 1
	ch <- 2

	fmt.Println(<-ch)
	fmt.Println(<-ch)
}

```

## Key Points

- They offer asynchronous communication.
- Used when handling bursts of data.
- They block on send only when the buffer is full.
- They block on receive only when the buffer is empty.

## Related Notes
[[2 - Channels]]
[[3 - Unbuffered Channels]]

