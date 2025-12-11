# Stack

## What is a Stack?
A stack is a Last-In-First-Out (LIFO) data structure. Think of it like a stack of plates - you can only add or remove from the top!

## When to Use Stack?
- When you need to reverse something
- When you need to track "going back" (like browser history)
- When matching pairs (parentheses, brackets)
- When you need most recent item first

## Common Problems You Can Solve

1. **Balanced parentheses** - Check if brackets are properly matched
2. **Next greater/smaller element** - Find next larger element for each item
3. **Expression evaluation** - Calculate mathematical expressions
4. **Histogram problems** - Largest rectangle in histogram
5. **Stock span** - Days since stock price was higher
6. **Undo operations** - Track recent actions

## How to Develop Solutions

### Step 1: Understand Stack Operations
```
push(item)  - Add item to top
pop()       - Remove and return top item
peek()/top()- Look at top without removing
isEmpty()   - Check if stack is empty
```

### Step 2: Think "Last In, First Out"
- Most recently added item is first to come out
- Like a pile of books - you take from top

### Step 3: Common Patterns
- **Matching pairs**: Push opening, pop when closing
- **Next greater**: Push indices, pop when found greater
- **Monotonic stack**: Keep stack sorted (increasing/decreasing)

### Example Logic
**Problem**: Check balanced parentheses "(())"
```
Approach: Stack matching
1. Create empty stack
2. For each character:
   - If opening bracket '(' → push to stack
   - If closing bracket ')' → pop from stack
   - If pop fails or doesn't match → invalid
3. At end, stack should be empty
```

**Problem**: Next greater element
```
Approach: Monotonic decreasing stack
1. Create empty stack and result array
2. Traverse from right to left:
   - While stack not empty AND top ≤ current:
     - Pop (they're not greater)
   - If stack empty: no greater element
   - Else: top is next greater
   - Push current to stack
```

## Time Complexity Tips
- Push: O(1)
- Pop: O(1)
- Peek: O(1)
- Most stack problems: O(n) - single pass through data
