Patterns

- sliding window pattern
- subset pattern -> no reptttion and repetttion
- Modified binary search
- top k elements -> use heap
- binary tree dfs
- toplogical sort
- two pointer
  - two moving pointer at diff speed
  - two are in same direction
  - Opposite direction
- prefix sum
- Linkindeni inplace reverse
- monotonic stock
- interval or range are overlap
  - find interval and etc
- backtracking
- dynamic programming
- priorty queue

1. Fast and Slow Pointer

- Cycle detection method
- O(1) space efficiency
- Linked list problems

1. Merge Intervals

- Sort and merge
- O(n log n) complexity
- Overlapping interval handling

1. Sliding Window

- Fixed/variable window
- O(n) time optimization
- Subarray/substring problems

1. Islands (Matrix Traversal)

- DFS/BFS traversal
- Connected component detection
- 2D grid problems

1. Two Pointers

- Dual pointer strategy
- Linear time complexity
- Array/list problems

1. Cyclic Sort

- Sorting in cycles
- O(n) time complexity
- Constant space usage

1. In-place Reversal of Linked List

- Reverse without extra space
- O(n) time efficiency
- Pointer manipulation technique

1. Breadth First Search

- Level-by-level traversal
- Uses queue structure
- Shortest path problems

1. Depth First Search

- Recursive/backtracking approach
- Uses stack (or recursion)
- Tree/graph traversal

1.  Two Heaps

- Max and min heaps
- Median tracking efficiently
- O(log n) insertions

1.  Subsets

- Generate all subsets
- Recursive or iterative
- Backtracking or bitmasking

1.  Modified Binary Search

- Search in variations
- O(log n) time
- Rotated/specialized arrays

1.  Bitwise XOR

- Toggle bits operation
- O(1) space complexity
- Efficient for pairing

1.  Top 'K' elements

- Use heap/quickselect
- O(n log k) time
- Efficient selection problem

1.  K-way Merge

- Merge sorted lists
- Min-heap based approach
- O(n log k) complexity

1.  0/1 Knapsack (Dynamic Programming)

- Choose or skip items
- O(n \* W) complexity
- Maximize value selection

1.  Unbounded Knapsack (Dynamic Programming)

- Unlimited item choices
- O(n \* W) complexity
- Multiple item selection

1.  Topological Sort (Graphs)

- Directed acyclic graph
- Order dependency resolution
- Uses DFS or BFS

1.  Monotonic Stack

- Maintain increasing/decreasing stack
- Optimized for range queries
- O(n) time complexity

1.  Backtracking

- Recursive decision-making
- Explore all possibilities
- Pruning with constraints

1.  Union Find

- Track and merge connected components
- Used for disjoint sets
- Great for network connectivity

1.  Greedy Algorithm

- Make locally optimal choices
- Efficient for problems with optimal substructure
- Covers tasks like activity selection, minimum coins

1️⃣ Merge Intervals  
2️⃣ Koko Eating Bananas  
3️⃣ Search in Rotated Sorted Array  
4️⃣ Detect a Cycle in Linked List  
5️⃣ Word Search II  
6️⃣ Gas Station  
7️⃣ Sliding Window Maximum  
8️⃣ Coin Change  
9️⃣ Word Break  
🔟 Edit Distance  
1️⃣1️⃣ Trapping Rainwater  
1️⃣2️⃣ Largest Rectangle in a Histogram  
1️⃣3️⃣ Rod Cutting  
1️⃣4️⃣ Binary Tree Maximum Path Sum  
1️⃣5️⃣ Number of Distinct Islands  
1️⃣6️⃣ Rotten Oranges  
1️⃣7️⃣ Course Schedule II  
1️⃣8️⃣ Pacific Atlantic Water Flow  
1️⃣9️⃣ Cheapest Flights Within K Stops  
2️⃣0️⃣ Min Cost to Connect All Points

These problems cover Greedy, DP, Graphs, Binary Search, Sliding Window, Trees, and more—helping to build a strong problem-solving mindset rather than just memorizing solutions.

💡 What I Learned Along the Way:  
🔹 Quality over quantity—solving fewer problems deeply is better than rushing through many.  
🔹 Pattern recognition matters—many problems share similar core ideas.  
🔹 Revisiting and optimizing solutions—helps reinforce concepts and improve efficiency.

If you’re preparing for interviews, don’t focus on hitting a high problem count. Focus on understanding concepts, thinking deeply, and solving strategically.

Of course, sometimes we do need to practice more to get better. The key is to identify what works best for you—some may need more practice, while others improve by focusing on fewer problems but solving them deeply.

- https://photonlines.substack.com/p/visual-focused-algorithms-cheat-sheet

- https://www.kirupa.com/data_structures_algorithms/intro_data_structures_why.htm (best)
- https://medium.com/javarevisited/data-structures-algorithms-cheat-sheet-for-tech-interviews-with-resources-025bb8b93368

| **Data Structure**            | **Type**                    | **Operations (Time Complexity)**             | **Use Cases**                                         |
| ----------------------------- | --------------------------- | -------------------------------------------- | ----------------------------------------------------- |
| **Array**                     | Linear                      | Access: O(1), Insert/Delete: O(n)            | Fixed-size collections, random access                 |
| **Dynamic Array**             | Linear                      | Insert: Amortized O(1), Access: O(1)         | Resizable array (e.g., Python lists)                  |
| **Linked List**               | Linear                      | Insert/Delete: O(1), Access: O(n)            | Dynamic memory allocation, stack/queue                |
| **Singly Linked List**        | Linear                      | Insert/Delete: O(1), Access: O(n)            | Sequential data, simple structures                    |
| **Doubly Linked List**        | Linear                      | Insert/Delete: O(1), Access: O(n)            | More complex data traversal, memory management        |
| **Circular Linked List**      | Linear                      | Insert/Delete: O(1), Access: O(n)            | Circular data, round-robin scheduling                 |
| **Stack**                     | Linear                      | Push/Pop: O(1)                               | Undo/redo functionality, parsing expressions          |
| **Queue**                     | Linear                      | Enqueue/Dequeue: O(1)                        | Task scheduling, BFS                                  |
| **Deque**                     | Linear                      | Insert/Remove from both ends: O(1)           | Sliding window problems, stack/queue hybrid           |
| **Tree**                      | Non-Linear                  | Insert/Search/Delete: O(log n) (avg)         | Hierarchical data, binary search, sorting             |
| **Binary Tree**               | Non-Linear                  | Insert/Search/Delete: O(log n) (avg)         | Tree traversal, hierarchical problems                 |
| **Binary Search Tree (BST)**  | Non-Linear                  | Insert/Search/Delete: O(log n) (avg)         | Fast searching, sorting, range queries                |
| **AVL Tree**                  | Non-Linear                  | Insert/Search/Delete: O(log n)               | Balanced search trees, optimized search               |
| **Heap**                      | Non-Linear                  | Insert/Extract: O(log n)                     | Priority queues, sorting algorithms (heap sort)       |
| **Trie (Prefix Tree)**        | Non-Linear                  | Insert/Search: O(k), where k = string length | Autocomplete, dictionary, prefix matching             |
| **Graph**                     | Non-Linear                  | BFS/DFS: O(V + E), Dijkstra: O(V log V)      | Social networks, pathfinding, recommendation          |
| **Adjacency Matrix**          | Graph (Dense)               | Insert/Search/Delete: O(1)                   | Dense graphs, quick edge lookups                      |
| **Adjacency List**            | Graph (Sparse)              | Insert/Search/Delete: O(V + E)               | Sparse graphs, dynamic graph traversal                |
| **Directed Graph (Digraph)**  | Graph                       | BFS/DFS: O(V + E), Shortest path: O(V + E)   | Directed dependencies, task scheduling                |
| **Undirected Graph**          | Graph                       | BFS/DFS: O(V + E), Shortest path: O(V + E)   | Social networks, connectivity                         |
| **Disjoint Set (Union-Find)** | Specialized                 | Union/Find: O(α(n))                          | Kruskal’s algorithm, network connectivity             |
| **Hash Table**                | Hashing                     | Insert/Search/Delete: O(1)                   | Caching, associative arrays, unique storage           |
| **Hash Set**                  | Hashing                     | Insert/Search/Delete: O(1)                   | Set operations, removing duplicates                   |
| **Priority Queue**            | Specialized                 | Insert: O(log n), Extract Min/Max: O(log n)  | Task scheduling, Dijkstra’s algorithm, Huffman coding |
| **Bloom Filter**              | Specialized (Probabilistic) | Insert/Check: O(1)                           | Membership testing, web caches, databases             |
| **Segment Tree**              | Advanced                    | Query/Update: O(log n)                       | Range queries, interval problems                      |
| **Fenwick Tree (BIT)**        | Advanced                    | Query/Update: O(log n)                       | Prefix sum queries, cumulative frequency              |
| **Suffix Tree**               | String Processing           | Search: O(m) where m is the pattern length   | String matching, text processing                      |
| **Suffix Array**              | String Processing           | Search: O(log n)                             | Pattern matching, suffix-based searches               |
| **K-d Tree**                  | Multi-dimensional           | Insert/Search: O(log n)                      | Range searches, nearest neighbor searches             |
| **Quad Tree**                 | Multi-dimensional           | Insert/Search: O(log n)                      | Spatial partitioning, image processing                |
| **Octree**                    | Multi-dimensional           | Insert/Search: O(log n)                      | 3D data, computer graphics                            |
| **Matrix**                    | Multi-dimensional           | Access: O(1), Operations: O(n^2)             | 2D grid storage, dynamic programming                  |
| **Skip List**                 | Specialized                 | Insert/Search/Delete: O(log n)               | Alternative to balanced trees, fast searching         |
| **Aho-Corasick**              | String Processing           | Search: O(n + m + z)                         | Multi-pattern matching, dictionary matching           |
| **B-Tree**                    | Tree (Balanced)             | Search/Insert/Delete: O(log n)               | Database indexing, file systems                       |

## ** LEVEL 1: FOUNDATIONAL PATTERNS** (Must-Know Before Anything Else)

### Pointer-Based Techniques

1. **Two Pointers** — converging/diverging on sorted arrays
2. **Fast & Slow Pointers** — cycle detection, finding middle
3. **Sliding Window** — contiguous subarrays/substrings
4. **Merge Intervals** — overlapping ranges, scheduling

### Search & Sort Variants

5. **Binary Search** — and all modified versions
6. **Cyclic Sort** — placing elements in their correct positions
7. **Insertion Sort Logic** — relevant to some interval problems

### Basic Graph Traversal

8. **BFS (Breadth-First Search)** — level-order, shortest path (unweighted)
9. **DFS (Depth-First Search)** — exploring all paths, connectivity

---

## ** LEVEL 2: STRUCTURAL PATTERNS** (Core Interview Techniques)

### Array & Matrix Problems

10. **Island Pattern (Matrix Traversal)** — connected components, flood fill
11. **Prefix Sum / Cumulative Sum** — range queries
12. **Product of Array / Except Self** — circular/prefix logic

### Linked List Techniques

13. **In-place Reversal of Linked Lists** — reversing segments
14. **Linked List Cycle** — detection & finding start

### Interval & Scheduling

15. **Insert & Merge Intervals** — calendar problems
16. **Meeting Rooms** — interval scheduling

### Stack Variations

17. **Monotonic Stack** — next greater/smaller element
18. **Valid Parentheses** — bracket matching (basic but important)

---

## ** LEVEL 3: ADVANCED SEARCH & OPTIMIZATION** (Interview Gold)

### Exhaustive Search

19. **Backtracking** — N-Queens, permutations, combinations, Sudoku
20. **Subsets Generation** — power set, all combinations

### Binary Search Extensions

21. **Modified Binary Search** — rotated arrays, find first/last occurrence
22. **Binary Search on Answer Space** — minimizing/maximizing something

### Bit Manipulation

23. **Bitwise XOR** — finding unpaired elements, swap tricks
24. **Bit Masking** — representing subsets, states

---

## ** LEVEL 4: DATA STRUCTURE OPTIMIZATION** (Efficiency Masters)

### Heaps & Priority Queues

25. **Two Heaps Pattern** — median finding, scheduling
26. **Top K Elements** — k-th largest, frequency sorting
27. **K-way Merge** — merging sorted streams/arrays

### Hash Tables & Counting

28. **Anagrams & Grouping** — character frequency patterns
29. **LRU Cache** — double-linked list + hash map

### Disjoint Sets

30. **Union-Find (Disjoint Set Union)** — connectivity, cycle detection in undirected graphs

---

## ** LEVEL 5: DYNAMIC PROGRAMMING**

### DP Fundamentals

31. **0/1 Knapsack** — bounded constraints, optimal selection
32. **Unbounded Knapsack** — unlimited items
33. **Coin Change** — minimum/maximum combinations
34. **Climbing Stairs** — path counting patterns

### DP on Sequences

35. **Longest Increasing Subsequence (LIS)** — optimal subsequences
36. **Longest Common Subsequence (LCS)** — sequence alignment
37. **Edit Distance (Levenshtein)** — string transformation
38. **Maximum Subarray (Kadane's Algorithm)** — contiguous optimization

### DP on Grids/2D

39. **Unique Paths** — grid navigation with obstacles
40. **Minimum Path Sum** — cost-based routing
41. **Matrix Chain Multiplication** — parenthesization order

### DP on Strings

42. **Word Break** — segmentation, dictionary lookup
43. **Palindromic Substrings** — longest/count
44. **Regular Expression Matching** — pattern DP

### DP with State Transition

45. **House Robber** — state transitions with constraints
46. **Stock Trading (Multiple Transactions)** — multi-state DP
47. **Paint House** — color-based state DP

---

## ** LEVEL 6: GRAPH ALGORITHMS**

### Shortest Path

48. **Dijkstra's Algorithm** — weighted shortest path
49. **Bellman-Ford Algorithm** — negative weights, cycle detection
50. **Floyd-Warshall** — all-pairs shortest path

### Minimum Spanning Tree

51. **Kruskal's Algorithm** — MST via sorting + Union-Find
52. **Prim's Algorithm** — MST via priority queue

### Connectivity & Flow

53. **Topological Sort** — dependency ordering, DAG
54. **Strongly Connected Components (SCC)** — Tarjan's/Kosaraju's
55. **Bipartite Check** — 2-coloring via BFS/DFS
56. **Network Flow (Ford-Fulkerson)** — max flow, min cut

---

## ** LEVEL 7: ADVANCED OPTIMIZATION**

### Greedy Algorithms

57. **Activity Selection** — interval scheduling
58. **Huffman Coding** — optimal compression
59. **Fractional Knapsack** — greedy vs DP comparison
60. **Jump Game / Reach** — greedy forward leaps

### Segment Trees & Range Queries

61. **Segment Trees** — range sum/min/max queries with updates
62. **Fenwick Tree (Binary Indexed Tree)** — efficient prefix sums
63. **Sparse Table** — static range min/max

### Tries & Pattern Matching

64. **Trie (Prefix Tree)** — autocomplete, word search
65. **Suffix Arrays / Suffix Trees** — pattern matching, text processing

### Advanced String Algorithms

66. **KMP (Knuth-Morris-Pratt)** — string pattern matching
67. **Rabin-Karp** — rolling hash, pattern detection
68. **Z-Algorithm** — linear time pattern matching

---

## ** LEVEL 8: COMPETITIVE/RARE PATTERNS** (If Time Permits)

### Randomization & Probabilistic

69. **QuickSelect** — finding k-th element without full sort
70. **Randomized Binary Search** — probabilistic guarantees

### Mathematical Patterns

71. **GCD / LCM Patterns** — number theory
72. **Modular Arithmetic** — large number handling
73. **Prime Sieve (Sieve of Eratosthenes)** — generate primes efficiently

### Combinatorial Patterns

74. **Next Permutation** — lexicographic ordering
75. **Combination/Permutation Generation** — systematic enumeration

---
