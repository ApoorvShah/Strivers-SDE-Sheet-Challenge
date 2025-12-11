# LinkedList

## What is a LinkedList?
A linked list is a chain of nodes, where each node contains data and a reference (link) to the next node. Think of it like a treasure hunt where each clue points to the next location.

## When to Use LinkedList?
- When you need frequent insertions/deletions at beginning or middle
- When size changes frequently
- When you don't need random access (accessing by index)

## Common Problems You Can Solve

1. **Reversal** - Reverse the entire list or parts of it
2. **Cycle detection** - Find if list loops back on itself
3. **Merging** - Combine two sorted lists
4. **Finding middle** - Fast and slow pointer technique
5. **Removing nodes** - Delete specific nodes or duplicates
6. **Flattening** - Merge multilevel lists

## How to Develop Solutions

### Step 1: Understand Node Structure
```
Node has:
- data (the value)
- next (pointer to next node)
- head points to first node
- null/None marks the end
```

### Step 2: Common Techniques
- **Two Pointers**: Fast and slow (find middle, detect cycle)
- **Dummy Node**: Simplifies edge cases (empty list, single node)
- **Recursion**: Clean solutions for reversal, merging
- **In-place Modification**: Change links without extra space

### Step 3: Always Consider
- What if list is empty? (head = null)
- What if only one node?
- How to handle last node? (next = null)

### Example Logic
**Problem**: Find middle of linked list
```
Approach: Fast and Slow Pointers
1. Create slow pointer at head
2. Create fast pointer at head
3. While fast can move 2 steps:
   - Move slow 1 step
   - Move fast 2 steps
4. When fast reaches end, slow is at middle!
```

**Problem**: Detect cycle in list
```
Approach: Floyd's Algorithm
1. Start slow and fast at head
2. Move slow 1 step, fast 2 steps
3. If they meet, cycle exists!
4. If fast reaches null, no cycle
```

## Time Complexity Tips
- Access by index: O(n) - must traverse from head
- Insert at beginning: O(1) - just change head
- Insert at end: O(n) - must reach end first
- Delete node (given pointer): O(1) - change links
- Search: O(n) - check each node
