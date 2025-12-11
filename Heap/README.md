# Heap (Priority Queue)

## What is a Heap?
A heap is a special tree-based data structure where parent nodes are always greater (Max-Heap) or smaller (Min-Heap) than their children. Think of it like a tournament bracket where the winner (max/min) is always at the top!

## When to Use Heap?
- When you need the largest or smallest element quickly
- When processing items by priority (not just order)
- For continuous stream of data where you need min/max
- For K-largest or K-smallest problems

## Common Types
- **Min-Heap**: Parent < Children (smallest at top)
- **Max-Heap**: Parent > Children (largest at top)
- **Priority Queue**: Abstract type usually implemented with heap

## Common Problems You Can Solve

1. **Kth largest/smallest** - Find Kth largest element in array
2. **Median in stream** - Find median as numbers come in
3. **Merge K sorted arrays** - Efficiently merge multiple sorted lists
4. **Top K frequent** - Find K most frequent elements
5. **Heap sort** - Sort using heap
6. **Task scheduling** - Process highest priority tasks first

## How to Develop Solutions

### Step 1: Understand Heap Operations
```
insert(value)  - Add value, maintain heap property: O(log n)
extractMin()   - Remove and return smallest (min-heap): O(log n)
extractMax()   - Remove and return largest (max-heap): O(log n)
peek()         - View top without removing: O(1)
```

### Step 2: Heap Property
**Min-Heap**: parent ≤ children
```
       1
      / \
     3   2
    / \
   5   4
```

**Max-Heap**: parent ≥ children
```
       9
      / \
     7   8
    / \
   3   5
```

### Step 3: Common Patterns

**K largest elements**: Use Min-Heap of size K
- Keep smallest of K largest at top
- If new element > top, replace top

**K smallest elements**: Use Max-Heap of size K
- Keep largest of K smallest at top
- If new element < top, replace top

**Median finding**: Use 2 heaps
- Max-heap for smaller half
- Min-heap for larger half
- Median is at tops of heaps

### Example Logic
**Problem**: Find Kth largest element
```
Approach: Min-Heap of size K
1. Create min-heap of size K
2. Add first K elements to heap
3. For remaining elements:
   - If element > heap top (smallest of K largest)
     - Remove top
     - Add this element
4. Heap top is Kth largest!
```

**Problem**: Merge K sorted arrays
```
Approach: Min-Heap
1. Create min-heap
2. Add first element from each array (with array index)
3. While heap not empty:
   - Extract min (it's next in sorted order)
   - Add to result
   - Add next element from same array to heap
4. Result is merged sorted array
```

**Problem**: Find median in stream
```
Approach: Two heaps
1. Max-heap for lower half
2. Min-heap for upper half
3. Balance heaps (size difference ≤ 1)
4. Median = top of larger heap
   OR average of both tops if equal size
```

## Time Complexity Tips
- Insert: O(log n)
- Extract min/max: O(log n)
- Peek: O(1)
- Build heap from array: O(n)
- Heap sort: O(n log n)
- Finding Kth largest with heap: O(n log K)
