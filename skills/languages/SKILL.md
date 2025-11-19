---
name: programming-languages
description: Master programming languages, data structures, algorithms, and computer science fundamentals. Use for learning core programming concepts and problem-solving skills.
---

# Programming Languages & Fundamentals Skill

Build strong programming foundations and solve algorithmic problems.

## Quick Start

Solve a classic algorithm problem:

```python
# Binary Search
def binary_search(arr, target):
    left, right = 0, len(arr) - 1

    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1

# Usage
arr = [1, 3, 5, 7, 9, 11]
print(binary_search(arr, 7))  # Output: 3
```

## Data Structures

### Arrays & Lists
```python
arr = [1, 2, 3, 4, 5]
arr.append(6)        # O(1)
arr.insert(0, 0)     # O(n)
arr.pop()            # O(1)
arr[2]               # O(1) access
```

### Linked Lists
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        node = Node(data)
        if not self.head:
            self.head = node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = node
```

### Stacks & Queues
```python
# Stack (LIFO)
stack = []
stack.append(1)      # Push
stack.pop()          # Pop

# Queue (FIFO)
from collections import deque
queue = deque()
queue.append(1)      # Enqueue
queue.popleft()      # Dequeue
```

### Trees
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

# Tree traversals
def inorder(node):      # Left, Root, Right
    if not node:
        return
    inorder(node.left)
    print(node.val)
    inorder(node.right)

def preorder(node):     # Root, Left, Right
    if not node:
        return
    print(node.val)
    preorder(node.left)
    preorder(node.right)

def postorder(node):    # Left, Right, Root
    if not node:
        return
    postorder(node.left)
    postorder(node.right)
    print(node.val)
```

### Hash Tables
```python
# Dictionary/HashMap
hash_map = {}
hash_map['key'] = 'value'   # O(1) insert
value = hash_map['key']      # O(1) lookup
del hash_map['key']          # O(1) delete
```

## Algorithm Patterns

### Sorting Algorithms
```python
# QuickSort - O(n log n) average
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quicksort(left) + middle + quicksort(right)

# Merge Sort - O(n log n)
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)
```

### Dynamic Programming
```python
# Fibonacci - Memoization
def fib(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fib(n-1, memo) + fib(n-2, memo)
    return memo[n]

# Coin Change
def coin_change(coins, amount):
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0

    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] = min(dp[i], dp[i - coin] + 1)

    return dp[amount] if dp[amount] != float('inf') else -1
```

### Two Pointers
```python
# Two Sum Sorted
def two_sum(arr, target):
    left, right = 0, len(arr) - 1

    while left < right:
        current_sum = arr[left] + arr[right]
        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1
        else:
            right -= 1

    return []
```

## Complexity Analysis

### Big O Notation
```
O(1)     - Constant time
O(log n) - Logarithmic (binary search)
O(n)     - Linear (simple loop)
O(n log n) - Linearithmic (merge sort)
O(n²)    - Quadratic (nested loops)
O(2ⁿ)    - Exponential (subset generation)
O(n!)    - Factorial (permutations)
```

### Amortized Analysis
```python
# Dynamic array growth
class DynamicArray:
    def __init__(self):
        self.capacity = 1
        self.size = 0
        self.arr = [0] * 1

    def append(self, val):
        if self.size == self.capacity:
            self.capacity *= 2
            new_arr = [0] * self.capacity
            for i in range(self.size):
                new_arr[i] = self.arr[i]
            self.arr = new_arr

        self.arr[self.size] = val
        self.size += 1
```

## OOP Principles

### SOLID

```python
# Single Responsibility
class UserService:
    def get_user(self, user_id):
        pass

# Open/Closed
class Shape:
    def area(self):
        raise NotImplementedError

class Circle(Shape):
    def area(self):
        return 3.14 * self.radius ** 2

# Liskov Substitution
class Bird:
    def fly(self):
        pass

class Sparrow(Bird):
    def fly(self):
        return "Flying"

# Interface Segregation
class Flyer:
    def fly(self):
        pass

class Swimmer:
    def swim(self):
        pass

# Dependency Inversion
class Logger:
    def log(self, message):
        pass

class UserService:
    def __init__(self, logger: Logger):
        self.logger = logger
```

## Programming Languages Comparison

| Language | Use Case | Learning Curve | Performance |
|----------|----------|-----------------|-------------|
| Python | Data science, web, scripting | Easy | Moderate |
| JavaScript | Web (frontend/backend) | Easy-Medium | Moderate |
| Go | Cloud, microservices | Medium | High |
| Rust | Systems, performance | Hard | Very High |
| Java | Enterprise, Android | Medium | High |
| C++ | Games, systems | Hard | Very High |

## Practice Resources

**Coding Challenges:**
- [LeetCode](https://leetcode.com) - 2000+ problems
- [HackerRank](https://hackerrank.com) - Structured learning
- [CodeWars](https://codewars.com) - Game-based learning
- [Codeforces](https://codeforces.com) - Competitive programming

**Algorithm Visualizations:**
- [Visualgo](https://visualgo.net) - Algorithm visualization
- [Sorting Algorithms](https://www.sortvisualizer.com) - Visual sorting

## Study Plan (3-6 months)

**Month 1-2: Fundamentals**
- Basic data structures
- Simple algorithms
- Complexity analysis
- 50 easy problems

**Month 3-4: Intermediate**
- Advanced data structures
- Dynamic programming
- Graph algorithms
- 50 medium problems

**Month 5-6: Advanced**
- Complex patterns
- System design basics
- 50 hard problems
- Mock interviews

## Common Interview Questions

**Easy Level:**
- Two Sum, Palindrome, Merge Sorted Arrays
- Reverse String, Valid Parentheses

**Medium Level:**
- Longest Substring, Median of Two Sorted Arrays
- Number of Islands, Longest Increasing Subsequence

**Hard Level:**
- Trapping Rain Water, Word Ladder II
- Median Finder, LRU Cache

## Tips for Success

✅ Understand before memorizing
✅ Practice writing code by hand
✅ Analyze time/space complexity
✅ Start with simpler problems
✅ Explain your approach clearly
✅ Code clean and readable
✅ Test edge cases
✅ Practice regularly (daily)
✅ Review failed problems
✅ Learn from others' solutions
