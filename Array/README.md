# Array

## What is an Array?
An array is a collection of elements stored in consecutive memory locations. Think of it like a row of boxes, each holding a value, and each box has a number (index) starting from 0.

## When to Use Arrays?
- When you need to store multiple items of the same type
- When you know the size beforehand (or can estimate it)
- When you need fast access to elements using their position

## Common Problems You Can Solve

1. **Finding elements** - Search for duplicates, missing numbers, or specific values
2. **Subarray problems** - Find subarrays with certain properties (max sum, specific length)
3. **Two pointer technique** - Find pairs, triplets that satisfy conditions
4. **Sliding window** - Problems involving consecutive elements
5. **Matrix operations** - 2D arrays for grid-based problems

## How to Develop Solutions

### Step 1: Understand the Problem
- What are we looking for? (max, min, count, exists?)
- What are the constraints? (sorted? positive numbers?)

### Step 2: Choose Your Approach
- **Brute Force**: Try all possibilities (nested loops)
- **Two Pointers**: Use two indices moving toward each other
- **Sliding Window**: Move a window of fixed/variable size
- **HashMap**: Store values for quick lookup

### Step 3: Think About Edge Cases
- Empty array
- Single element
- All elements same
- Negative numbers

### Example Logic
**Problem**: Find two numbers that add up to a target
```
Approach: Use HashMap
1. Create empty map
2. For each number:
   - Calculate needed = target - current number
   - If needed exists in map, found answer!
   - Otherwise, add current number to map
```

## Time Complexity Tips
- Accessing element by index: O(1) - very fast!
- Searching unsorted array: O(n) - check all elements
- Sorting array: O(n log n) - using good algorithms
