# Greedy Algorithms

## What is a Greedy Algorithm?
A greedy algorithm makes the locally optimal choice at each step, hoping to find a global optimum. Think of it like always picking the best immediate option without worrying about future consequences - sometimes it works perfectly!

## When to Use Greedy?
- Problem has greedy choice property (local optimum leads to global optimum)
- Making the best choice now doesn't prevent best solution later
- Usually involves optimization (maximize/minimize something)
- Simpler and faster than Dynamic Programming when it works

## Common Problems You Can Solve

1. **Activity selection** - Maximum non-overlapping activities
2. **Fractional knapsack** - Maximize value (can take fractions)
3. **Job scheduling** - Maximize profit or minimize delays
4. **Coin change** - Minimum coins (only works for certain coin systems)
5. **Huffman coding** - Optimal data compression
6. **Minimum platforms** - Minimum train platforms needed
7. **Meeting rooms** - Maximum meetings in one room

## How to Develop Solutions

### Step 1: Identify Greedy Choice
- What's the best immediate choice?
- Sort by some criteria (finish time, value/weight ratio, etc.)
- Common sorting criteria:
  - Earliest finish time
  - Highest value per unit
  - Shortest duration
  - Earliest deadline

### Step 2: Prove It Works (Or Doesn't)
Ask: Does picking the best now allow best overall?
- Some problems: Greedy works (activity selection)
- Some problems: Greedy fails, need DP (0/1 knapsack)

### Step 3: Common Pattern
```
1. Sort items by some criteria
2. Iterate through sorted items
3. If current item is compatible/valid:
   - Add to solution
   - Update state
4. Return solution
```

### Example Logic

**Problem**: Activity Selection (max non-overlapping)
```
Approach: Sort by finish time
1. Sort activities by finish time
2. Pick first activity
3. For remaining activities:
   - If start time ≥ last finish time:
     - Pick this activity
     - Update last finish time
4. Count of picked activities is answer

Why greedy works:
Finishing early leaves more time for other activities!
```

**Problem**: Fractional Knapsack
```
Approach: Sort by value/weight ratio
1. Calculate value per unit weight for each item
2. Sort by this ratio (highest first)
3. For each item:
   - If capacity remains:
     - Take as much as possible
     - Update capacity and total value
4. Return total value

Why greedy works:
Taking highest value per weight first is optimal
when fractions allowed!
```

**Problem**: Minimum Platforms
```
Approach: Sort arrivals and departures
1. Sort arrival times
2. Sort departure times separately
3. Track platforms in use:
   - If train arriving before earliest departure:
     - Need one more platform
   - Else: A platform is free
4. Track maximum platforms needed

Why greedy works:
We only care about peak overlap, not which specific trains!
```

**Problem**: Job Sequencing with Deadlines
```
Approach: Sort by profit (highest first)
1. Sort jobs by profit (decreasing)
2. Create time slots (1 to max deadline)
3. For each job (highest profit first):
   - Find latest available slot before deadline
   - Assign job to that slot
4. Sum profits of scheduled jobs

Why greedy works:
Doing highest profit jobs first, as late as possible!
```

## Greedy vs Dynamic Programming

**Use Greedy when:**
- Local optimal → Global optimal
- No need to reconsider past choices
- Faster and simpler

**Use DP when:**
- Need to try all possibilities
- Past choices affect future options
- Greedy doesn't give correct answer

**Example:**
- Fractional Knapsack: Greedy works ✓
- 0/1 Knapsack: Greedy fails, use DP ✗

## Tips for Solving

1. Think: "What's the best choice now?"
2. Try to prove/disprove greedy works
3. Sort the data appropriately
4. Test with small examples
5. Watch for counterexamples where greedy fails

## Time Complexity Tips
- Usually O(n log n) due to sorting
- Iteration after sorting: O(n)
- Much faster than DP or backtracking
- Best when applicable!
