# Data Structures — Introduction

> A high-level map of data structures every software engineer must know, plus time/space complexity — the foundation for DSA interview prep.

---

## 1. What is a Data Structure?

A way of organizing and storing data so it can be accessed and modified efficiently. Choosing the right data structure is critical for writing performant software.

---

## 2. Time & Space Complexity (Big-O Notation)

Big-O describes how an algorithm's runtime/space grows as input size (`n`) grows.

| Notation | Name | Example |
|---|---|---|
| O(1) | Constant | Array index access |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Loop through array |
| O(n log n) | Linearithmic | Merge sort, Quick sort (avg) |
| O(n²) | Quadratic | Nested loops, Bubble sort |
| O(2ⁿ) | Exponential | Recursive Fibonacci (naive) |
| O(n!) | Factorial | Permutations |

**Rule of thumb:** Drop constants and lower-order terms. `O(2n + 5)` → `O(n)`.

---

## 3. Linear Data Structures

### 3.1 Array
Fixed-size, contiguous memory, indexed access.

| Operation | Time Complexity |
|---|---|
| Access | O(1) |
| Search | O(n) |
| Insert/Delete (end) | O(1) |
| Insert/Delete (middle) | O(n) |

### 3.2 Linked List
Nodes connected via pointers; dynamic size.

| Type | Description |
|---|---|
| Singly Linked List | Each node points to the next |
| Doubly Linked List | Each node points to next and previous |
| Circular Linked List | Last node points back to the first |

| Operation | Time Complexity |
|---|---|
| Access | O(n) |
| Insert/Delete (at head) | O(1) |
| Search | O(n) |

**Array vs Linked List:**
| Array | Linked List |
|---|---|
| Fixed size (mostly) | Dynamic size |
| Fast random access O(1) | Slow access O(n) |
| Costly insert/delete in middle | Fast insert/delete (if node known) |

### 3.3 Stack (LIFO — Last In, First Out)
Operations: `push()`, `pop()`, `peek()` — all O(1)

**Use cases:** Undo functionality, expression evaluation, backtracking, function call stack (recursion)

### 3.4 Queue (FIFO — First In, First Out)
Operations: `enqueue()`, `dequeue()` — O(1)

**Types:**
- Simple Queue
- Circular Queue
- Priority Queue (dequeues based on priority, not order)
- Deque (Double-Ended Queue) – insert/remove from both ends

**Use cases:** Task scheduling, BFS traversal, print queues, message queues

---

## 4. Non-Linear Data Structures

### 4.1 Trees
Hierarchical structure with a root node and child nodes.

| Type | Description |
|---|---|
| **Binary Tree** | Each node has at most 2 children |
| **Binary Search Tree (BST)** | Left child < parent < right child |
| **AVL Tree** | Self-balancing BST |
| **Heap** | Complete binary tree; Min-Heap or Max-Heap |
| **Trie** | Tree for storing strings (prefix-based lookup) |

#### BST Operations
| Operation | Average | Worst Case (unbalanced) |
|---|---|---|
| Search | O(log n) | O(n) |
| Insert | O(log n) | O(n) |
| Delete | O(log n) | O(n) |

#### Tree Traversals
```
Inorder   (Left → Root → Right)  → sorted order in BST
Preorder  (Root → Left → Right)  → used to copy a tree
Postorder (Left → Right → Root)  → used to delete a tree
Level Order (BFS, level by level)
```

### 4.2 Heap
A complete binary tree used to implement **Priority Queues**.

- **Min-Heap** – smallest element at root
- **Max-Heap** – largest element at root

| Operation | Time Complexity |
|---|---|
| Insert | O(log n) |
| Extract Min/Max | O(log n) |
| Peek | O(1) |

**Use cases:** Priority scheduling, Dijkstra's algorithm, heap sort, top-K problems

### 4.3 Graph
A set of nodes (vertices) connected by edges — models relationships/networks.

| Type | Description |
|---|---|
| Directed | Edges have direction |
| Undirected | Edges have no direction |
| Weighted | Edges have a cost/weight |
| Cyclic/Acyclic | Contains cycles or not |

**Representations:**
- **Adjacency Matrix** – O(V²) space, O(1) edge lookup
- **Adjacency List** – O(V + E) space, efficient for sparse graphs

**Traversals:**
- **BFS (Breadth-First Search)** – level by level, uses a Queue
- **DFS (Depth-First Search)** – goes deep first, uses a Stack/recursion

**Common Graph Algorithms:**
| Algorithm | Purpose |
|---|---|
| Dijkstra's | Shortest path (non-negative weights) |
| Bellman-Ford | Shortest path (handles negative weights) |
| Kruskal's / Prim's | Minimum Spanning Tree |
| Topological Sort | Ordering of DAG (Directed Acyclic Graph) |
| Union-Find | Detect cycles, connected components |

### 4.4 Hash Table (Hash Map)
Stores key-value pairs using a **hash function** for near O(1) access.

| Operation | Average | Worst Case |
|---|---|---|
| Insert | O(1) | O(n) |
| Search | O(1) | O(n) |
| Delete | O(1) | O(n) |

**Collision Handling:**
- **Chaining** – store colliding elements in a linked list at that index
- **Open Addressing** – find next available slot (linear/quadratic probing)

**Use cases:** Caching, database indexing, counting frequencies, de-duplication

---

## 5. Choosing the Right Data Structure

| Need | Use |
|---|---|
| Fast lookups by key | Hash Map |
| Maintain order + fast access | Array / ArrayList |
| Frequent insert/delete at ends | Deque / Linked List |
| Sorted data with fast search | BST / Balanced Tree |
| Get min/max repeatedly | Heap |
| Model relationships/networks | Graph |
| LIFO behavior | Stack |
| FIFO behavior | Queue |
| Prefix-based string search | Trie |

---

## 6. Quick Revision Summary

- Big-O measures scalability, not raw speed
- Arrays = fast access, slow insert/delete; Linked Lists = opposite
- Stack = LIFO, Queue = FIFO
- BST enables O(log n) search when balanced
- Heaps power priority queues; Graphs model networks
- Hash Maps give near O(1) lookups but need good hash functions to avoid collisions

---

## 7. Interview-Style Questions

1. What is the time complexity of searching in a balanced BST vs an unbalanced one?
2. Explain the difference between BFS and DFS, and when you'd use each.
3. How does a hash table handle collisions?
4. Why is a heap used for priority queues instead of a sorted array?
5. Explain the difference between an adjacency list and an adjacency matrix.
6. When would you use a linked list over an array?
7. What is the difference between a Trie and a BST?

---

**Previous file ←** `dbms-basics.md`
**Next file →** `system-design-basics.md`
