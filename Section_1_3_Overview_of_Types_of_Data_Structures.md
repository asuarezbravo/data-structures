
# 1.3 Overview of Types of Data Structures

## Types of Data Structures

Data structures can be classified based on how they organize data and the types of operations they support. Here, we’ll look at the main categories of data structures:

1. **Linear Data Structures**
2. **Non-Linear Data Structures**
3. **Hashing**
4. **Advanced Data Structures**

Each type has specific uses and advantages, which we will explore in this section.

### 1. Linear Data Structures

In linear data structures, data elements are arranged in a sequential manner. These structures are simple and efficient for data traversal but may lack flexibility for complex relationships.

#### Examples:
- **Arrays**: A fixed-size, indexed collection of elements.
- **Linked Lists**: A dynamic structure with nodes that link to the next element.
- **Stacks**: A Last-In, First-Out (LIFO) structure.
- **Queues**: A First-In, First-Out (FIFO) structure.

### Example Code: Array in Go

```go
package main

import "fmt"

func main() {
    numbers := [3]int{10, 20, 30}
    fmt.Println("Array elements:", numbers)
}
```

### 2. Non-Linear Data Structures

Non-linear data structures allow complex relationships between elements. These structures are not sequential, and they enable efficient representation of hierarchical or interconnected data.

#### Examples:
- **Trees**: Structures with a root node and child nodes, representing hierarchical data.
- **Graphs**: Consist of nodes and edges, used to represent networks and connections.

### 3. Hashing

**Hashing** is a technique used to map data elements to a specific location in memory, allowing quick access to data. Hash tables use hashing to store key-value pairs, making retrieval fast and efficient.

### Example Code: Hash Table in Go

```go
package main

import "fmt"

func main() {
    hashTable := map[string]int{
        "Alice": 1,
        "Bob":   2,
        "Charlie": 3,
    }
    fmt.Println("Hash Table:", hashTable)
}
```

### 4. Advanced Data Structures

These structures, including heaps, tries, disjoint sets, and segment trees, handle specific types of data management or allow complex operations. They are often used in more specialized applications, like priority queues, string manipulation, and network analysis.

---

[Continue to 2.1 Abstract Data Types (ADTs)](./2_1_Abstract_Data_Types_ADTs.md)
