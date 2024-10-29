
# 6.1 Heaps

## What is a Heap?

A **heap** is a specialized tree-based data structure that satisfies the heap property:
- In a **max-heap**, the parent node is greater than or equal to its children.
- In a **min-heap**, the parent node is less than or equal to its children.

Heaps are commonly used in priority queues and algorithms like heapsort.

### Basic Operations and Complexity

| Operation   | Description                                    | Time Complexity | Space Complexity |
|-------------|------------------------------------------------|-----------------|------------------|
| Insert      | Add a new element to the heap                  | O(log n)        | O(1)             |
| Remove      | Remove the root (highest/lowest) element       | O(log n)        | O(1)             |
| Peek        | Retrieve the root element without removing it  | O(1)            | O(1)             |
| Build Heap  | Create a heap from an unsorted array           | O(n)            | O(1)             |

### Example in Go: Min-Heap Using the Container/Heap Package

Go's `container/heap` package provides a heap interface that we can use to implement a min-heap.

```go
package main

import (
    "container/heap"
    "fmt"
)

type IntHeap []int

func (h IntHeap) Len() int           { return len(h) }
func (h IntHeap) Less(i, j int) bool { return h[i] < h[j] }
func (h IntHeap) Swap(i, j int)      { h[i], h[j] = h[j], h[i] }

func (h *IntHeap) Push(x interface{}) {
    *h = append(*h, x.(int))
}

func (h *IntHeap) Pop() interface{} {
    old := *h
    n := len(old)
    x := old[n-1]
    *h = old[0 : n-1]
    return x
}

func main() {
    h := &IntHeap{2, 1, 5}
    heap.Init(h)
    heap.Push(h, 3)
    fmt.Println("Minimum:", (*h)[0])
    fmt.Println("Popped minimum:", heap.Pop(h))
}
```

In this example, `IntHeap` implements a min-heap by defining methods for pushing, popping, and comparing elements.

### Advantages of Heaps

- **Efficient Access to Extremes**: Heaps provide efficient access to the smallest (min-heap) or largest (max-heap) element.
- **Useful in Priority Queues**: Commonly used for managing priority-based tasks.

### Limitations of Heaps

- **Limited Use Cases**: Heaps are primarily used for specific scenarios like priority queues and sorting.

---

[Continue to 6.2 Tries](./6_2_Tries.md)
