
# 2.3 Recursion and Iteration

## What is Recursion?

**Recursion** is a programming technique where a function calls itself to solve a problem. Recursion is often used for tasks that can be divided into similar subtasks. A recursive function has a base case (to stop the recursion) and a recursive case (where the function calls itself).

### Example in Go: Recursive Factorial Calculation

```go
package main

import "fmt"

// Recursive factorial function
func factorial(n int) int {
    if n == 0 {
        return 1
    }
    return n * factorial(n-1)
}

func main() {
    fmt.Println("Factorial of 5:", factorial(5))
}
```

In this example, the `factorial` function calls itself to calculate the factorial of a number. The base case is `n == 0`, which returns 1 and stops the recursion.

## What is Iteration?

**Iteration** is a repetitive control structure that loops over a block of code until a condition is met. Unlike recursion, iteration does not involve function calls and typically uses loops (like `for` and `while`) to repeat operations.

### Example in Go: Iterative Factorial Calculation

```go
package main

import "fmt"

// Iterative factorial function
func factorial(n int) int {
    result := 1
    for i := 1; i <= n; i++ {
        result *= i
    }
    return result
}

func main() {
    fmt.Println("Factorial of 5:", factorial(5))
}
```

In this example, the factorial is calculated by looping through the values from 1 to `n` and multiplying them, without using function calls.

## Comparing Recursion and Iteration

- **Recursion**: May use more memory due to function call stack but can make code simpler for certain problems (like tree traversals).
- **Iteration**: Generally more memory-efficient but can be less intuitive for recursive-like problems.

---

[Continue to 3.1 Arrays](./Section_3_1_Arrays.md)
