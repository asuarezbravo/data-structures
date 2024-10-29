
# 5.1 Hash Tables

## What is a Hash Table?

A **hash table** is a data structure that stores key-value pairs. It uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found. Hash tables are used for fast data retrieval and are widely used in database indexing, caching, and associative arrays.

### How Hashing Works

1. **Key**: The unique identifier for data.
2. **Hash Function**: Converts the key into an integer index.
3. **Collision**: Occurs when two keys hash to the same index.

### Basic Operations

1. **Insert**: Add a new key-value pair to the table.
2. **Search**: Find a value using its key.
3. **Delete**: Remove a key-value pair from the table.

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

---

[Continue to 5.2 Collision Resolution Techniques](./5_2_Collision_Resolution_Techniques.md)
