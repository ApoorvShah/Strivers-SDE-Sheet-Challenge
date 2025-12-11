# Backtracking

## What is Backtracking?
Backtracking is a technique to solve problems by trying all possibilities, and "backing up" when you hit a dead end. Think of it like solving a maze - you try a path, and if it doesn't work, you go back and try another!

## When to Use Backtracking?
- Need to find ALL possible solutions
- Need to explore all combinations/permutations
- Problem has constraints that eliminate many possibilities
- Can build solution incrementally and check validity

## Common Problems You Can Solve

1. **N-Queens** - Place N queens on chessboard (no attacks)
2. **Sudoku Solver** - Fill grid following Sudoku rules
3. **Permutations** - Generate all arrangements
4. **Combinations** - Generate all selections
5. **Subset Sum** - Find subsets that sum to target
6. **Rat in Maze** - Find path through maze
7. **M-Coloring** - Color graph with M colors
8. **Word Break** - Split string into valid words

## How to Develop Solutions

### Step 1: Understand the Structure
```
1. Make a choice
2. Explore that choice (recursion)
3. If it leads to solution: great!
4. If it fails: UNDO the choice (backtrack)
5. Try next choice
```

### Step 2: The Template
```
backtrack(state, choices):
  if is_solution(state):
    add state to results
    return

  for each choice in choices:
    if is_valid(choice, state):
      make_choice(choice)           # Choose
      backtrack(new_state, choices)  # Explore
      undo_choice(choice)            # Backtrack (Un-choose)
```

### Step 3: Three Key Steps
1. **Choose**: Make a choice, add to current path
2. **Explore**: Recursively explore with this choice
3. **Un-choose**: Remove choice, try next option

### Example Logic

**Problem**: Generate all permutations
```
Approach: Backtracking
permute(nums, current, result):
  if current is complete:
    add current to result
    return

  for each num in nums:
    if num not used:
      add num to current        # Choose
      mark num as used
      permute(nums, current)    # Explore
      remove num from current   # Un-choose
      mark num as unused
```

**Problem**: N-Queens
```
Approach: Backtracking row by row
solveNQueens(row, board):
  if row == N:
    found a solution!
    return

  for col in 0 to N-1:
    if isSafe(row, col):
      place queen at (row, col)     # Choose
      solveNQueens(row + 1, board)   # Explore next row
      remove queen from (row, col)   # Backtrack

isSafe(row, col):
  check no queen in same column
  check no queen in diagonal
```

**Problem**: Combination Sum
```
Approach: Backtracking with index
findCombinations(target, index, current, result):
  if target == 0:
    add current to result
    return
  if target < 0:
    return  # Invalid path

  for i from index to end:
    current.add(nums[i])              # Choose
    findCombinations(target - nums[i], i, current)  # Explore
    current.removeLast()              # Backtrack
```

**Problem**: Sudoku Solver
```
Approach: Backtracking cell by cell
solveSudoku(board):
  find empty cell (row, col)
  if no empty cell:
    solved!
    return true

  for num in 1 to 9:
    if isValid(board, row, col, num):
      board[row][col] = num          # Choose
      if solveSudoku(board):         # Explore
        return true
      board[row][col] = empty        # Backtrack

  return false  # No solution with current choices
```

## Key Concepts

### Pruning
- Cut off paths that can't lead to solution
- Makes backtracking faster
- Example: In N-Queens, don't try if position is attacked

### State Management
- Track current partial solution
- Track what's been used/visited
- Restore state when backtracking

### When to Backtrack
- Solution is complete (base case)
- Constraint violated (pruning)
- Tried all options from current state

## Optimization Tips

1. **Early termination**: Check constraints before recursing
2. **Pruning**: Eliminate impossible paths early
3. **Ordering**: Try most promising choices first
4. **Memoization**: Cache results for overlapping subproblems (becomes DP!)

## Time Complexity Tips
- Usually exponential: O(2^n) or O(n!)
- With pruning: Can be much better
- Space: O(depth of recursion)
- Examples:
  - Permutations: O(n!)
  - Subsets: O(2^n)
  - N-Queens: O(n!) with pruning

## Backtracking vs Brute Force
- Backtracking: Smarter brute force
- Prunes invalid paths early
- Doesn't waste time exploring dead ends
- Still tries all valid possibilities
