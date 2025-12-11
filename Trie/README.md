# Trie (Prefix Tree)

## What is a Trie?
A Trie is a tree-like data structure used to store strings. Each path from root to leaf represents a word, and each node represents a character. Think of it like an autocomplete system in your phone - it knows all words starting with what you've typed!

## When to Use Trie?
- Autocomplete features (search suggestions)
- Spell checkers
- Finding words with common prefixes
- Dictionary implementations
- IP routing tables

## Common Problems You Can Solve

1. **Word search** - Check if word exists in dictionary
2. **Prefix search** - Find all words starting with prefix
3. **Autocomplete** - Suggest words based on prefix
4. **Longest common prefix** - Find common prefix of all words
5. **Count distinct substrings** - Count unique substrings
6. **Max XOR** - Find maximum XOR of numbers (binary trie)

## How to Develop Solutions

### Step 1: Understand Trie Structure
```
Node has:
- children[] - Array/Map of child nodes (26 for a-z)
- isEndOfWord - Boolean flag
```

**Example**: Storing "cat", "car", "dog"
```
       root
      /    \
     c      d
     |      |
     a      o
    / \     |
   t   r    g
   *   *    *
(* = end of word)
```

### Step 2: Basic Operations

**Insert a word**
```
1. Start at root
2. For each character in word:
   - If child doesn't exist, create it
   - Move to child node
3. Mark last node as end of word
```

**Search for word**
```
1. Start at root
2. For each character:
   - If child doesn't exist, return false
   - Move to child node
3. Return true if last node is marked as end
```

**Search for prefix**
```
Same as search, but don't check isEndOfWord
Just check if path exists
```

### Step 3: Common Patterns

**Autocomplete/All words with prefix**
```
1. Navigate to end of prefix
2. From there, do DFS to collect all words
3. Each path to isEndOfWord is a valid word
```

**Count words with prefix**
```
Add counter at each node
Increment when inserting word
```

### Example Logic
**Problem**: Implement autocomplete
```
Approach: Trie + DFS
1. Insert all dictionary words into Trie
2. For given prefix:
   - Navigate to end of prefix in Trie
   - If prefix doesn't exist, return []
   - From that node, run DFS
   - Collect all paths to isEndOfWord nodes
   - These are all words with that prefix
```

**Problem**: Longest word with all prefixes
```
Approach: Trie
1. Insert all words
2. DFS from root
3. Only go down paths where isEndOfWord = true
4. Track longest word found this way
5. This ensures all prefixes exist!
```

**Problem**: Maximum XOR (binary trie)
```
Approach: Binary Trie (0s and 1s)
1. Insert all numbers in binary form
2. For query number:
   - Try to go opposite bit at each step
   - This maximizes XOR
   - If opposite doesn't exist, go same bit
```

## Time Complexity Tips
- Insert word of length L: O(L)
- Search word of length L: O(L)
- Space for N words of average length L: O(N × L)
- Better than HashMap for prefix operations
- Each node can have up to 26 children (for lowercase a-z)
