# Queue

## What is a Queue?
A queue is a First-In-First-Out (FIFO) data structure. Think of it like a line at a ticket counter - first person in line is first to be served!

## When to Use Queue?
- When order matters (first come, first served)
- When processing tasks in order they arrive
- Level-by-level traversal (like in trees)
- Implementing breadth-first search

## Common Problems You Can Solve

1. **Level order traversal** - Visit tree nodes level by level
2. **Sliding window maximum** - Find max in each window
3. **First non-repeating character** - In a stream of characters
4. **Task scheduling** - Process tasks in arrival order
5. **BFS in graphs** - Shortest path problems

## How to Develop Solutions

### Step 1: Understand Queue Operations
```
enqueue(item) - Add item to back/rear
dequeue()     - Remove and return front item
front()/peek()- Look at front without removing
isEmpty()     - Check if queue is empty
```

### Step 2: Think "First In, First Out"
- First added item is first to come out
- Like waiting in line - fair ordering

### Step 3: Types of Queues
- **Simple Queue**: Basic FIFO
- **Circular Queue**: Rear connects back to front
- **Deque**: Can add/remove from both ends
- **Priority Queue**: Items ordered by priority (see Heap)

### Example Logic
**Problem**: Level order traversal of tree
```
Approach: BFS using Queue
1. Create empty queue
2. Add root to queue
3. While queue not empty:
   - Remove front node
   - Process/print it
   - Add its left child to queue
   - Add its right child to queue
4. This processes level by level!
```

**Problem**: Sliding window maximum
```
Approach: Deque (double-ended queue)
1. Create deque to store indices
2. For each element:
   - Remove elements outside window from front
   - Remove smaller elements from back
   - Add current element index to back
   - Front of deque has maximum for this window
```

## Time Complexity Tips
- Enqueue: O(1)
- Dequeue: O(1)
- Front/Peek: O(1)
- BFS traversal: O(n) where n is number of nodes
