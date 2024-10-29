
# 6.2 Tries

## What is a Trie?

A **trie** (also known as a prefix tree) is a tree-like data structure used to store strings in a way that enables efficient searching, insertion, and retrieval of words or prefixes. Tries are commonly used in applications such as autocomplete and spell-checking.

### Basic Trie Operations

1. **Insert**: Add a word to the trie.
2. **Search**: Check if a word exists in the trie.
3. **Prefix Search**: Check if any word in the trie starts with a given prefix.

### Example in Go: Simple Trie Implementation

```go
package main

import "fmt"

type TrieNode struct {
    children map[rune]*TrieNode
    isEnd    bool
}

type Trie struct {
    root *TrieNode
}

// NewTrie initializes a new Trie
func NewTrie() *Trie {
    return &Trie{root: &TrieNode{children: make(map[rune]*TrieNode)}}
}

// Insert adds a word to the Trie
func (t *Trie) Insert(word string) {
    node := t.root
    for _, char := range word {
        if _, exists := node.children[char]; !exists {
            node.children[char] = &TrieNode{children: make(map[rune]*TrieNode)}
        }
        node = node.children[char]
    }
    node.isEnd = true
}

// Search checks if a word is in the Trie
func (t *Trie) Search(word string) bool {
    node := t.root
    for _, char := range word {
        if _, exists := node.children[char]; !exists {
            return false
        }
        node = node.children[char]
    }
    return node.isEnd
}

func main() {
    trie := NewTrie()
    trie.Insert("hello")
    trie.Insert("world")

    fmt.Println("Search 'hello':", trie.Search("hello"))
    fmt.Println("Search 'world':", trie.Search("world"))
    fmt.Println("Search 'hell':", trie.Search("hell")) // False, as "hell" isn't inserted
}
```

In this example, we implement a simple trie with insertion and search functionality.

### Advantages of Tries

- **Efficient Prefix Search**: Tries allow fast retrieval of words with a given prefix.
- **Memory Efficient for Similar Words**: Words with common prefixes share nodes, saving space.

### Limitations of Tries

- **High Memory Usage for Sparse Data**: If words have few common prefixes, tries can use a lot of memory.
- **Complex Implementation**: Tries are more complex to implement compared to basic data structures.

---

[Continue to 6.3 Disjoint Set](./6_3_Disjoint_Set.md)
