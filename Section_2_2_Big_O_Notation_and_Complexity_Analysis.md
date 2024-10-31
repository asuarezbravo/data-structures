
# 2.2 Big O Notation and Complexity Analysis

## What is Big O Notation?

**Big O Notation** is a mathematical concept used to describe the performance or complexity of an algorithm. It provides an upper bound on the time or space an algorithm takes relative to the size of its input.

### Common Time Complexities

1. **O(1)**: Constant time. The algorithm takes the same amount of time regardless of input size.
2. **O(n)**: Linear time. The algorithm’s time grows linearly with the input size.
3. **O(log n)**: Logarithmic time. Time grows logarithmically as input size increases, common in search algorithms like binary search.
4. **O(n^2)**: Quadratic time. The time grows proportionally to the square of the input size, often seen in algorithms with nested loops.

### Example: Linear vs. Quadratic Complexity in Go

Here’s a comparison of a linear algorithm (O(n)) and a quadratic algorithm (O(n^2)) using a simple Go program.

```go
package main

import "fmt"

// Linear time complexity O(n)
func linearSum(n int) int {
    sum := 0
    for i := 0; i < n; i++ {
        sum += i
    }
    return sum
}

// Quadratic time complexity O(n^2)
func quadraticSum(n int) int {
    sum := 0
    for i := 0; i < n; i++ {
        for j := 0; j < n; j++ {
            sum += i + j
        }
    }
    return sum
}

func main() {
    fmt.Println("Linear sum:", linearSum(100))
    fmt.Println("Quadratic sum:", quadraticSum(100))
}
```

In this example:
- The `linearSum` function has a time complexity of O(n) as it iterates over the input size once.
- The `quadraticSum` function has a time complexity of O(n^2) due to nested loops iterating over the input.

---

[Continue to 2.3 Recursion and Iteration](./Section_2_3_Recursion_and_Iteration.md)
