# 5 - Channel Synchronization

Tags: #go #advanced #channels 


## Overview
***Channel synchronization ensures goroutines coordinate safely and complete work in a predictable order***.


## Basic example
```go
package main

import (
	"fmt"
	"time"
)

func main() {

	done := make(chan bool)

	go func() {

		fmt.Println("Working..")
		time.Sleep(2 * time.Second)
		done <- true

	}()

	t := <-done
	fmt.Println(t, "Finished")

}

```

### MULTIPLE GO ROUTINES AND ENSURING ALL GOROUTINES ARE COMPLETE
```go
package main

import (
	"fmt"
	"time"
)

func main() {

	numGoRoutines := 5

	done := make(chan int, numGoRoutines)
	for v := 0; v < numGoRoutines; v++ {
		go func(id int) {
			time.Sleep(200 * time.Millisecond)
			fmt.Printf("Goroutine %d is executing....\n", id)
			done <- id
		}(v)
	}

	for i := 0; i < numGoRoutines; i++ {
		fmt.Println(<-done)

	}

	fmt.Println("All goroutines have been finished")

}

```
### SYNCHRONIZING DATA EXCHANGE

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	data := make(chan string)

	go func() {
		for i := 0; i < 5; i++ {
			data <- fmt.Sprintf("hello%d", i)
			time.Sleep(200 * time.Millisecond)
		}
		close(data)

	}()

	for value := range data {
		fmt.Println("Data received", value, ":", time.Now())
	}
}
```

## Key Points
- Use channels to signal completion (`done <- true`) and pass results.
- Buffered channels are useful when collecting results from multiple goroutines.
- Close channels from the sender side only, after all sends are done.

## Related Notes

[[1 - Goroutines]]
[[2 - Channels]]
[[3 - Unbuffered Channels]]
[[4 - Buffered Channels]]