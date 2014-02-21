Simple Queue
============

## USAGE

``` go
package main

import "github.com/dukex/squeue"
import "fmt"
import "time"

var QUEUE *squeue.Queue

func main() {
  QUEUE = squeue.NewQueue(2 * time.Second)
  QUEUE.Run()

  QUEUE.Push(func() {
    fmt.Println("first!")
  })
  QUEUE.Push(func() {
    fmt.Println("Hi")
  })
  QUEUE.Push(func() {
    fmt.Println("Hello!")
  })

  <-time.After(10 * time.Second)
}
```

Output every 2 second

```
first!
Hi
Hello!
```
