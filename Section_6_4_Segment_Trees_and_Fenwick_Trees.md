
# 6.4 Segment Trees and Fenwick Trees

## Segment Trees

A **segment tree** is a tree data structure that allows answering range queries and updating elements efficiently. Segment trees are often used for operations like finding the sum or minimum of elements in a range.

### Basic Operations on Segment Trees

1. **Build**: Construct the segment tree based on an initial array.
2. **Query**: Retrieve information (like sum or minimum) for a range of elements.
3. **Update**: Modify an element and update the tree to reflect the change.

### Example in Go: Segment Tree for Range Sum

```go
package main

import "fmt"

type SegmentTree struct {
    tree []int
    arr  []int
}

// NewSegmentTree initializes the segment tree with an array
func NewSegmentTree(arr []int) *SegmentTree {
    size := len(arr) * 4
    tree := make([]int, size)
    st := &SegmentTree{tree: tree, arr: arr}
    st.build(0, 0, len(arr)-1)
    return st
}

// build constructs the segment tree
func (st *SegmentTree) build(node, start, end int) {
    if start == end {
        st.tree[node] = st.arr[start]
    } else {
        mid := (start + end) / 2
        st.build(2*node+1, start, mid)
        st.build(2*node+2, mid+1, end)
        st.tree[node] = st.tree[2*node+1] + st.tree[2*node+2]
    }
}

// Query range sum
func (st *SegmentTree) Query(l, r, node, start, end int) int {
    if start > r || end < l {
        return 0
    }
    if l <= start && end <= r {
        return st.tree[node]
    }
    mid := (start + end) / 2
    leftSum := st.Query(l, r, 2*node+1, start, mid)
    rightSum := st.Query(l, r, 2*node+2, mid+1, end)
    return leftSum + rightSum
}

func main() {
    arr := []int{1, 3, 5, 7, 9, 11}
    st := NewSegmentTree(arr)
    fmt.Println("Sum of range (1, 3):", st.Query(1, 3, 0, 0, len(arr)-1))
}
```

In this example, we build a segment tree for range sum queries.

## Fenwick Trees (Binary Indexed Trees)

A **Fenwick Tree** (or Binary Indexed Tree) is a data structure that also allows efficient range queries and updates but is simpler to implement than a segment tree.

### Basic Operations on Fenwick Trees

1. **Update**: Increase or decrease an element.
2. **Query**: Compute prefix sums up to a certain index.

### Example in Go: Fenwick Tree for Range Sum

```go
package main

import "fmt"

type FenwickTree struct {
    tree []int
}

// NewFenwickTree initializes a Fenwick Tree
func NewFenwickTree(size int) *FenwickTree {
    return &FenwickTree{tree: make([]int, size+1)}
}

// Update adds value to an element
func (ft *FenwickTree) Update(index, value int) {
    for index < len(ft.tree) {
        ft.tree[index] += value
        index += index & -index
    }
}

// Query returns the prefix sum up to index
func (ft *FenwickTree) Query(index int) int {
    sum := 0
    for index > 0 {
        sum += ft.tree[index]
        index -= index & -index
    }
    return sum
}

func main() {
    ft := NewFenwickTree(6)
    ft.Update(1, 1)
    ft.Update(2, 3)
    ft.Update(3, 5)
    fmt.Println("Prefix sum up to index 3:", ft.Query(3))
}
```

In this example, we demonstrate the use of a Fenwick Tree to calculate prefix sums efficiently.

---

[Continue to 7.1 Choosing the Right Data Structure](./7_1_Choosing_the_Right_Data_Structure.md)
