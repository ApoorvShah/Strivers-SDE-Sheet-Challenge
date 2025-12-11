# Dynamic Programming (DP)

## What is Dynamic Programming?
Dynamic Programming is a technique to solve problems by breaking them into smaller overlapping subproblems, solving each once, and storing results to avoid recalculation. Think of it like saving your work instead of redoing calculations!

## When to Use DP?
- Problem can be broken into overlapping subproblems
- Problem has optimal substructure (optimal solution uses optimal solutions of subproblems)
- You're recalculating the same things multiple times
- Choices lead to subproblems with similar structure

## Common Problems You Can Solve

1. **Fibonacci** - Classic DP example
2. **Knapsack** - Maximize value with weight constraint
3. **Longest Common Subsequence** - Find longest common sequence
4. **Edit Distance** - Minimum edits to transform one string to another
5. **Coin Change** - Minimum coins to make amount
6. **Path problems** - Minimum/maximum path sum in grid
7. **Rod cutting** - Maximize profit by cutting rod

## How to Develop Solutions

### Step 1: Identify DP Problem
Ask yourself:
- Am I solving same subproblem multiple times?
- Can I make choices that lead to smaller versions of same problem?
- Does optimal solution depend on optimal solutions of smaller problems?

### Step 2: Define the State
- What information do I need to track?
- Usually index, remaining capacity, current position, etc.
- Example: `dp[i]` = answer for first i elements

### Step 3: Find Recurrence Relation
- How does current state depend on previous states?
- What choices can I make?
- Example: `dp[i] = dp[i-1] + dp[i-2]` (Fibonacci)

### Step 4: Choose Approach

**Top-Down (Memoization)** - Recursion + Cache
```
1. Write recursive solution
2. Add cache to store results
3. Check cache before computing
```

**Bottom-Up (Tabulation)** - Iterative
```
1. Create DP table
2. Fill base cases
3. Fill table using recurrence relation
4. Answer is in final cell
```

### Example Logic

**Problem**: Fibonacci number
```
Top-Down:
fib(n):
  if n in cache: return cache[n]
  if n <= 1: return n
  cache[n] = fib(n-1) + fib(n-2)
  return cache[n]

Bottom-Up:
dp[0] = 0, dp[1] = 1
for i from 2 to n:
  dp[i] = dp[i-1] + dp[i-2]
return dp[n]
```

**Problem**: Coin Change (minimum coins)
```
Bottom-Up:
dp[0] = 0  (0 coins for amount 0)
for amount from 1 to target:
  dp[amount] = infinity
  for each coin:
    if coin <= amount:
      dp[amount] = min(dp[amount],
                       1 + dp[amount - coin])
```

**Problem**: 0/1 Knapsack
```
State: dp[i][w] = max value using first i items
                  with weight limit w
Recurrence:
  If weight[i] > w: can't take item
    dp[i][w] = dp[i-1][w]
  Else: choose max of take or don't take
    dp[i][w] = max(dp[i-1][w],  // don't take
                   value[i] + dp[i-1][w-weight[i]])  // take
```

### Step 5: Optimize Space
- Often can reduce 2D DP to 1D
- Only need previous row/column
- Example: Fibonacci only needs last 2 values

## Common DP Patterns

1. **Linear DP**: One dimension (climbing stairs, house robber)
2. **2D DP**: Two dimensions (grid paths, LCS, edit distance)
3. **Subset DP**: Choose or not choose (knapsack, subset sum)
4. **Interval DP**: Solve for all intervals (matrix chain, palindrome partition)
5. **State Machine DP**: Different states (buy/sell stock)

## Tips for Solving

1. Start with recursive solution
2. Identify repeated calculations
3. Add memoization
4. Convert to bottom-up if needed
5. Optimize space
6. Don't forget base cases!

## Time Complexity Tips
- Usually O(number of states × time per state)
- 1D DP: Often O(n)
- 2D DP: Often O(n × m)
- With memoization: Each state computed once
- Much better than exponential brute force!
