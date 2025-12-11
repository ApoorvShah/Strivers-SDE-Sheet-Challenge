# String

## What is a String?
A string is a sequence of characters (letters, numbers, symbols). Think of it like a word or sentence stored in your program.

## When to Use Strings?
- Working with text data
- Parsing and pattern matching
- Manipulating words, sentences, or documents

## Common Problems You Can Solve

1. **Pattern matching** - Find if a pattern exists in text (KMP, Rabin-Karp)
2. **Palindromes** - Check if text reads same forwards and backwards
3. **Anagrams** - Check if two strings have same characters
4. **Substrings** - Find longest/shortest substring with certain properties
5. **String manipulation** - Reverse, rotate, compare strings

## How to Develop Solutions

### Step 1: Understand String Properties
- Strings are **immutable** in many languages (can't change, must create new)
- Each character has an index (position)
- Can be treated like an array of characters

### Step 2: Common Techniques
- **Two Pointers**: One from start, one from end (palindrome check)
- **HashMap/Frequency Count**: Count character occurrences
- **Sliding Window**: Find substrings with specific properties
- **String Building**: Use StringBuilder for efficiency

### Step 3: Pattern Matching Algorithms
- **KMP (Knuth-Morris-Pratt)**: Smart pattern searching
- **Rabin-Karp**: Uses hashing to find patterns
- **Z-Algorithm**: Finds pattern occurrences efficiently

### Example Logic
**Problem**: Check if string is palindrome
```
Approach: Two Pointers
1. Set left pointer at start (0)
2. Set right pointer at end (length-1)
3. While left < right:
   - If characters don't match, return false
   - Move left forward, right backward
4. Return true (all matched!)
```

## Time Complexity Tips
- Accessing character: O(1)
- Building new string character by character: O(n²) - avoid!
- Using StringBuilder: O(n) - much better!
- Pattern matching: O(n) with KMP, O(n²) brute force
