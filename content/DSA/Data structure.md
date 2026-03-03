- **Sliding Window:** This pattern is used to perform a required operation on a specific window size of a given array or linked list. An example of this is finding the longest subarray containing all 1s. This pattern is useful for problems that involve finding the longest/shortest substring, subarray, or value within a linear data structure, such as an array, linked list, or string. Some other problems you can solve using the Sliding Window pattern are:
  - Maximum sum subarray of size ‘K’ (easy)
  - Longest substring with ‘K’ distinct characters (medium)
  - String anagrams (hard)

- **Two Pointers or Iterators:** This pattern involves using two pointers that iterate through a data structure until one or both of the pointers hit a certain condition. This pattern is often useful when searching pairs in a sorted array or linked list. An example of this is when you have to compare each element of an array to its other elements. Two pointers are needed because using just one pointer would require you to continually loop back through the array to find the answer. This back-and-forth process with a single iterator is inefficient for time and space complexity, also known as asymptotic analysis. Using a single pointer would result in a time complexity of O(n²), which is not optimal. Two pointers can help you find a solution with better space or runtime complexity. Ways to identify when to use the Two Pointer method:
  - The problem deals with sorted arrays (or Linked Lists) and you need to find a set of elements that fulfill certain constraints
  - The set of elements in the array is a pair, a triplet, or even a subarray
  - Here are some problems that feature the Two Pointer pattern:
    - Squaring a sorted array (easy)
    - Triplets that sum to zero (medium)
    - Comparing strings that contain backspaces (medium)

- **Fast and Slow pointers:** This approach, also known as the **Hare & Tortoise algorithm**, is a pointer algorithm that uses two pointers that move through the array (or sequence/linked list) at different speeds. **This approach is quite useful when dealing with cyclic linked lists or arrays.** By moving at different speeds, the algorithm proves that the two pointers are bound to meet. The fast pointer should catch the slow pointer once both the pointers are in a cyclic loop. How do you identify when to use the Fast and Slow pattern?
  - The problem will deal with a loop in a linked list or array
  - When you need to know the position of a certain element or the overall length of the linked list.
    When should I use it over the Two Pointer method mentioned above?
    - There are some cases where you shouldn’t use the Two Pointer approach such as in a singly linked list where you can’t move in a backwards direction. An example of when to use the Fast and Slow pattern is when you’re trying to determine if a linked list is a palindrome.
      Problems featuring the fast and slow pointers pattern:
    - Linked List Cycle (easy)
    - Palindrome Linked List (medium)
    - Cycle in a Circular Array (hard)

- **Merge Intervals:** The Merge Intervals pattern is an efficient technique to deal with overlapping intervals. In a lot of problems involving intervals, you either need to find overlapping intervals or merge intervals if they overlap. Understanding and recognizing these six cases of overlapping intervals will help you solve a wide range of problems from inserting intervals to optimizing interval merges. How do you identify when to use the Merge Intervals pattern?
  - If you’re asked to produce a list with only mutually exclusive intervals
  - If you hear the term “overlapping intervals”. Merge interval problem patterns:
    - Intervals Intersection (medium)
    - Maximum CPU Load (hard)

- **Cyclic sort:** This pattern describes an interesting approach to deal with problems involving arrays containing numbers in a given range. The Cyclic Sort pattern iterates over the array one number at a time, and if the current number you are iterating is not at the correct index, you swap it with the number at its correct index. You could try placing the number in its correct index, but this will produce a complexity of O(n^2) which is not optimal, hence the Cyclic Sort pattern. How do I identify this pattern?
  - Problems involving a sorted array with numbers in a given range
  - If the problem asks you to find the missing/duplicate/smallest number in an unsorted/rotated array Problems featuring the cyclic sort pattern:
    - Find the Missing Number (easy)
    - Find the Smallest Missing Positive Number (medium)

- **In-place reversal of linked list:** In a lot of problems, you may be asked to reverse the links between a set of nodes of a linked list. Often, the constraint is that you need to do this in-place, i.e., using the existing node objects and without using extra memory. This pattern reverses one node at a time starting with one variable (current) pointing to the head of the linked list, and one variable (previous) will point to the previous node that you have processed. In a lock-step manner, you will reverse the current node by pointing it to the previous before moving on to the next node. Also, you will update the variable “previous” to always point to the previous node that you have processed. How do I identify when to use this pattern:
  - If you’re asked to reverse a linked list without using extra memory Problems featuring in-place reversal of linked list pattern:
    - Reverse a Sub-list (medium)
    - Reverse every K-element Sub-list (medium)

- **Tree BFS:** This pattern is based on the Breadth First Search (BFS) technique to traverse a tree and uses a queue to keep track of all the nodes of a level before jumping onto the next level. Any problem involving the traversal of a tree in a level-by-level order can be efficiently solved using this approach. The Tree BFS pattern works by pushing the root node to the queue and then continually iterating until the queue is empty. For each iteration, we remove the node at the head of the queue and “visit” that node. After removing each node from the queue, we also insert all of its children into the queue. How to identify the Tree BFS pattern:
  - If you’re asked to traverse a tree in a level-by-level fashion (or level order traversal) Problems featuring Tree BFS pattern:
    - Binary Tree Level Order Traversal (easy)
    - Zigzag Traversal (medium)

- **Tree DFS:** Tree DFS is based on the Depth First Search (DFS) technique to traverse a tree. You can use recursion (or a stack for the iterative approach) to keep track of all the previous (parent) nodes while traversing. The Tree DFS pattern works by starting at the root of the tree, if the node is not a leaf you need to do three things:
  1. Decide whether to process the current node now (pre-order), or between processing two children (in-order) or after processing both children (post-order).
  2. Make two recursive calls for both the children of the current node to process them. How to identify the Tree DFS pattern:
  - If you’re asked to traverse a tree with in-order, preorder, or postorder DFS
  - If the problem requires searching for something where the node is closer to a leaf Problems featuring Tree DFS pattern:
    - Sum of Path Numbers (medium)
    - All Paths for a Sum (medium)

- **Two heaps:** This pattern uses two heaps; A Min Heap to find the smallest element and a Max Heap to find the biggest element. The pattern works by storing the first half of numbers in a Max Heap, this is because you want to find the largest number in the first half. You then store the second half of numbers in a Min Heap, as you want to find the smallest number in the second half. At any time, the median of the current list of numbers can be calculated from the top element of the two heaps. Ways to identify the Two Heaps pattern:
  - Useful in situations like Priority Queue, Scheduling
  - If the problem states that you need to find the smallest/largest/median elements of a set
  - Sometimes, useful in problems featuring a binary tree data structure Problems featuring Two Heaps pattern:
    - Find the Median of a Number Stream (medium)

- **Subsets:** The pattern Subsets describes an efficient Breadth First Search (BFS) approach to handle problems involving Permutations and Combinations of a given set of elements. The pattern looks like this: Given a set of
  1. Start with an empty set: [[]]
  2. Add the first number (1) to all the existing subsets to create new subsets: [[],];
  3. Add the second number (5) to all the existing subsets: [[],,,];
  4. Add the third number (3) to all the existing subsets: [[],,,,,,,].

  How to identify the Subsets pattern:
  - Problems where you need to find the combinations or permutations of a given set Problems featuring Subsets pattern:
    - Subsets With Duplicates (easy)
    - String Permutations by changing case (medium)

- **Modified binary search:** This pattern describes an efficient way to handle all problems involving Binary Search in a sorted array, linked list, or matrix. The patterns looks like this for an ascending order set:
  1. First, find the middle of start and end. An easy way to find the middle would be: middle = (start + end) / 2. But this has a good chance of producing an integer overflow so it’s recommended that you represent the middle as: middle = start + (end — start) / 2
  2. If the key is equal to the number at index middle then return middle
  3. If ‘key’ isn’t equal to the index middle:
  4. Check if key < arr[middle]. If it is reduce your search to end = middle — 1
  5. Check if key > arr[middle]. If it is reduce your search to end = middle + 1

     Problems featuring the Modified Binary Search pattern:
     - Order-agnostic Binary Search (easy)
     - Search in a Sorted Infinite Array (medium)

- **Top K elements:** This pattern will make use of the Heap to solve multiple problems dealing with ‘K’ elements at a time from a set of given elements. The best data structure to keep track of ‘K’ elements is Heap. This pattern is for problems that ask you to find the top/smallest/frequent ‘K’ elements among a given set. The pattern looks like this:
  1. Insert ‘K’ elements into the min-heap or max-heap based on the problem.
  2. Iterate through the remaining numbers and if you find one that is larger than what you have in the heap, then remove that number and insert the larger one. There is no need for a sorting algorithm because the heap will keep track of the elements for you.

  How to identify the Top ‘K’ Elements pattern:
  - If you’re asked to find the top/smallest/frequent ‘K’ elements of a given set
  - If you’re asked to sort an array to find an exact element Problems featuring Top ‘K’ Elements pattern:
    - Top ‘K’ Numbers (easy)
    - Top ‘K’ Frequent Numbers (medium)

- **K-way Merge:** K-way Merge helps you solve problems that involve a set of sorted arrays. Whenever you’re given ‘K’ sorted arrays, you can use a Heap to efficiently perform a sorted traversal of all the elements of all arrays. You can push the smallest element of each array in a Min Heap to get the overall minimum. After getting the overall minimum, push the next element from the same array to the heap. Then, repeat this process to make a sorted traversal of all elements. The pattern looks like this:
  1. Insert the first element of each array in a Min Heap.
  2. After this, take out the smallest (top) element from the heap and add it to the merged list.
  3. After removing the smallest element from the heap, insert the next element of the same list into the heap.
  4. Repeat steps 2 and 3 to populate the merged list in sorted order.

  How to identify the K-way Merge pattern:
  - The problem will feature sorted arrays, lists, or a matrix
  - If the problem asks you to merge sorted lists, find the smallest element in a sorted list. Problems featuring the K-way Merge pattern:
    - Merge K Sorted Lists (medium)
    - K Pairs with Largest Sums (Hard)

- **Topological Sort:** Topological Sort is used to find a linear ordering of elements that have dependencies on each other. For example, if event ‘B’ is dependent on event ‘A’, ‘A’ comes before ‘B’ in topological ordering. This pattern defines an easy way to understand the technique for performing topological sorting of a set of elements. The pattern works like this:
  1. Initialization a. Store the graph in adjacency lists by using a HashMap b. To find all sources, use a HashMap to keep the count of in-degrees Build the graph and find in-degrees of all vertices
  2. Build the graph from the input and populate the in-degrees HashMap.
  3. Find all sources a. All vertices with ‘0’ in-degrees will be sources and are stored in a Queue.
  4. Sort a. For each source, do the following things: —i) Add it to the sorted list. — ii)Get all of its children from the graph. — iii)Decrement the in-degree of each child by 1. — iv)If a child’s in-degree becomes ‘0’, add it to the sources Queue. b. Repeat (a), until the source Queue is empty.
     How to identify the Topological Sort pattern:
  - The problem will deal with graphs that have no directed cycles
  - If you’re asked to update all objects in a sorted order
  - If you have a class of objects that follow a particular order Problems featuring the Topological Sort pattern:
    - Task scheduling (medium)
    - Minimum height of a tree (hard)

[Source](https://hackernoon.com/14-patterns-to-ace-any-coding-interview-question-c5bb3357f6ed)

## Graph

nodes + edges

Representation

#### Adjacency Matrix

A **2D array (matrix)** is used where:

- `matrix[i][j] = 1` (or weight `w`) if there is an edge from `i` to `j`
- `matrix[i][j] = 0` if there is no edge

```
graph = [
    [0, 1, 0, 1],
    [1, 0, 1, 1],
    [0, 1, 0, 1],
    [1, 1, 1, 0]
]

```

**Pros:**

- Fast `O(1)` edge lookup (to check if `u` is connected to `v`)
- Good for **dense** graphs (many edges)

  **Cons:**

- Uses `O(V²)` space (bad for large graphs)
- Slow `O(V)` iteration for neighbors

#### **Adjacency List**

A **dictionary (hashmap) or list of lists** is used, where each node has a list of its neighbors.

```
graph = {
    0: [1, 3],
    1: [0, 2, 3],
    2: [1, 3],
    3: [0, 1, 2]
}

```

**Pros:**

- Uses `O(V + E)` space (efficient for large, sparse graphs)
- Fast `O(1)` average-time edge insertion/removal
- Best for **sparse** graphs (few edges)

  **Cons:**

- Slower `O(degree)` edge lookup compared to adjacency matrix

#### **Edge List**

A **list of edges** (tuples or lists), storing only the connections.

```
edges = [(0, 1), (0, 3), (1, 2), (1, 3), (2, 3)]

O will connect with 0 and 1
1 will connect with 0 and 3
2 will connecte with 1 and 2
etc

```

- Uses `O(E)` space (smallest for sparse graphs)
- Good for algorithms like Kruskal’s
- `O(E)` edge lookup time (slowest)

### Types

**Directed**

- Edges have a direction (one-way connections).
- Represented using an **asymmetric adjacency matrix** (`graph[i][j]` can be `1`, but `graph[j][i]` can be `0`).
- Used in **webpage links**, **road networks with one-way streets**, **dependency graphs**.

```
    (A) → (B) → (C)
           ↘
             (D)
```

**Undirected Graph**

- Edges have **no direction** (connections are bidirectional).
- Represented using a **symmetric adjacency matrix** (`graph[i][j] == graph[j][i]`).

```
    (A) --- (B)
      \     /
       (C)

```

### Algorithms

#### Breadth-First Search (BFS)

1. Start from a node, mark it as visited.
2. Use a **queue** (FIFO) to explore neighbors.
3. Continue until all reachable nodes are visited.

**used for**

- **Finding the shortest path** in an **unweighted graph**

```js
function bfs(graph, start) {
  const visited = new Set()
  const queue = [start]

  while (queue.length > 0) {
    const node = queue.shift() // dequeue
    if (!visited.has(node)) {
      console.log(node) // process node
      visited.add(node)
      for (const neighbor of graph[node]) {
        if (!visited.has(neighbor)) {
          queue.push(neighbor) // enqueue
        }
      }
    }
  }
}

// Example graph
const graph = {
  A: ["B", "C"],
  B: ["D", "E"],
  C: ["F"],
  D: [],
  E: ["F"],
  F: [],
}

console.log("BFS starting from A:")
bfs(graph, "A")
```

#### Depth-First Search (DFS)

1. Start from a node, mark it as visited.
2. Use a **stack (LIFO)** or recursion to explore deep first.
3. Backtrack when needed.

```js
function dfsRecursive(graph, node, visited = new Set()) {
  if (!visited.has(node)) {
    console.log(node) // process node
    visited.add(node)
    for (const neighbor of graph[node]) {
      dfsRecursive(graph, neighbor, visited)
    }
  }
}

console.log("DFS Recursive starting from A:")
dfsRecursive(graph, "A")
```

**Used for**

- **Detecting cycles** in a graph

Trees

```javascript
// Tree Node definition
class Node {
  constructor(value) {
    this.value = value
    this.children = [] // multiple children allowed (general tree)
  }

  addChild(node) {
    this.children.push(node)
  }
}

// DFS Traversal (recursive)
function dfs(root) {
  const result = []

  function traverse(node) {
    if (!node) return
    result.push(node.value) // visit current node
    for (let child of node.children) {
      traverse(child) // recursively visit children
    }
  }

  traverse(root)
  return result
}

// BFS Traversal (level-order)
function bfs(root) {
  if (!root) return []

  const result = []
  const queue = [root]

  while (queue.length > 0) {
    const node = queue.shift()
    result.push(node.value)
    for (let child of node.children) {
      queue.push(child)
    }
  }

  return result
}

// Height of the tree (max depth)
function height(root) {
  if (!root) return 0
  if (root.children.length === 0) return 1

  let maxChildHeight = 0
  for (let child of root.children) {
    maxChildHeight = Math.max(maxChildHeight, height(child))
  }
  return maxChildHeight + 1 // include current node
}

// Width of the tree (maximum nodes in any level)
function width(root) {
  if (!root) return 0

  let maxWidth = 0
  const queue = [root]

  while (queue.length > 0) {
    const levelSize = queue.length
    maxWidth = Math.max(maxWidth, levelSize)

    for (let i = 0; i < levelSize; i++) {
      const node = queue.shift()
      for (let child of node.children) {
        queue.push(child)
      }
    }
  }

  return maxWidth
}

// ------------------ Example ------------------

// Build tree:
//         A
//       / | \
//      B  C  D
//     / \     \
//    E   F     G

const A = new Node("A")
const B = new Node("B")
const C = new Node("C")
const D = new Node("D")
const E = new Node("E")
const F = new Node("F")
const G = new Node("G")

A.addChild(B)
A.addChild(C)
A.addChild(D)
B.addChild(E)
B.addChild(F)
D.addChild(G)

// Run all functions
console.log("DFS:", dfs(A)) // A, B, E, F, C, D, G
console.log("BFS:", bfs(A)) // A, B, C, D, E, F, G
console.log("Height:", height(A)) // 3 (A-B-E)
console.log("Width:", width(A)) // 3 (Level 2: B, C, D)
```

```javascript
// ----------------- Binary Tree Node -----------------
class Node {
  constructor(value) {
    this.value = value
    this.left = null
    this.right = null
  }
}

// ----------------- DFS Traversal (Preorder) -----------------
function dfs(root) {
  const result = []

  function traverse(node) {
    if (!node) return
    result.push(node.value) // Visit node
    traverse(node.left) // Go left
    traverse(node.right) // Go right
  }

  traverse(root)
  return result
}

// ----------------- BFS Traversal (Level-order) -----------------
function bfs(root) {
  if (!root) return []

  const result = []
  const queue = [root]

  while (queue.length > 0) {
    const node = queue.shift()
    result.push(node.value)

    if (node.left) queue.push(node.left)
    if (node.right) queue.push(node.right)
  }

  return result
}

// ----------------- Height of Binary Tree -----------------
function height(root) {
  if (!root) return 0
  return 1 + Math.max(height(root.left), height(root.right))
}

// ----------------- Width of Binary Tree -----------------
function width(root) {
  if (!root) return 0

  let maxWidth = 0
  const queue = [root]

  while (queue.length > 0) {
    const levelSize = queue.length
    maxWidth = Math.max(maxWidth, levelSize)

    for (let i = 0; i < levelSize; i++) {
      const node = queue.shift()
      if (node.left) queue.push(node.left)
      if (node.right) queue.push(node.right)
    }
  }

  return maxWidth
}

// ----------------- Example Binary Tree -----------------
//           A
//          / \
//         B   C
//        / \   \
//       D   E   F

const A = new Node("A")
const B = new Node("B")
const C = new Node("C")
const D = new Node("D")
const E = new Node("E")
const F = new Node("F")

A.left = B
A.right = C
B.left = D
B.right = E
C.right = F

// ----------------- Run All -----------------
console.log("DFS (Preorder):", dfs(A)) // A, B, D, E, C, F
console.log("BFS (Level-order):", bfs(A)) // A, B, C, D, E, F
console.log("Height:", height(A)) // 3 (A-B-D)
console.log("Width:", width(A)) // 3 (Level 2: B, C, F)
```

```javascript
/**
 * single-file: common binary-tree functions (binary trees & BSTs)
 *
 * Implemented:
 * - Node class
 * - recursive traversals: preorder, inorder, postorder
 * - iterative traversals (preorder, inorder, postorder)
 * - level-order (BFS) + zigzag level order
 * - height, width, size (node count), leaf count
 * - isBST (validate BST)
 * - lowest common ancestor (LCA) for binary tree (not only BST)
 * - diameter (longest path in nodes)
 * - max path sum (max root-to-root path)
 * - invert/mirror tree
 * - serialize/deserialize (preorder)
 * - kth smallest in BST
 * - pathSum (existence of root-to-leaf sum)
 *
 * Each function is commented and demonstrated.
 */

// ---------------- Node ----------------
class Node {
  constructor(val) {
    this.val = val
    this.left = null
    this.right = null
  }
}

// ---------------- Traversals ----------------
// 1. Recursive preorder/inorder/postorder
function preorderRec(root, out = []) {
  if (!root) return out
  out.push(root.val)
  preorderRec(root.left, out)
  preorderRec(root.right, out)
  return out
}
function inorderRec(root, out = []) {
  if (!root) return out
  inorderRec(root.left, out)
  out.push(root.val)
  inorderRec(root.right, out)
  return out
}
function postorderRec(root, out = []) {
  if (!root) return out
  postorderRec(root.left, out)
  postorderRec(root.right, out)
  out.push(root.val)
  return out
}

// 2. Iterative traversals (stack-based)
function preorderIter(root) {
  if (!root) return []
  const stack = [root],
    out = []
  while (stack.length) {
    const node = stack.pop()
    out.push(node.val)
    if (node.right) stack.push(node.right)
    if (node.left) stack.push(node.left)
  }
  return out
}
function inorderIter(root) {
  const out = [],
    stack = [],
    cur = { node: root }
  let node = root
  while (stack.length || node) {
    while (node) {
      stack.push(node)
      node = node.left
    }
    node = stack.pop()
    out.push(node.val)
    node = node.right
  }
  return out
}
function postorderIter(root) {
  // two-stack method
  if (!root) return []
  const s1 = [root],
    s2 = [],
    out = []
  while (s1.length) {
    const n = s1.pop()
    s2.push(n)
    if (n.left) s1.push(n.left)
    if (n.right) s1.push(n.right)
  }
  while (s2.length) out.push(s2.pop().val)
  return out
}

// 3. BFS / Level-order
function levelOrder(root) {
  if (!root) return []
  const q = [root],
    out = []
  while (q.length) {
    const node = q.shift()
    out.push(node.val)
    if (node.left) q.push(node.left)
    if (node.right) q.push(node.right)
  }
  return out
}
function levelOrderByLevel(root) {
  if (!root) return []
  const q = [root],
    out = []
  while (q.length) {
    const size = q.length
    const level = []
    for (let i = 0; i < size; i++) {
      const n = q.shift()
      level.push(n.val)
      if (n.left) q.push(n.left)
      if (n.right) q.push(n.right)
    }
    out.push(level)
  }
  return out
}
function zigzagLevelOrder(root) {
  if (!root) return []
  const q = [root],
    out = [],
    leftToRight = { val: true }
  let dir = true
  while (q.length) {
    const size = q.length,
      level = []
    for (let i = 0; i < size; i++) {
      const n = q.shift()
      level.push(n.val)
      if (n.left) q.push(n.left)
      if (n.right) q.push(n.right)
    }
    out.push(dir ? level : level.reverse())
    dir = !dir
  }
  return out
}

// ---------------- Metrics: height, width, size, leaves ----------------
function height(root) {
  // nodes count in depth (empty -> 0)
  if (!root) return 0
  return 1 + Math.max(height(root.left), height(root.right))
}
function size(root) {
  if (!root) return 0
  return 1 + size(root.left) + size(root.right)
}
function leafCount(root) {
  if (!root) return 0
  if (!root.left && !root.right) return 1
  return leafCount(root.left) + leafCount(root.right)
}
function maxWidth(root) {
  // maximum nodes in any level
  if (!root) return 0
  const q = [root]
  let maxW = 0
  while (q.length) {
    maxW = Math.max(maxW, q.length)
    const size = q.length
    for (let i = 0; i < size; i++) {
      const n = q.shift()
      if (n.left) q.push(n.left)
      if (n.right) q.push(n.right)
    }
  }
  return maxW
}

// ---------------- BST validation ----------------
function isBST(root) {
  // in-order must be strictly increasing for a valid BST
  const arr = inorderRec(root, [])
  for (let i = 1; i < arr.length; i++) if (arr[i] <= arr[i - 1]) return false
  return true
}

// ---------------- Lowest Common Ancestor (binary tree) ----------------
function lowestCommonAncestor(root, p, q) {
  // returns node or null; p and q are values (for simplicity)
  function dfs(node) {
    if (!node) return null
    if (node.val === p || node.val === q) return node
    const L = dfs(node.left)
    const R = dfs(node.right)
    if (L && R) return node
    return L ? L : R
  }
  return dfs(root)
}

// ---------------- Diameter (longest path in nodes) ----------------
function diameter(root) {
  let ans = 0
  function dfs(node) {
    if (!node) return 0
    const L = dfs(node.left)
    const R = dfs(node.right)
    ans = Math.max(ans, 1 + L + R) // nodes in path through node
    return 1 + Math.max(L, R)
  }
  dfs(root)
  return ans
}

// ---------------- Max Path Sum (classic: max root-to-root through any node) ----------------
function maxPathSum(root) {
  let maxSum = -Infinity
  function dfs(node) {
    if (!node) return 0
    const L = Math.max(0, dfs(node.left))
    const R = Math.max(0, dfs(node.right))
    maxSum = Math.max(maxSum, node.val + L + R)
    return node.val + Math.max(L, R)
  }
  dfs(root)
  return maxSum
}

// ---------------- Invert / Mirror Tree ----------------
function invertTree(root) {
  if (!root) return null
  const left = invertTree(root.left)
  const right = invertTree(root.right)
  root.left = right
  root.right = left
  return root
}

// ---------------- Serialize / Deserialize (preorder with null markers) ----------------
function serialize(root) {
  const out = []
  function s(n) {
    if (!n) {
      out.push("#")
      return
    }
    out.push(String(n.val))
    s(n.left)
    s(n.right)
  }
  s(root)
  return out.join(",")
}
function deserialize(data) {
  if (!data) return null
  const arr = data.split(",")
  let i = 0
  function d() {
    if (i >= arr.length) return null
    const token = arr[i++]
    if (token === "#") return null
    const node = new Node(Number.isNaN(Number(token)) ? token : Number(token))
    node.left = d()
    node.right = d()
    return node
  }
  return d()
}

// ---------------- kth smallest in BST ----------------
function kthSmallest(root, k) {
  // inorder traversal yields sorted for BST
  const stack = [],
    node = root
  let cur = root,
    count = 0
  while (stack.length || cur) {
    while (cur) {
      stack.push(cur)
      cur = cur.left
    }
    cur = stack.pop()
    count++
    if (count === k) return cur.val
    cur = cur.right
  }
  return null
}

// ---------------- pathSum: root-to-leaf sum existence ----------------
function hasPathSum(root, target) {
  if (!root) return false
  if (!root.left && !root.right) return root.val === target
  return hasPathSum(root.left, target - root.val) || hasPathSum(root.right, target - root.val)
}

// ---------------- Build tree from inorder + preorder (classic) ----------------
function buildTreeFromPreIn(preorderArr, inorderArr) {
  const idxMap = new Map()
  for (let i = 0; i < inorderArr.length; i++) idxMap.set(inorderArr[i], i)
  let preIndex = 0
  function helper(left, right) {
    if (left > right) return null
    const rootVal = preorderArr[preIndex++]
    const root = new Node(rootVal)
    const idx = idxMap.get(rootVal)
    root.left = helper(left, idx - 1)
    root.right = helper(idx + 1, right)
    return root
  }
  return helper(0, inorderArr.length - 1)
}

// ---------------- Example/demo ----------------
// Construct a sample binary tree:
//           5
//         /   \
//        3     8
//       / \   / \
//      1   4 7  10
//                 \
//                 12

const root = new Node(5)
root.left = new Node(3)
root.right = new Node(8)
root.left.left = new Node(1)
root.left.right = new Node(4)
root.right.left = new Node(7)
root.right.right = new Node(10)
root.right.right.right = new Node(12)

// Traversals
console.log("preorderRec:", preorderRec(root))
console.log("inorderRec:", inorderRec(root))
console.log("postorderRec:", postorderRec(root))
console.log("preorderIter:", preorderIter(root))
console.log("inorderIter:", inorderIter(root))
console.log("postorderIter:", postorderIter(root))
console.log("levelOrder:", levelOrder(root))
console.log("levelOrderByLevel:", levelOrderByLevel(root))
console.log("zigzagLevelOrder:", zigzagLevelOrder(root))

// Metrics
console.log("height:", height(root))
console.log("size:", size(root))
console.log("leafCount:", leafCount(root))
console.log("maxWidth:", maxWidth(root))

// BST checks & ops
console.log("isBST:", isBST(root)) // true for this constructed tree
console.log("kthSmallest k=3:", kthSmallest(root, 3)) // should be 4 (1,3,4,5,7,8,10,12)

// LCA (values)
console.log("LCA of 1 and 4:", (lowestCommonAncestor(root, 1, 4) || {}).val) // 3

// diameter & max path sum (values used as node costs)
console.log("diameter (nodes):", diameter(root))
console.log("maxPathSum:", maxPathSum(root))

// invert
const serializedBefore = serialize(root)
console.log("serialize before invert:", serializedBefore)
invertTree(root)
console.log("serialize after invert:", serialize(root))
invertTree(root) // invert back

// serialize / deserialize
const s = serialize(root)
const r2 = deserialize(s)
console.log("serialize -> deserialize -> inorder:", inorderRec(r2))

// path sum example
console.log("hasPathSum target 9 (5->3->1):", hasPathSum(root, 9))

// buildTreeFromPreIn demo
const pre = [5, 3, 1, 4, 8, 7, 10, 12]
const inord = [1, 3, 4, 5, 7, 8, 10, 12]
const built = buildTreeFromPreIn(pre, inord)
console.log("built inorder:", inorderRec(built))

// Note: functions assume numbers or strings consistently as node values.
// For production, avoid shift() in performance-critical code; use index pointers for queue or deque.
```

- https://leetwho.com/

### Low level design

**1. Object-Oriented Design (OOD) Principles**

- **SOLID Principles**
  - **S**ingle Responsibility Principle
  - **O**pen/Closed Principle
  - **L**iskov Substitution Principle
  - **I**nterface Segregation Principle
  - **D**ependency Inversion Principle
- Encapsulation, Abstraction, Inheritance, Polymorphism

**2. Design Patterns (Gang of Four - GoF)**

- **Creational Patterns**
  - Singleton, Factory, Abstract Factory, Builder, Prototype
- **Structural Patterns**
  - Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy
- **Behavioral Patterns**
  - Strategy, Observer, Command, Chain of Responsibility, State, Template Method

**3. UML Diagrams (Unified Modeling Language)**

- Class Diagrams
- Sequence Diagrams
- Activity Diagrams

**4. System Components & Interaction**

- API Design & Best Practices
- Database Design (Normalization, Indexing, Transactions)
- Caching Strategies (LRU Cache, Redis, In-memory Caching)
- Concurrency & Thread Safety (Locks, Mutex, Synchronization, Deadlocks)

### class diagram

- `+` for public (visible to all classes)
- `-` for private (visible only within the class)
- `#` for protected (visible to subclasses)
- `~` for package or default visibility (visible to classes in the same package)

## Resources

- https://www.stratascratch.com/
-
