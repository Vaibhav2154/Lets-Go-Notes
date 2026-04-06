# Go-routines in Go

Tags: #go #advanced #goroutines 


## Overview

Go routines are **light weight threads** handled by the go runtime scheduler. They are usually used for high concurrency in go programming. 

## Code Example

```Go
package main

import (
	"fmt"
	"time"
)

func main() {
	var err error

	fmt.Println("Start of the program")

	go sayHello()

	fmt.Println("After the say hello function")

	func() {
		err = doWork()
	}()

	go printNumbers()
	go printAlphabets()

	if err != nil {
		fmt.Println("An error occured")
	} else {
		fmt.Println("Do work completed properly")
	}

	time.Sleep(2 * time.Second)
}

func sayHello() {
	fmt.Println("Before Saying hello")

	time.Sleep(1 * time.Second)

	fmt.Println("Saying hello")
}

func printNumbers() {
	for i := 0; i < 5; i++ {
		fmt.Println("Number", i, time.Now())
		time.Sleep(100 * time.Millisecond)
	}
}

func printAlphabets() {
	for _, number := range "abcde" {
		fmt.Println("Alphabet", string(number), time.Now())
		time.Sleep(200 * time.Millisecond)
	}
}

func doWork() error {
	time.Sleep(1 * time.Second)
	return fmt.Errorf("An error occured in the do work")
}
```


## Key Points

- They are functions that leaves the main thread and run in the background and come back to join the main thread once the functions are finished to return any value
- They don't stop the program flow, they are non blocking
- Uses M:N Scheduling model.
- Should avoid goroutine leaks when used and shouldn't create many goroutines to prevent excessive resource consumptions

## Related Topics
[[2- Channels]]

