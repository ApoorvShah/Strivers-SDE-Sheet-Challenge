# Sorting

## What is Sorting?
Sorting is arranging elements in a specific order (usually ascending or descending). Think of it like organizing books on a shelf by name or organizing cards in your hand by number!

## When to Use Sorting?
- Need data in order for processing
- Searching becomes faster (binary search)
- Finding duplicates easier
- Many algorithms work better on sorted data
- Organizing data for humans to read

## Common Sorting Algorithms

### Simple Sorts (O(n²))
1. **Bubble Sort** - Repeatedly swap adjacent elements
2. **Selection Sort** - Find minimum, put in position
3. **Insertion Sort** - Insert each element in correct position

### Efficient Sorts (O(n log n))
4. **Merge Sort** - Divide, sort, merge
5. **Quick Sort** - Pick pivot, partition, recurse
6. **Heap Sort** - Build heap, extract max repeatedly

### Special Sorts
7. **Counting Sort** - Count occurrences (for limited range)
8. **Radix Sort** - Sort digit by digit

## Common Problems You Can Solve

1. **Sort array** - Basic sorting
2. **Sort 0s, 1s, 2s** - Dutch National Flag problem
3. **Merge intervals** - Combine overlapping intervals
4. **Count inversions** - Pairs where arr[i] > arr[j] and i < j
5. **Sorting with custom comparator** - Sort by multiple criteria

## How to Develop Solutions

### Step 1: Choose Right Algorithm

**When to use which?**
- **Bubble/Selection/Insertion**: Small arrays, educational
- **Merge Sort**: Need stable sort, linked lists
- **Quick Sort**: Average case, in-place sorting
- **Heap Sort**: Guaranteed O(n log n), space-constrained
- **Counting/Radix**: Limited range integers

### Step 2: Common Sorting Techniques

**Merge Sort** (Divide and Conquer)
```
mergeSort(arr, left, right):
  if left >= right: return

  mid = (left + right) / 2
  mergeSort(arr, left, mid)      # Sort left half
  mergeSort(arr, mid+1, right)   # Sort right half
  merge(arr, left, mid, right)   # Merge sorted halves

merge(arr, left, mid, right):
  Create temp arrays for left and right
  Compare elements, put smaller in arr
  Copy remaining elements
```

**Quick Sort** (Pivot and Partition)
```
quickSort(arr, low, high):
  if low >= high: return

  pivotIndex = partition(arr, low, high)
  quickSort(arr, low, pivotIndex - 1)
  quickSort(arr, pivotIndex + 1, high)

partition(arr, low, high):
  pivot = arr[high]
  i = low - 1
  for j from low to high-1:
    if arr[j] <= pivot:
      i++
      swap arr[i] and arr[j]
  swap arr[i+1] and arr[high]
  return i + 1
```

### Example Logic

**Problem**: Sort array of 0s, 1s, 2s (Dutch National Flag)
```
Approach: Three pointers
low = 0, mid = 0, high = n-1

while mid <= high:
  if arr[mid] == 0:
    swap arr[low] and arr[mid]
    low++, mid++
  else if arr[mid] == 1:
    mid++
  else:  // arr[mid] == 2
    swap arr[mid] and arr[high]
    high--

All 0s before low, all 1s between low and mid,
all 2s after high
```

**Problem**: Count inversions (brute force vs merge sort)
```
Brute Force O(n²):
count = 0
for i from 0 to n-1:
  for j from i+1 to n:
    if arr[i] > arr[j]:
      count++

Using Merge Sort O(n log n):
During merge step, if left[i] > right[j]:
  This means left[i] > all remaining in right
  inversions += (mid - i + 1)
```

**Problem**: Merge overlapping intervals
```
Approach: Sort then merge
1. Sort intervals by start time
2. Create result list
3. For each interval:
   - If overlaps with last in result:
     - Merge them (extend end time)
   - Else:
     - Add as new interval
4. Return result

Example: [[1,3], [2,6], [8,10]]
Sort: Already sorted
Process:
  [1,3] - add to result
  [2,6] - overlaps with [1,3] → merge to [1,6]
  [8,10] - no overlap → add to result
Result: [[1,6], [8,10]]
```

## Comparison of Algorithms

| Algorithm      | Time (Avg) | Time (Worst) | Space  | Stable? |
|----------------|------------|--------------|--------|---------|
| Bubble Sort    | O(n²)      | O(n²)        | O(1)   | Yes     |
| Selection Sort | O(n²)      | O(n²)        | O(1)   | No      |
| Insertion Sort | O(n²)      | O(n²)        | O(1)   | Yes     |
| Merge Sort     | O(n log n) | O(n log n)   | O(n)   | Yes     |
| Quick Sort     | O(n log n) | O(n²)        | O(log n)| No     |
| Heap Sort      | O(n log n) | O(n log n)   | O(1)   | No      |

**Stable** = Maintains relative order of equal elements

## Tips for Solving

1. **Ask if you can modify the array** (in-place vs new array)
2. **Check for special cases** (all same, already sorted)
3. **Consider built-in sort** for interviews (unless asked to implement)
4. **Two pointer technique** works well with sorted arrays

## Time Complexity Tips
- Simple sorts: O(n²) - okay for small n (< 100)
- Efficient sorts: O(n log n) - standard for most cases
- Counting/Radix: O(n) - when range is limited
- Sorting enables O(log n) binary search!
