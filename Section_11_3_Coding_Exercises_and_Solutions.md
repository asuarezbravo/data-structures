
# 11.3 Coding Exercises and Solutions

This section includes a set of practice problems for each type of data structure covered in this guide. Each exercise includes a description, followed by a solution implemented in Go.

## Array Exercises

### Exercise 1: Reverse an Array

**Problem**: Write a function that takes an array of integers and returns a new array with elements in reverse order.

#### Solution

```go
package main

import "fmt"

func reverseArray(arr []int) []int {
    n := len(arr)
    result := make([]int, n)
    for i := 0; i < n; i++ {
        result[i] = arr[n-i-1]
    }
    return result
}

func main() {
    arr := []int{1, 2, 3, 4, 5}
    fmt.Println("Reversed array:", reverseArray(arr))
}
```

### Exercise 2: Find the Maximum Element in an Array

**Problem**: Write a function that finds the maximum element in an integer array.

#### Solution

```go
package main

import "fmt"

func findMax(arr []int) int {
    max := arr[0]
    for _, num := range arr {
        if num > max {
            max = num
        }
    }
    return max
}

func main() {
    arr := []int{10, 20, 30, 5, 25}
    fmt.Println("Maximum element:", findMax(arr))
}
```

---

## Linked List Exercises

### Exercise 1: Remove Duplicates from a Linked List

**Problem**: Write a function to remove duplicate values from a linked list.

#### Solution

```go
package main

import "fmt"

type Node struct {
    data int
    next *Node
}

type LinkedList struct {
    head *Node
}

func (list *LinkedList) Insert(data int) {
    newNode := &Node{data: data}
    newNode.next = list.head
    list.head = newNode
}

func (list *LinkedList) RemoveDuplicates() {
    current := list.head
    for current != nil && current.next != nil {
        if current.data == current.next.data {
            current.next = current.next.next
        } else {
            current = current.next
        }
    }
}

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
    list.Insert(3)
    list.Insert(3)
    list.Insert(2)
    list.Insert(1)
    list.Insert(1)
    fmt.Println("Before removing duplicates:")
    list.Display()

    list.RemoveDuplicates()
    fmt.Println("After removing duplicates:")
    list.Display()
}
```

---

## Stack Exercises

### Exercise 1: Check for Balanced Parentheses

**Problem**: Write a function that uses a stack to check if a string containing parentheses is balanced.

#### Solution

```go
package main

import "fmt"

func isBalanced(s string) bool {
    stack := []rune{}
    for _, char := range s {
        if char == '(' {
            stack = append(stack, char)
        } else if char == ')' {
            if len(stack) == 0 {
                return false
            }
            stack = stack[:len(stack)-1]
        }
    }
    return len(stack) == 0
}

func main() {
    fmt.Println("Is balanced ("(())"): ", isBalanced("(())"))
    fmt.Println("Is balanced ("(()"): ", isBalanced("(()"))
}
```

---

## Queue Exercises

### Exercise 1: Implement a Queue Using Two Stacks

**Problem**: Implement a queue using two stacks.

#### Solution

```go
package main

import "fmt"

type Queue struct {
    stack1 []int
    stack2 []int
}

func (q *Queue) Enqueue(x int) {
    q.stack1 = append(q.stack1, x)
}

func (q *Queue) Dequeue() int {
    if len(q.stack2) == 0 {
        for len(q.stack1) > 0 {
            top := q.stack1[len(q.stack1)-1]
            q.stack1 = q.stack1[:len(q.stack1)-1]
            q.stack2 = append(q.stack2, top)
        }
    }
    result := q.stack2[len(q.stack2)-1]
    q.stack2 = q.stack2[:len(q.stack2)-1]
    return result
}

func main() {
    q := Queue{}
    q.Enqueue(1)
    q.Enqueue(2)
    fmt.Println("Dequeue:", q.Dequeue())
    q.Enqueue(3)
    fmt.Println("Dequeue:", q.Dequeue())
}
```

---

## Hash Table Exercises

### Exercise 1: Find the First Non-Repeating Character

**Problem**: Write a function to find the first non-repeating character in a string.

#### Solution

```go
package main

import "fmt"

func firstNonRepeatingChar(s string) rune {
    charCount := make(map[rune]int)
    for _, char := range s {
        charCount[char]++
    }
    for _, char := range s {
        if charCount[char] == 1 {
            return char
        }
    }
    return ' '
}

func main() {
    fmt.Printf("First non-repeating character: %c
", firstNonRepeatingChar("swiss"))
}
```

---

## Tree Exercises

### Exercise 1: Find the Height of a Binary Tree

**Problem**: Write a function to calculate the height of a binary tree.

#### Solution

```go
package main

import "fmt"

type TreeNode struct {
    value int
    left  *TreeNode
    right *TreeNode
}

func findHeight(root *TreeNode) int {
    if root == nil {
        return 0
    }
    leftHeight := findHeight(root.left)
    rightHeight := findHeight(root.right)
    if leftHeight > rightHeight {
        return leftHeight + 1
    }
    return rightHeight + 1
}

func main() {
    root := &TreeNode{value: 1}
    root.left = &TreeNode{value: 2}
    root.right = &TreeNode{value: 3}
    root.left.left = &TreeNode{value: 4}
    root.left.right = &TreeNode{value: 5}
    fmt.Println("Height of the tree:", findHeight(root))
}
```

This section provides a variety of exercises for each type of data structure with solutions in Go, allowing readers to practice core concepts. 

