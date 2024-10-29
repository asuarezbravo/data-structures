
# 4.2 Graphs

## What is a Graph?

A **graph** is a non-linear data structure that consists of a set of nodes (also called vertices) and edges connecting these nodes. Graphs are used to represent relationships and connections in networks, such as social networks, maps, and recommendation systems.

### Basic Terminology

1. **Vertex (Node)**: A point in the graph.
2. **Edge**: A connection between two vertices.
3. **Directed Graph**: Edges have a direction (from one vertex to another).
4. **Undirected Graph**: Edges do not have a direction.

### Types of Graphs

1. **Directed Graph**: Edges have direction (like a one-way street).
2. **Undirected Graph**: Edges are bidirectional (like two-way streets).
3. **Weighted Graph**: Each edge has a weight, representing the cost or distance between vertices.

### Example in Go: Representing a Graph Using an Adjacency List

An **adjacency list** is a common way to represent graphs. Each vertex has a list of other vertices it is connected to.

```go
package main

import "fmt"

// Graph structure using adjacency list
type Graph struct {
    vertices map[int][]int
}

// AddVertex adds a new vertex to the graph
func (g *Graph) AddVertex(vertex int) {
    if g.vertices == nil {
        g.vertices = make(map[int][]int)
    }
    g.vertices[vertex] = []int{}
}

// AddEdge adds an edge between two vertices
func (g *Graph) AddEdge(v1, v2 int) {
    g.vertices[v1] = append(g.vertices[v1], v2)
    g.vertices[v2] = append(g.vertices[v2], v1) // For undirected graph
}

// Display prints the graph's adjacency list
func (g *Graph) Display() {
    for vertex, edges := range g.vertices {
        fmt.Printf("%d -> %v
", vertex, edges)
    }
}

func main() {
    graph := Graph{}
    graph.AddVertex(1)
    graph.AddVertex(2)
    graph.AddVertex(3)
    graph.AddEdge(1, 2)
    graph.AddEdge(1, 3)
    graph.Display()
}
```

In this example, we define a graph with vertices and edges and display the adjacency list.

### Advantages of Graphs

- **Representation of Complex Relationships**: Graphs are ideal for representing relationships in social networks, maps, and web link structures.
- **Flexible Structure**: Graphs can represent both simple and complex relationships.

### Limitations of Graphs

- **Complex Implementation**: Managing and traversing graphs can be complex.
- **Memory Usage**: Large graphs can consume significant memory, especially with dense connections.

---

[Continue to 5.1 Hash Tables](./5_1_Hash_Tables.md)
