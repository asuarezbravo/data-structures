
# 6.3 Disjoint Set

## What is a Disjoint Set?

A **disjoint set** (also known as union-find) is a data structure that keeps track of a set of elements partitioned into multiple non-overlapping subsets. Disjoint sets are useful in cases where we need to manage and track connections between items, such as in network connectivity and Kruskal’s algorithm for finding minimum spanning trees.

### Basic Operations and Complexity

| Operation   | Description                          | Time Complexity (With Path Compression and Union by Rank) |
|-------------|--------------------------------------|----------------------------------------------------------|
| Find        | Determine which subset an element belongs to | O(α(n))           |
| Union       | Join two subsets into a single subset        | O(α(n))           |

* α(n) is the Inverse Ackermann function, which grows very slowly, making these operations nearly constant time.

### Example in Go: Disjoint Set with Union by Rank and Path Compression

```go
package main

import "fmt"

type DisjointSet struct {
    parent []int
    rank   []int
}

func NewDisjointSet(size int) *DisjointSet {
    ds := &DisjointSet{
        parent: make([]int, size),
        rank:   make([]int, size),
    }
    for i := range ds.parent {
        ds.parent[i] = i
    }
    return ds
}

func (ds *DisjointSet) Find(x int) int {
    if ds.parent[x] != x {
        ds.parent[x] = ds.Find(ds.parent[x])
    }
    return ds.parent[x]
}

func (ds *DisjointSet) Union(x, y int) {
    rootX := ds.Find(x)
    rootY := ds.Find(y)
    if rootX != rootY {
        if ds.rank[rootX] > ds.rank[rootY] {
            ds.parent[rootY] = rootX
        } else if ds.rank[rootX] < ds.rank[rootY] {
            ds.parent[rootX] = rootY
        } else {
            ds.parent[rootY] = rootX
            ds.rank[rootX]++
        }
    }
}

func main() {
    ds := NewDisjointSet(5)
    ds.Union(0, 1)
    ds.Union(1, 2)
    fmt.Println("Are 0 and 2 connected?", ds.Find(0) == ds.Find(2))
    fmt.Println("Are 0 and 3 connected?", ds.Find(0) == ds.Find(3))
}
```

In this example, we use union by rank and path compression to optimize `Find` and `Union` operations.

### Advantages of Disjoint Sets

- **Efficient for Dynamic Connectivity**: Useful in tracking connected components in a network.
- **Optimized Operations**: With path compression and union by rank, operations are nearly constant time.

### Limitations of Disjoint Sets

- **Limited Use Cases**: Mostly applicable in network connectivity and clustering scenarios.

---

[Continue to 6.4 Segment Trees and Fenwick Trees](./6_4_Segment_Trees_and_Fenwick_Trees.md)
