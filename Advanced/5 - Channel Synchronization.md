# 5 - Channel Synchronization

Tags: #go #advanced #channels 


## Overview
***It ensures that data is properly exchanged between Goroutines. It coordinates the execution flow to avoid race conditions and ensure predictable behavior***


## Basic example
```Go
func main() {

	done := make(chan bool)
	
	
	go func() {
	
		fmt.Println("Working..")
		time.Sleep(2 * time.Second)
		done <- true
	
	}()
	
	t := <-done
	fmt.Println(t,"Finished")

}

```

### MULTIPLE GO ROUTINES AND ENSURING ALL GOROUTINES ARE COMPLETE
```Go
func main() {

	numGoRoutines := 5
	
	done := make(chan int, 5)
	for v := range numGoRoutines {
		time.Sleep(2*time.Second)
		go func(id int) {
			fmt.Printf("Goroutine %d is executing....\n",id)
			done <- id
		}(v)
	}
	
	for range numGoRoutines {
	
		fmt.Println(<-done)
	
	}
	
	fmt.Println("All goroutines have been finished")

}

```
### SYNCHRONIZING DATA EXCHANGE

```Go
func main() {
	data := make(chan string)
	
	go func() {
		for i := range 5 {		
			data <- fmt.Sprintf("hello%d", i)
			time.Sleep(2 * time.Second)
		}
		close(data)
	
	}()
	
	for value := range data {
		fmt.Println("Data receviced", value, ":",time.Now())
	}
}
```

## Key Points
- It helps the *life cycle* of Go routines and completion of tasks.
- A channel should be closed once all of the expected data has been put into the channel.
## Related Notes