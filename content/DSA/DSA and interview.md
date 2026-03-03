## TIps in DSA

- Ask clarify question before start etc.
- first add basic condition and return
- Give proper varaiables etc
- Explain your logic and thought process if we have more then one apporach tell why we choose this apporach what make how it differes etc

Best one to follow

- https://takeuforward.org/strivers-a2z-dsa-course/strivers-a2z-dsa-course-sheet-2/

## Two pointer approach

- two moving pointer at diff speed
- two are in same direction
- Opposite direction

we need to take decsion based on condition when we want to shrink the pointer from left or right

for **Max Water Hold** problem we move pointer based on which is lesser

## Array

Pre compute technique

Prefix sum is a technique where we **pre-compute** cumulative sums of an array to **answer range queries efficiently**.

“What’s the sum of elements from index `i` to `j`?”

- if we precompute a prefix sum array to answer each in `O(1)` time.

| Problem Type                  | Example Problems                                            |
| ----------------------------- | ----------------------------------------------------------- |
| **Basic Traversal**           | Sum, Max/Min, Reverse                                       |
| **Searching**                 | Linear Search, Binary Search                                |
| **Sorting**                   | QuickSort, MergeSort, Bubble Sort                           |
| **Prefix Sum**                | Range Sum Query, Subarray Sum                               |
| **Sliding Window**            | Max sum subarray, Longest substring without repeating chars |
| **Two Pointers**              | Pair Sum, Container With Most Water                         |
| **Hashing (Map/Set)**         | Two Sum, Longest Consecutive Sequence                       |
| **Binary Search on Answer**   | Koko Eating Bananas, Capacity to Ship Packages              |
| **Greedy**                    | Min Platforms, Merge Intervals                              |
| **Kadane’s Algorithm**        | Maximum Subarray Sum                                        |
| **Subarrays/Subsets**         | Count/Generate Subarrays, Subset Sum                        |
| **Backtracking**              | Subsets, Combination Sum                                    |
| **Bit Manipulation**          | Find Single Number, XOR Tricks                              |
| **Prefix XOR**                | Count of subarrays with XOR = K                             |
| **Monotonic Stack**           | Next Greater Element, Histogram Area                        |
| **Union Find (Disjoint Set)** | Detect Cycles in Graphs (if grid based)                     |
| **DP (on Array)**             | House Robber, Max Product Subarray                          |
| **Divide & Conquer**          | Maximum Subarray (recursive)                                |
| **Counting/Indexing**         | Counting Sort, Inversion Count                              |
| **Rotations/Shifts**          | Rotate Array, Cyclic Sort                                   |

## Monotonic stack

A **Monotonic Stack** is a special kind of stack where elements are kept in **monotonic (increasing or decreasing) order**.

- **Next Greater Element**
- **Previous Smaller Element**
- **Largest Rectangle in Histogram**
- **Daily Temperatures**
- **Stock Span Problem**

pattern

```js
for (let i = 0; i < arr.length; i++) {
  while (stack.length && (condition based on arr[i] and stack top)) {
    // Do something with stack.pop()
  }
  stack.push(i);
}

```

```js
const nums = [300, 4, 2, 1, 5, 3, 400]

const stack = []
const result = Array(nums.length).fill(-1) // Array to store the result

for (let i = 0; i < nums.length; i++) {
  // While stack is not empty and current element is greater than stack's top
  while (stack.length && nums[i] > nums[stack[stack.length - 1]]) {
    const index = stack.pop() // Get index of the previous smaller element
    result[index] = nums[i] // Set the next greater element for that index
  }
  stack.push(i) // Push current element's index onto the stack
}

console.log(result) // Output the next greater elements
;[400, 5, 5, 5, 400, 400, -1]
```

### HEAP

A **heap** is a **special kind of binary tree** used mainly for **priority queues** and **efficient sorting** (like in **Heap Sort**). It has these main properties:

1. **Complete Binary Tree**
   - Every level is fully filled except possibly the last.
   - Last level has all nodes **as left as possible**.

2. **Heap Property**  
   Two types:
   - **Max Heap**: Every parent node is **greater than or equal** to its children.
   - **Min Heap**: Every parent node is **less than or equal** to its children.

Implement a heap using an **array** (no need for pointers!):

- For index `i`:
  - **Left child** → at `2i + 1`
  - **Right child** → at `2i + 2`
  - **Parent** → at `(i - 1) // 2`

```
        30
      /    \
    15      25
   /  \     /
  5   10   20

```

Insertion

- when inserting the element insert the element in last index array and do compare with parent until condition match and swap such that we will not get holes array

```
        30
      /    \
    15      25
   /  \     /


- Let we going to insert a new number it need to be from left such that when we store that in array it wont create holes
[30,15,25,5]

```

Deletion

- Remove root node and replace the last node to root node and do the comparsion from root node until no issue

- If we want sorted array we need to remove one element by one element and do heapfiy

```js
class Heap {
  constructor(compare) {
    this.data = []
    this.compare = compare // (a, b) => a < b for MinHeap, a > b for MaxHeap
  }

  parent(i) {
    return Math.floor((i - 1) / 2)
  }
  left(i) {
    return 2 * i + 1
  }
  right(i) {
    return 2 * i + 2
  }

  swap(i, j) {
    ;[this.data[i], this.data[j]] = [this.data[j], this.data[i]]
  }

  push(value) {
    this.data.push(value)
    this.heapifyUp(this.data.length - 1)
  }

  pop() {
    if (this.data.length === 0) return undefined
    if (this.data.length === 1) return this.data.pop()
    const root = this.data[0]
    this.data[0] = this.data.pop()
    this.heapifyDown(0)
    return root
  }

  peek() {
    return this.data[0]
  }

  heapifyUp(i) {
    while (i > 0) {
      const p = this.parent(i)
      if (this.compare(this.data[i], this.data[p])) {
        this.swap(i, p)
        i = p
      } else break
    }
  }

  heapifyDown(i) {
    const n = this.data.length
    while (true) {
      let best = i
      const l = this.left(i)
      const r = this.right(i)

      if (l < n && this.compare(this.data[l], this.data[best])) best = l
      if (r < n && this.compare(this.data[r], this.data[best])) best = r

      if (best !== i) {
        this.swap(i, best)
        i = best
      } else break
    }
  }
}

// Usage:
// const minHeap = new Heap((a, b) => a < b);
// const maxHeap = new Heap((a, b) => a > b);
```

### Sorting

- Bubble sort
  - Swap two elements until no swap needed
- Selection sort
  - Select pick smalles element and put to new array and repeat that on pick min from array
- Insertion sort
  - Pick one number and find the right place to insert

```
 Let’s trace through this:

**Initial Array:** `[5, 3, 4, 1, 2]`

- **Pass 1:** key = 3 → insert before 5 → `[3, 5, 4, 1, 2]`

- **Pass 2:** key = 4 → insert before 5 → `[3, 4, 5, 1, 2]`

- **Pass 3:** key = 1 → move 5, 4, 3 → `[1, 3, 4, 5, 2]`

- **Pass 4:** key = 2 → move 5, 4, 3 → `[1, 2, 3, 4, 5]`
```

- Merge sort
  - Split ➡ Sort ➡ Merge
  -

- Quick sort
  1.  **Pick a pivot** (any element from the array).
  2.  **Partition** the array into two parts:
      - Elements **less than** the pivot.
      - Elements **greater than or equal to** the pivot.
  3.  **Recursively** apply the same steps to the left and right parts.
  4.  Combine the results.

- Heap sort
- Couting sort

### Buket sort

1. Number line divided into segments
2. Mapping function routes each value to its segment
3. Segments are inherently ordered
4. Only local disorder is fixed inside each segment

> Sorting by location first, comparison second.

complexity approaches O(n)

```js
function bucketSort(arr, bucketSize = 5) {
  if (arr.length === 0) return arr

  let min = Math.min(...arr)
  let max = Math.max(...arr)

  let bucketCount = Math.floor((max - min) / bucketSize) + 1
  let buckets = Array.from({ length: bucketCount }, () => [])

  for (let num of arr) {
    let index = Math.floor((num - min) / bucketSize)
    buckets[index].push(num)
  }

  return buckets.map((bucket) => bucket.sort((a, b) => a - b)).flat()
}
```

- https://platform.stratascratch.com/coding?code_type=1

Frontend

- https://www.greatfrontend.com/front-end-system-design-playbook/types-of-questions
- https://frontendlead.com/system-design/frontend-system-design-interview-guide

## binary search

In binary search, the midpoint is usually found as `mid = (l + h) / 2`.  
However, if `l` and `h` are very large, their sum `(l + h)` might exceed the maximum integer limit and cause **overflow**.

To prevent this, we use:  
`mid = l + (h - l) / 2`

**Why it works:**

- `(h - l)` is always smaller than `(l + h)`, so it stays within range.
- Adding `l` after halving ensures the midpoint is still correctly positioned between `l` and `h`.

**Short definition:**  
A safe way to compute the midpoint in binary search that avoids integer overflow.

**The Core Insight of Binary Search**

At its heart, **binary search** is not about arrays it’s about **searching in any ordered space** where you can test whether the solution lies to the “left” or “right” of some midpoint.

So, if:

1. You know the answer lies between two bounds — say, between `low` and `high`, and
2. You can ask a _yes/no question_ at a midpoint `mid` like “is the solution smaller or larger than this?”,

then we can repeatedly **halve the search space** until you find the answer.

That’s the abstract idea and it works even outside of arrays.

**Applying That Idea to Finding a Square Root**

Let’s find √100 using binary search.

We know:

- The answer lies between `low = 0` and `high = 100`.
- If we pick any `mid`, we can test:
  - If `mid * mid == 100` → we found it.
  - If `mid * mid < 100` → the true square root must be _larger_ (move right).
  - If `mid * mid > 100` → the true square root must be _smaller_ (move left).

That’s exactly the same left/right decision rule used in binary search on arrays only now, the comparison is based on the **square of mid**.

## Bitwise

find not repating number in array
we can use XOR

Because XOR doesn’t depend on order it’s **commutative** and **associative**:

```
a ⊕ b ⊕ a ⊕ b ⊕ c  =  c
```

```js
function findSingleNumber(arr) {
  let result = 0
  for (let num of arr) {
    result ^= num
  }
  return result
}

console.log(findSingleNumber([1, 1, 2, 3, 3, 4, 4])) // 2
```

But if the array is sorted we can use binarysearch and which is log n

## TWO pointer

- where to init
- how to update which one to move and when to stop

Use **elimination logic** — each comparison lets you confidently discard part of the search space by moving one pointer while keeping the other.

**The reasoning steps:**

1. **Initialize**: Place pointers at strategic positions (often start/end or both at start)
2. **Evaluate**: Check the current state (sum, comparison, condition)
3. **Decide**: Based on the evaluation, determine which pointer to move
4. **Eliminate**: Moving a pointer guarantees you're not missing solutions (this is key!)
5. **Converge**: Pointers move toward each other or scan the structure until done

If naive solution involves nested loops over the same structure, ask: "Can I eliminate parts of the search space based on comparisons?"

intersection of two array

- if it is sorted we can use two pointer

## Montonic

Monotonic properties relate to the consistent, one-directional behavior of a function, sequence, or system as its inputs or elements increase. A property is monotonic if it is either entirely non-increasing or entirely non-decreasing across its entire domain or a specific interval

## Hashing

- replicating substring

## Recursion

- we need to reapet same step so figure it out one step that need to repat and do.

## Sliding window

- Subarray,substring we need to go with this and the answer must need to continous (if we combine a subarray to get sum etc.)
  - We need to know when to shrink our window and how

- Max subarray sum
- count of anagram

## Arrays

### **Maximum Product Subarray**

why this algorithm exists and why it looks “strange”, you need clarity on these concepts:

1. Contiguous subarrays and how they differ from subsequences
2. Why brute force is too slow for subarray problems
3. Dynamic programming as “carry forward best partial solutions”
4. How multiplication behaves:
   - sign flips with negatives
   - zero as a reset element
5. Why tracking only one “best so far” fails for products

We want:

> The maximum product of any contiguous subarray.

Unlike sum, multiplication has dangerous behavior:

- Negative × Negative = Positive
- Zero wipes everything
- A very small negative can become very large when multiplied by another negative later

So a simple “keep the largest product so far” is insufficient.

## Why naive thinking fails

Let’s say we tried this logic:

> “At each index, keep the largest product ending here.”

This fails because:

- A large negative product might be terrible now but excellent later if multiplied by another negative.

So the system must remember:

- The **maximum product ending here**
- The **minimum product ending here**

Why minimum? Because it might become the maximum after sign flip.

This is the key insight.

At every position `i`, we ask:

What is the maximum product subarray that MUST end at index `i`?

Three possibilities:

1. Start fresh at nums[i]
2. Extend previous max: max \* nums[i]
3. Extend previous min: min \* nums[i] (important when nums[i] is negative)

So:

```python
newMax = max(nums[i], max * nums[i], min * nums[i]) newMin = min(nums[i], max * nums[i], min * nums[i])
```

Then:

- update global result using newMax
- move forward

This makes the algorithm **O(n)** while still exploring all meaningful paths.

```c
int min = nums[0];
int max = nums[0];
int result = max;

for(int i = 1; i < nums.length; i++){
    int cur = nums[i];

    int temp = Math.max(cur, Math.max(max * cur, min * cur));
    min = Math.min(cur, Math.min(min * cur, max * cur));
    max = temp;

    result = Math.max(result, max);
}

```

## Dynamic programming

It is nothing but recurssion of graph and memory where we do same thing again and again

Let say we have coins 2,3,5 and we need to find the no of ways we can make 8

so let say 2 is the last coin if we add that we get our target then we have 6 ruppe balance in that 6 rupee we need to how many ways using 2,3,5 we can form 6 rupee and list will go keep

It is permutaion problem where we see same computation is done in multiple place instead of doing each time we can cache it

```js
function howManyWays(target, coins) {
  const memo = {} // memo[x] = number of ways to make x

  function dfs(remaining) {
    // If we already computed this value, return it
    if (memo[remaining] !== undefined) {
      return memo[remaining]
    }

    // Base case: exactly 0 remaining means 1 valid sequence
    if (remaining === 0) return 1

    // If negative, no solution
    if (remaining < 0) return 0

    // Try all coins as first coin
    let ways = 0
    for (const c of coins) {
      ways += dfs(remaining - c)
    }

    memo[remaining] = ways // store the result
    return ways
  }

  return dfs(target)
}

console.log(howManyWays(5, [1, 4, 5])) // Output: 4
```

if we need min sum

```js
function minCoins(target, coins) {
  const memo = {} // memo[x] = min coins to make x

  function dfs(remaining) {
    // If already computed
    if (memo[remaining] !== undefined) {
      return memo[remaining]
    }

    // If we hit exactly zero → no more coins needed
    if (remaining === 0) return 0

    // If negative → invalid
    if (remaining < 0) return Infinity

    let best = Infinity

    // Choose the coin that leads to minimum remaining coins
    for (const c of coins) {
      const result = dfs(remaining - c)
      best = Math.min(best, result + 1) // +1 because we used a coin
    }

    memo[remaining] = best
    return best
  }

  const ans = dfs(target)
  return ans === Infinity ? -1 : ans // If impossible
}

console.log(minCoins(5, [1, 4, 5])) // Output: 1
```

This similar to

```js
minCoins(x) = 1 + min(
    minCoins(x - 1),
    minCoins(x - 4),
    minCoins(x - 5)
)

```

### Backtracking vs DP

### BACKTRACKING = **Generate / Explore all possibilities**

- exploring all combinations, subsets, permutations
- searching through a decision tree
- producing all valid solutions
- path construction

Backtracking = **YES/NO branching** at each step.

### ✔ DP = **Optimize / Count / Decide**

DP answers:

- “Is it possible?”
- “What is the best?”
- “How many ways?”
- “What is the minimum cost?”
- “What is the maximum score?”
- “What is the longest/shortest?”

DP = compressing the search tree into states to avoid recomputation.

## Strings

Palindrome

- A plaindrome is nothing but except center they have common things

Every palindrome has:

- **Odd length:** one center (e.g., `"abcba"` → center at `c`)
- **Even length:** two-center boundary (e.g., `"abba"` → center between the two `b`'s)

Palindromic Substrings

```js
var countSubstrings = function (s) {
  let count = 0

  function expand(l, r) {
    while (l >= 0 && r < s.length && s[l] === s[r]) {
      count++
      l--
      r++
    }
  }

  for (let i = 0; i < s.length; i++) {
    expand(i, i) // odd
    expand(i, i + 1) // even
  }

  return count
}
```

## Heap

A **binary heap** is a **complete binary tree** that satisfies a **heap property**:

- **Min-heap:** Every parent ≤ its children → smallest element is always at the root.
- **Max-heap:** Every parent ≥ its children → largest element is always at the root.

**Key consequences**

- No ordering guarantee between siblings.
- Tree is filled level-by-level, left to right.

### Array Representation (1-based indexing)

Index 0 is unused for clean mathematics.

For an element at index `i`:

- Left child = `2i`
- Right child = `2i + 1`
- Parent = `floor(i / 2)`

```
Array: [null, 20, 19, 17, 13, 15, 12, 16, 11, 10]

Tree view (max-heap):

          20 (1)
       /           \
    19 (2)        17 (3)
   /    \        /     \
13(4) 15(5)   12(6) 16(7)
 / \
11(8) 10(9)
```

#### Insert (Min-Heap Example)

1. Append new value at end of array.
2. **Bubble up** while it is smaller than its parent.
3. Swap with parent until heap property holds.

Mechanism:

```
Insert x → place at end → while x < parent(x): swap
```

#### Remove (Min-Heap Example)

1. Remove root (smallest).
2. Move last element to root.
3. **Bubble down** by swapping with smaller child until heap property holds.

Mechanism:

```
Remove root → replace with last → while node > child: swap with smaller child
```

## Backtracking

Backtracking is a recursion pattern that:

- Maintains _state variables_ describing a partial solution.
- **Explores** possible next choices by making those state updates and recursing.
- **Detects invalid/complete states** (prune or accept).
- **Reverts** the state (or uses immutable copies) to try the next choice.

Mechanically: recursion frames hold local copies (or you mutate+undo) of the state. You only descend into calls that satisfy constraints.

Generate all valid Parentheses

So let say if they give n=2 we need to generate all valid paranetessi

```
(()) ()()
```

### Constraints reasoning

- We never allow `close > open` at any prefix (that would be invalid).
- We never allow `open > n` or `close > n`.  
   Those are _local constraints_ evaluating only on the current state, enabling pruning.

Every partial string is a node; edges are choosing `'('` or `')'`. The full space is a binary tree of depth `2n`, but constraints prune huge parts of it. The number of valid leaves is the nth Catalan number (not exponential like 2^(2n) in practice for valid results).

Solution

1. We need to construct strings length `2n` using `'('` and `')'`.
2. Let state be `(s, open, close)` where
   - `s` = current string (length `open + close`)
   - `open` = number of `'('` used
   - `close` = number of `')'` used
3. Terminal condition: if `open + close == 2n`, then `s` is complete → add to results.
4. Legal moves:
   - Add `'('` if `open < n`.
   - Add `')'` if `close < open` (ensures prefix constraint).
5. Why those moves are _necessary_:
   - Must never exceed `n` opens.
   - Must never close more than opened (local prune).
6. Recursively apply choices; after returning, undo (if mutating) or let the recursion frame discard local copy.

These rules exactly capture minimal necessary constraints and will generate each valid string exactly once.

- **State vector:** `(s, open, close)` — minimal sufficient information.
- **Invariant at every node:** `0 ≤ close ≤ open ≤ n` and `len(s) = open + close`.
- **Why invariant matters:** If `close > open`, no completion can be valid — prune immediately.
- **What would break:** Removing the `close < open` rule will produce invalid strings and require post-filtering or more checks later. Removing `open < n` would try invalid opens beyond required and complicate termination.

```js
// Generate Parentheses - LeetCode 22
function generateParenthesis(n) {
  const res = []
  function backtrack(s, open, close) {
    if (s.length === 2 * n) {
      res.push(s)
      return
    }
    // If we can still add '(' -> try it
    if (open < n) {
      backtrack(s + "(", open + 1, close)
    }
    // We can add ')' only if it won't break validity
    if (close < open) {
      backtrack(s + ")", open, close + 1)
    }
  }
  backtrack("", 0, 0)
  return res
}

// Example
console.log(generateParenthesis(3))
// ["((()))","(()())","(())()","()(())","()()()"]
```

#### Generate All Subsets Whose Sum Equals a Target

we need take decsion does we need to include this number or not and keep tracking

#### subset generation backtracking

It's a method to **generate all possible subsets** (a.k.a. the **power set**) of a given set or array.

array = [1,2,3]

```js
;([], [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3])
```

bruteforce

```js
function subsets(nums) {
  const res = [[]]
  for (const num of nums) {
    const len = res.length
    for (let i = 0; i < len; i++) {
      res.push([...res[i], num])
    }
  }
  return res
}

console.log(subsets([1, 2]))
// Output: [ [], [1], [2], [1,2] ]
```

We iterating through each number and adding that number to exist subset and creating this as

- Time = O(n \* 2^n)

Backtracking

```js
function subsetsBacktrack(nums) {
  const res = [];

  function backtrack(index, path) {
    res.push([...path]);
    for (let i = index; i < nums.length; i++) {
      path.push(nums[i]);                 // include
      backtrack(i + 1, path);             // recurse
      path.pop();                         // exclude (backtrack)
    }
  }

  backtrack(0, []);
  return res;
}

console.log(subsetsBacktrack([1, 2]));
// Output: [ [], [1], [1,2], [2] ]


Start: []

├── [1]
│   ├── [1,2]
│   │   └── [1,2,3]
│   └── [1,3]
├── [2]
│   └── [2,3]
└── [3]


           []
         /    \
      [1]      []
     /   \    /   \
 [1,2] [1]  [2]   []


method2
function subsetsBacktrack(nums) {
  const res = [];

  function backtrack(index, path) {
    res.push(path);
    for (let i = index; i < nums.length; i++) {
      backtrack(i + 1, [...path, nums[i]]);
    }
  }

  backtrack(0, []);
  return res;
}

console.log(subsetsBacktrack([1, 2]));

```

- In recurrsio it go depth first and then comeback

### Template for backtrack

- For backtrack problem we explore all path it just a decision tree where we take dicision does we need to include this number or not and we try explore path by include the number and not include by backtracking ,
- Some time we have constraint that will have some condition

Note:

We can achevie Backtracking in two ways

Backtracking is exactly DFS over an _implicit_ tree where:

- each node = a state
- each edge = a decision
- each branch = a complete solution (or dead end)

There is **no actual tree stored in memory** recursion (or a manual stack) simulates DFS.

```javascript
var generateParenthesis = function (n) {
  const result = []
  const temp = []

  function backtrack(openCount, closeCount) {
    // if we built a full sequence
    if (temp.length === n * 2) {
      result.push(temp.join(""))
      return
    }

    // try adding "("
    if (openCount < n) {
      temp.push("(")
      backtrack(openCount + 1, closeCount)
      temp.pop()
    }

    // try adding ")"
    if (closeCount < openCount) {
      temp.push(")")
      backtrack(openCount, closeCount + 1)
      temp.pop()
    }
  }

  backtrack(0, 0)
  return result
}

console.log(generateParenthesis(3))
```

**Triggering two children at the same time with different states**

At any state, we can _branch_ by generating:

- nextState1 → stack.push(nextState1)
- nextState2 → stack.push(nextState2)

Each child gets its own:

- updated partial solution (`temp`)
- updated decision counts (like openCount/closeCount)
- updated constraint state

This ensures branches are **independent**.

```js
var generateParenthesis = function (n) {
  const result = []

  function backtrack(curr, open, close) {
    if (curr.length === n * 2) {
      result.push(curr)
      return
    }

    if (open < n) {
      backtrack(curr + "(", open + 1, close)
    }

    if (close < open) {
      backtrack(curr + ")", open, close + 1)
    }
  }

  backtrack("", 0, 0)
  return result
}
```
