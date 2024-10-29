
# 5.2 Collision Resolution Techniques

## What is a Collision in a Hash Table?

In a hash table, a **collision** occurs when two keys hash to the same index. When this happens, a collision resolution technique is needed to handle storing multiple values at the same index without losing data.

### Common Collision Resolution Techniques

1. **Chaining**: Each slot in the hash table points to a list of items that share the same hash.
2. **Open Addressing**: If a collision occurs, another slot is searched following a probing sequence.

### Chaining Example in Go

Chaining stores multiple elements in the same index by using a linked list or another structure at each position.

```go
package main

import "fmt"

type HashTable struct {
    table map[int][]string
}

// Insert adds an element to the hash table
func (h *HashTable) Insert(key int, value string) {
    index := key % 10
    h.table[index] = append(h.table[index], value)
}

// Display shows all items in the hash table
func (h *HashTable) Display() {
    for index, values := range h.table {
        fmt.Printf("Index %d: %v
", index, values)
    }
}

func main() {
    hashTable := HashTable{table: make(map[int][]string)}
    hashTable.Insert(1, "Alice")
    hashTable.Insert(11, "Bob") // Collides with Alice
    hashTable.Display()
}
```

In this example, both `Alice` and `Bob` hash to the same index, and chaining allows both values to be stored.

### Open Addressing Example in Go

Open addressing finds the next available slot in case of a collision.

#### Linear Probing

```go
package main

import "fmt"

type HashTableOpen struct {
    table []string
}

// Insert adds an element to the hash table using linear probing
func (h *HashTableOpen) Insert(key int, value string) {
    index := key % len(h.table)
    for h.table[index] != "" {
        index = (index + 1) % len(h.table)
    }
    h.table[index] = value
}

func (h *HashTableOpen) Display() {
    for i, value := range h.table {
        fmt.Printf("Index %d: %s
", i, value)
    }
}

func main() {
    hashTable := HashTableOpen{table: make([]string, 10)}
    hashTable.Insert(1, "Alice")
    hashTable.Insert(11, "Bob") // Uses probing to find next slot
    hashTable.Display()
}
```

Here, `Alice` and `Bob` collide, and linear probing finds the next open slot for `Bob`.

---

[Continue to 6.1 Heaps](./6_1_Heaps.md)
