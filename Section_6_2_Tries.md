
# 6.2 Tries

## What is a Trie?

A **trie** (also known as a prefix tree) is a tree-like data structure used to store strings in a way that enables efficient searching, insertion, and retrieval of words or prefixes. Tries are commonly used in applications such as autocomplete and spell-checking.

### Basic Operations and Complexity

| Operation   | Description                                        | Time Complexity | Space Complexity |
|-------------|----------------------------------------------------|-----------------|------------------|
| Insert      | Add a word to the trie                             | O(m)            | O(m * n)         |
| Search      | Check if a word exists in the trie                 | O(m)            | O(1)             |
| Prefix Search | Check if any word in the trie starts with a prefix | O(m)          | O(1)             |
| Delete      | Remove a word from the trie                        | O(m)            | O(1)             |

* Here, **m** is the length of the word being inserted/searched, and **n** is the total number of words.

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

func NewTrie() *Trie {
    return &Trie{root: &TrieNode{children: make(map[rune]*TrieNode)}}
}

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
