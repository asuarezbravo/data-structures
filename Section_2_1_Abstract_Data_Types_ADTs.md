
# 2.1 Abstract Data Types (ADTs)

## What is an Abstract Data Type (ADT)?

An **Abstract Data Type (ADT)** is a model that defines a data structure purely based on the operations it performs and the types of data it holds, without specifying the actual implementation. ADTs allow us to focus on *what* operations are available rather than *how* they are implemented.

### Common ADTs and Their Operations

1. **Stack ADT**: Follows a Last-In-First-Out (LIFO) principle. Common operations include:
   - **Push**: Add an element to the top.
   - **Pop**: Remove the top element.
2. **Queue ADT**: Follows a First-In-First-Out (FIFO) principle. Common operations include:
   - **Enqueue**: Add an element to the end.
   - **Dequeue**: Remove an element from the front.

### Example in Go: Stack ADT

Here's a simple example of a stack ADT in Go, using a struct and slice to manage the stack operations.

```go
package main

import "fmt"

type Stack struct {
    items []int
}

// Push adds an item to the stack
func (s *Stack) Push(item int) {
    s.items = append(s.items, item)
}

// Pop removes an item from the stack
func (s *Stack) Pop() int {
    if len(s.items) == 0 {
        fmt.Println("Stack is empty")
        return -1
    }
    item := s.items[len(s.items)-1]
    s.items = s.items[:len(s.items)-1]
    return item
}

func main() {
    stack := Stack{}
    stack.Push(10)
    stack.Push(20)
    fmt.Println("Popped item:", stack.Pop())
}
```

In this example, the `Stack` struct has `Push` and `Pop` methods that allow stack operations without exposing the internal data structure to the user.

---

[Continue to 2.2 Big O Notation and Complexity Analysis](./2_2_Big_O_Notation_and_Complexity_Analysis.md)
