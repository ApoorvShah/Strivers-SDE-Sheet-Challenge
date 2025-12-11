# Math & Number Theory

## What are Math Problems?
Math problems in programming involve using mathematical concepts, formulas, and properties to solve computational challenges. Think of it like using math shortcuts to calculate things quickly!

## When to Use Math Approaches?
- Problem has underlying mathematical pattern
- Formula exists to solve directly
- Need to optimize from O(n) to O(1)
- Working with numbers, digits, primes, GCD, etc.

## Common Math Concepts

### 1. Number Properties
- **Even/Odd**: n % 2
- **Divisibility**: n % k == 0
- **Prime numbers**: Only divisible by 1 and itself
- **Perfect squares**: n = k × k

### 2. Key Formulas
- **Sum of first n numbers**: n × (n+1) / 2
- **Sum of squares**: n × (n+1) × (2n+1) / 6
- **Power of 2**: Use bit manipulation (1 << n)
- **GCD**: Greatest Common Divisor (Euclidean algorithm)
- **LCM**: Least Common Multiple = (a × b) / GCD(a,b)

### 3. Common Techniques
- **Modular arithmetic**: (a + b) % m = ((a % m) + (b % m)) % m
- **Fast exponentiation**: Calculate a^n in O(log n)
- **Digit manipulation**: Extract digits using %10 and /10
- **Bit manipulation**: Use AND, OR, XOR for efficiency

## Common Problems You Can Solve

1. **Power calculation** - Calculate x^n efficiently
2. **GCD/LCM** - Find greatest common divisor
3. **Prime numbers** - Check if prime, find all primes
4. **Factorial** - Calculate n!
5. **Digit problems** - Reverse number, sum digits, palindrome
6. **Combinations/Permutations** - nCr, nPr calculations
7. **Pattern problems** - Print patterns, sequences

## How to Develop Solutions

### Step 1: Look for Mathematical Pattern
- Can it be solved with a formula?
- Is there repetition or cycle?
- Can you use properties (even/odd, divisibility)?

### Step 2: Common Math Algorithms

**GCD (Euclidean Algorithm)**
```
gcd(a, b):
  if b == 0: return a
  return gcd(b, a % b)

Example: gcd(48, 18)
  gcd(48, 18) → gcd(18, 12) → gcd(12, 6) → gcd(6, 0) = 6
```

**Fast Power (Binary Exponentiation)**
```
power(x, n):
  if n == 0: return 1
  if n is even:
    half = power(x, n/2)
    return half × half
  else:
    return x × power(x, n-1)

Time: O(log n) instead of O(n)
```

**Check if Prime**
```
isPrime(n):
  if n <= 1: return false
  if n <= 3: return true
  if n % 2 == 0 or n % 3 == 0: return false

  Check divisibility from 5 to √n
  for i from 5 to √n, step by 6:
    if n % i == 0 or n % (i+2) == 0:
      return false
  return true

Why up to √n? If n = a × b and a ≤ b,
then a ≤ √n
```

**Sieve of Eratosthenes** (All primes up to n)
```
sieve(n):
  Create boolean array[n+1], set all to true
  array[0] = array[1] = false

  for i from 2 to √n:
    if array[i] is true:
      Mark all multiples of i as false
      (i×i, i×i+i, i×i+2i, ...)

  All true values are primes
Time: O(n log log n)
```

### Example Logic

**Problem**: Calculate x^n efficiently
```
Approach: Binary Exponentiation
If n is even: x^n = (x^(n/2))²
If n is odd: x^n = x × x^(n-1)

Example: 2^10
2^10 = (2^5)²
2^5 = 2 × (2^2)²
2^2 = (2^1)²
2^1 = 2 × 2^0 = 2

Only 4 steps instead of 10!
```

**Problem**: Count trailing zeros in factorial
```
Approach: Count factors of 5
Trailing zeros come from 10 = 2 × 5
In n!, factors of 2 are more than 5
So count factors of 5

countZeros(n):
  count = 0
  power = 5
  while n >= power:
    count += n / power
    power *= 5
  return count

Example: 25! has 25/5 + 25/25 = 5 + 1 = 6 zeros
```

**Problem**: Print pattern (Pascal's Triangle)
```
Approach: Use combination formula
Each value is nCr = n! / (r! × (n-r)!)

       1
      1 1
     1 2 1
    1 3 3 1
   1 4 6 4 1

OR use property: value[i][j] = value[i-1][j-1] + value[i-1][j]
```

## Bit Manipulation Tricks

```
Check if power of 2: n & (n-1) == 0
Count set bits: Use Brian Kernighan's algorithm
Get ith bit: (n >> i) & 1
Set ith bit: n | (1 << i)
Clear ith bit: n & ~(1 << i)
Toggle ith bit: n ^ (1 << i)
```

## Tips for Solving

1. **Look for formula** before coding
2. **Draw examples** for pattern recognition
3. **Check edge cases**: 0, 1, negative numbers
4. **Use modulo** to prevent overflow
5. **Think optimization**: Can O(n) become O(log n)?

## Time Complexity Tips
- Direct formula: O(1)
- Fast power: O(log n)
- GCD: O(log min(a,b))
- Prime check: O(√n)
- Sieve of Eratosthenes: O(n log log n)
- Factorization: O(√n)
