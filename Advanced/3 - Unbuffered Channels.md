# 3 - Un-buffered Channels

Tags: #go #advanced #channels 


## Overview
Un-buffered channels look for immediate receiver hence cannot be used in the main function as they message is received in the next line



## Code Example

```Go
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
- The receiver waits for all of the go routine to finish and  then assumes that channel would send a value to it by the channel
## Related Notes

[[1 - Goroutines]]
[[2 - Channels]]
[[4 - Buffered Channels]]
