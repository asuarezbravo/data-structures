
# 5.1 Hash Tables

## What is a Hash Table?

A **hash table** is a data structure that stores key-value pairs. It uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found. Hash tables are used for fast data retrieval and are widely used in database indexing, caching, and associative arrays.

### How Hashing Works

1. **Key**: The unique identifier for data.
2. **Hash Function**: Converts the key into an integer index.
3. **Collision**: Occurs when two keys hash to the same index.

### Basic Operations and Complexity

| Operation   | Description                                  | Average Time Complexity | Worst-Case Time Complexity | Space Complexity |
|-------------|----------------------------------------------|-------------------------|----------------------------|------------------|
| Insert      | Add a key-value pair                         | O(1)                    | O(n) (in case of collisions)| O(n)             |
| Search      | Find a value by its key                      | O(1)                    | O(n)                        | O(n)             |
| Delete      | Remove a key-value pair                      | O(1)                    | O(n)                        | O(n)             |

*The worst-case complexity occurs when all elements hash to the same index, leading to chaining or probing.

### Example in Go: Basic Hash Table Using a Map

Go provides a built-in `map` type that works as a hash table.

```go
package main

import "fmt"

func main() {
    hashTable := make(map[string]int)

    // Insert values
    hashTable["Alice"] = 25
    hashTable["Bob"] = 30

    // Search for a value
    fmt.Println("Alice's age:", hashTable["Alice"])

    // Delete a value
    delete(hashTable, "Alice")
    fmt.Println("After deletion, Alice's age:", hashTable["Alice"]) // Returns 0, meaning no value
}
```

In this example, we create a hash table to store and retrieve values associated with unique keys.

### Advantages of Hash Tables

- **Fast Lookup**: Provides average constant-time complexity for search, insert, and delete.
- **Efficient for Large Datasets**: Ideal for associative data storage.

### Limitations of Hash Tables

- **Collisions**: Multiple keys may hash to the same index, requiring collision resolution.
- **Unordered Data**: Hash tables do not maintain order, so keys are not sorted.

---

[Continue to 5.2 Collision Resolution Techniques](./Section_5_2_Collision_Resolution_Techniques.md)
