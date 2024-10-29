
# 3.4 Queues

## What is a Queue?

A **queue** is a linear data structure that follows the First-In, First-Out (FIFO) principle, meaning that the first element added is the first one removed. Queues are commonly used in scheduling tasks, managing print jobs, and handling requests in web servers.

### Basic Operations on Queues

1. **Enqueue**: Add an element to the end of the queue.
2. **Dequeue**: Remove an element from the front of the queue.
3. **Peek**: Retrieve the front element without removing it.

### Example in Go: Queue Implementation

```go
package main

import "fmt"

// Queue structure with a slice
type Queue struct {
    items []int
}

// Enqueue adds an item to the end of the queue
func (q *Queue) Enqueue(item int) {
    q.items = append(q.items, item)
}

// Dequeue removes an item from the front of the queue
func (q *Queue) Dequeue() int {
    if len(q.items) == 0 {
        fmt.Println("Queue is empty")
        return -1
    }
    item := q.items[0]
    q.items = q.items[1:]
    return item
}

// Peek returns the front item without removing it
func (q *Queue) Peek() int {
    if len(q.items) == 0 {
        fmt.Println("Queue is empty")
        return -1
    }
    return q.items[0]
}

func main() {
    queue := Queue{}
    queue.Enqueue(1)
    queue.Enqueue(2)
    fmt.Println("Front item:", queue.Peek())
    fmt.Println("Dequeued item:", queue.Dequeue())
    fmt.Println("Queue after dequeue:", queue.items)
}
```

In this example, the `Queue` struct uses a slice to manage items. The `Enqueue` method adds items to the end, and `Dequeue` removes the item from the front.

### Advantages of Queues

- **FIFO Order**: Ensures that the oldest element is processed first, ideal for scheduling and task management.
- **Efficient for Sequential Processing**: Useful in applications where data needs to be processed in the order it arrives.

### Limitations of Queues

- **Limited Access**: Only the front and back elements are accessible.
- **Memory Waste**: Static queues with fixed sizes can waste memory if not fully utilized.

---

[Continue to 4.1 Trees](./4_1_Trees.md)
