# Binary Search

## What is Binary Search?
Binary Search is a fast searching algorithm that works by repeatedly dividing the search space in half. Think of it like guessing a number 1-100 - you'd pick 50, then based on "higher/lower", you'd pick 25 or 75, cutting possibilities in half each time!

## When to Use Binary Search?
- Data is SORTED (or can be sorted)
- Looking for specific value or condition
- Can divide problem into halves
- Need O(log n) instead of O(n) search

## Common Problems You Can Solve

1. **Classic search** - Find element in sorted array
2. **First/Last occurrence** - Find boundaries of target
3. **Search in rotated array** - Array sorted then rotated
4. **Square root** - Find integer square root
5. **Aggressive cows** - Maximize minimum distance
6. **Book allocation** - Minimize maximum pages
7. **Median of two sorted arrays** - Find combined median

## How to Develop Solutions

### Step 1: Basic Binary Search Template
```
left = 0
right = array.length - 1

while left <= right:
  mid = left + (right - left) / 2

  if array[mid] == target:
    found! return mid
  else if array[mid] < target:
    left = mid + 1   # Search right half
  else:
    right = mid - 1  # Search left half

return -1  # Not found
```

### Step 2: Key Insights
- **Halves the search space each iteration**
- **Works on monotonic functions** (increasing/decreasing)
- **Need to define search space** (low, high)
- **Need to define condition** (what are we looking for?)

### Step 3: Binary Search on Answer
Not just for finding elements! Can find optimal answer:
```
Binary search on possible answers:
1. Define range of possible answers (low to high)
2. For each mid value:
   - Check if mid is valid answer
   - Based on result, adjust range
3. Converge to optimal answer
```

### Example Logic

**Problem**: Find square root (integer)
```
Approach: Binary search on answer
1. Search space: 0 to n
2. For each mid:
   - If mid * mid == n: found!
   - If mid * mid < n: answer might be larger
   - If mid * mid > n: answer is smaller
3. Keep track of last valid answer

left = 0, right = n
while left <= right:
  mid = (left + right) / 2
  if mid * mid == n: return mid
  if mid * mid < n:
    ans = mid        # This could be answer
    left = mid + 1
  else:
    right = mid - 1
```

**Problem**: First occurrence of element
```
Approach: Binary search with tracking
left = 0, right = n-1
firstPos = -1

while left <= right:
  mid = (left + right) / 2
  if arr[mid] == target:
    firstPos = mid      # Found one, but check left
    right = mid - 1     # Continue searching left
  else if arr[mid] < target:
    left = mid + 1
  else:
    right = mid - 1

return firstPos
```

**Problem**: Aggressive Cows (maximize minimum distance)
```
Approach: Binary search on distance
1. Search space: 1 to (max position - min position)
2. For each distance:
   - Try to place cows with that minimum distance
   - If successful: try larger distance
   - If failed: try smaller distance

canPlaceCows(positions, cows, minDist):
  place first cow at position 0
  for each position:
    if distance from last cow >= minDist:
      place cow here
  return if all cows placed

Binary search:
left = 1, right = maxPos - minPos
while left <= right:
  mid = (left + right) / 2
  if canPlaceCows(positions, cows, mid):
    ans = mid
    left = mid + 1   # Try larger distance
  else:
    right = mid - 1  # Try smaller distance
```

**Problem**: Book Allocation (minimize maximum pages)
```
Approach: Binary search on maximum pages
1. Search space: max(pages) to sum(pages)
2. For each maxPages:
   - Try to allocate books with this limit
   - If possible: try smaller limit
   - If not: need larger limit

canAllocate(books, students, maxPages):
  currentStudent = 1
  currentPages = 0
  for each book:
    if currentPages + book > maxPages:
      currentStudent++
      currentPages = book
      if currentStudent > students: return false
    else:
      currentPages += book
  return true
```

## Common Patterns

1. **Find exact match**: Classic binary search
2. **Find first/last occurrence**: Keep searching after finding
3. **Binary search on answer**: Search range of possible answers
4. **Rotated array**: Identify which half is sorted
5. **2D matrix**: Treat as 1D array with index conversion

## Tips for Solving

1. **Check if sorted** (or can be made monotonic)
2. **Define search space** clearly
3. **Avoid infinite loops**: Use `left + (right - left) / 2`
4. **Watch out for**: `left <= right` vs `left < right`
5. **Test edge cases**: Empty array, single element, target not found

## Time Complexity Tips
- Binary Search: O(log n) - divides by 2 each time
- Linear Search: O(n) - checks each element
- Example: Array of 1 million elements
  - Linear: Up to 1,000,000 checks
  - Binary: At most 20 checks! (log₂ 1,000,000 ≈ 20)
- Space: O(1) iterative, O(log n) recursive
