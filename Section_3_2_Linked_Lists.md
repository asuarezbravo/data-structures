
# 3.2 Linked Lists

## What is a Linked List?

A **linked list** is a linear data structure in which each element is a separate object called a node. Each node contains data and a reference (or link) to the next node in the sequence. Linked lists are dynamic, allowing efficient insertion and deletion operations.

### Types of Linked Lists

1. **Singly Linked List**: Each node has a single link to the next node.
2. **Doubly Linked List**: Each node has links to both the next and previous nodes.
3. **Circular Linked List**: The last node links back to the first node, creating a circular chain.

### Basic Operations on Linked Lists

1. **Insertion**: Add a new node to the beginning, end, or specific position.
2. **Deletion**: Remove a node from the list.
3. **Traversal**: Access each node in the sequence.

### Example in Go: Singly Linked List

```go
package main

import "fmt"

// Node represents a single node in a linked list
type Node struct {
    data int
    next *Node
}

// LinkedList represents a singly linked list
type LinkedList struct {
    head *Node
}

// Insert adds a new node to the beginning of the list
func (list *LinkedList) Insert(data int) {
    newNode := &Node{data: data}
    newNode.next = list.head
    list.head = newNode
}

// Display prints all nodes in the list
func (list *LinkedList) Display() {
    current := list.head
    for current != nil {
        fmt.Printf("%d -> ", current.data)
        current = current.next
    }
    fmt.Println("nil")
}

func main() {
    list := LinkedList{}
    list.Insert(10)
    list.Insert(20)
    list.Insert(30)
    list.Display()
}
```

In this example, we create a singly linked list with nodes containing integers. The `Insert` function adds a new node at the beginning of the list, and the `Display` function prints all nodes.

### Advantages of Linked Lists

- **Dynamic Size**: Unlike arrays, linked lists can grow or shrink in size dynamically.
- **Efficient Insertions/Deletions**: Insertions and deletions are faster, especially at the beginning of the list.

### Limitations of Linked Lists

- **No Random Access**: Elements must be accessed sequentially, which can be slower than arrays for certain operations.
- **Memory Overhead**: Each node requires extra memory for the link.

---

[Continue to 3.3 Stacks](./3_3_Stacks.md)
