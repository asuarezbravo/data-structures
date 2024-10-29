
# 4.1 Trees

## What is a Tree?

A **tree** is a non-linear data structure that represents a hierarchy. Trees are composed of nodes, with each node containing data and a link to its child nodes. The topmost node is called the **root**, and nodes without children are called **leaf nodes**.

### Basic Terms

1. **Root**: The top node in the tree.
2. **Parent**: A node that has links to other nodes (children).
3. **Child**: A node that has a parent node above it.
4. **Leaf**: A node with no children.

### Types of Trees

1. **Binary Tree**: Each node has up to two children.
2. **Binary Search Tree (BST)**: A binary tree where the left child is less than the parent, and the right child is greater.

### Example in Go: Basic Binary Tree

```go
package main

import "fmt"

// TreeNode represents a single node in a binary tree
type TreeNode struct {
    value int
    left  *TreeNode
    right *TreeNode
}

// Insert adds a new node to the binary tree
func (node *TreeNode) Insert(value int) {
    if value < node.value {
        if node.left == nil {
            node.left = &TreeNode{value: value}
        } else {
            node.left.Insert(value)
        }
    } else {
        if node.right == nil {
            node.right = &TreeNode{value: value}
        } else {
            node.right.Insert(value)
        }
    }
}

// InOrder prints the values of nodes in in-order traversal
func (node *TreeNode) InOrder() {
    if node == nil {
        return
    }
    node.left.InOrder()
    fmt.Printf("%d ", node.value)
    node.right.InOrder()
}

func main() {
    root := &TreeNode{value: 10}
    root.Insert(5)
    root.Insert(15)
    root.Insert(8)
    fmt.Println("In-order traversal:")
    root.InOrder()
}
```

In this example, we define a binary tree with nodes and implement insertion and in-order traversal.

### Advantages of Trees

- **Hierarchical Structure**: Trees represent hierarchical data effectively, like folder structures.
- **Efficient Searching**: Binary search trees allow efficient searching and sorting.

### Limitations of Trees

- **Complexity**: Managing trees is more complex than linear data structures.
- **Memory Overhead**: Each node requires additional memory for pointers.

---

[Continue to 4.2 Graphs](./4_2_Graphs.md)
