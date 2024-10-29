
# 6.4 Segment Trees and Fenwick Trees

## Segment Trees

A **segment tree** is a tree data structure that allows answering range queries and updating elements efficiently. Segment trees are often used for operations like finding the sum or minimum of elements in a range.

### Basic Operations and Complexity for Segment Trees

| Operation   | Description                               | Time Complexity | Space Complexity |
|-------------|-------------------------------------------|-----------------|------------------|
| Build       | Construct the segment tree                | O(n)            | O(n)             |
| Update      | Update an element in the segment tree     | O(log n)        | O(log n)         |
| Query       | Query a range of elements                 | O(log n)        | O(log n)         |

### Example in Go: Segment Tree for Range Sum

```go
package main

import "fmt"

type SegmentTree struct {
    tree []int
    arr  []int
}

func NewSegmentTree(arr []int) *SegmentTree {
    size := len(arr) * 4
    tree := make([]int, size)
    st := &SegmentTree{tree: tree, arr: arr}
    st.build(0, 0, len(arr)-1)
    return st
}

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

## Fenwick Trees (Binary Indexed Trees)

A **Fenwick Tree** (or Binary Indexed Tree) is a data structure that also allows efficient range queries and updates but is simpler to implement than a segment tree.

### Basic Operations and Complexity for Fenwick Trees

| Operation   | Description                               | Time Complexity | Space Complexity |
|-------------|-------------------------------------------|-----------------|------------------|
| Update      | Increase or decrease an element           | O(log n)        | O(n)             |
| Query       | Compute prefix sums up to a certain index | O(log n)        | O(n)             |

### Example in Go: Fenwick Tree for Range Sum

```go
package main

import "fmt"

type FenwickTree struct {
    tree []int
}

func NewFenwickTree(size int) *FenwickTree {
    return &FenwickTree{tree: make([]int, size+1)}
}

func (ft *FenwickTree) Update(index, value int) {
    for index < len(ft.tree) {
        ft.tree[index] += value
        index += index & -index
    }
}

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

### Advantages of Segment Trees and Fenwick Trees

- **Efficient Range Queries**: Both structures provide efficient ways to calculate and update range queries.
- **Dynamic Updates**: They allow dynamic updates to individual elements without needing to rebuild the entire structure.

### Limitations

- **Space Overhead**: Segment trees, in particular, require more space for efficient operation.
- **Complexity in Implementation**: Both trees are more complex to implement than basic data structures.

---

[Continue to 7.1 Choosing the Right Data Structure](./7_1_Choosing_the_Right_Data_Structure.md)
