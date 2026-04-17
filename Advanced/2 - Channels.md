# 2 - Channels

Tags: #go #advanced #channels


## Overview
Channels are used to synchronize the communication between the multiple go routines by passing values and other things.

## Code Example
```Go
package main

import (

"fmt"
"time"

)

func main() {

// variable := make(chan type)
greeting := make(chan string)
greetString := "Hello"


go func() {

	greeting <- greetString //
	greeting <- "Vaibhav" //

	for _, e := range "ABCDE" {
		greeting <- string(e)

	}
}()


  

go func() {

	reciever := <-greeting
	fmt.Println(reciever)

}()

go func() {

	reciever := <-greeting
	fmt.Println(reciever)

	for range 5 {

		reciever = <- greeting
		fmt.Println(reciever)

	}

}()

time.Sleep(100 * time.Microsecond)
}
```

## Key Points
- They are blocking because they continuously try to receive values, i.e. they are ready to receive continuous flow of data
- Main function/thread is also a go routine.
- It is usually used when there is a very large and continuous stream of data being passed from a sender.



## Related Notes

[[1 - Goroutines]]
[[3 - Unbuffered Channels]]
[[4 - Buffered Channels]]

