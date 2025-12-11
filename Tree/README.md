# Tree

## What is a Tree?
A tree is a hierarchical data structure with nodes connected by edges. It has a root node at top, and each node can have children nodes. Think of it like a family tree or organization chart!

## When to Use Trees?
- Representing hierarchical data (file systems, org charts)
- Fast searching (Binary Search Tree)
- Expression evaluation
- Decision making processes

## Common Types
- **Binary Tree**: Each node has at most 2 children (left, right)
- **Binary Search Tree (BST)**: Left child < Parent < Right child
- **Balanced Tree**: Height difference between subtrees is minimal

## Common Problems You Can Solve

1. **Traversals** - Visit all nodes in specific order (Inorder, Preorder, Postorder)
2. **Searching** - Find a value in BST
3. **Height/Depth** - Calculate tree height or node depth
4. **LCA (Lowest Common Ancestor)** - Find common parent of two nodes
5. **Views** - Top view, bottom view, left view, right view
6. **Path problems** - Root to leaf paths, path sum
7. **Construction** - Build tree from traversals

## How to Develop Solutions

### Step 1: Understand Tree Structure
```
Node has:
- data (the value)
- left (pointer to left child)
- right (pointer to right child)
- root points to top node
```

### Step 2: Common Techniques

**Recursion** - Most natural for trees
```
Base case: if node is null, return
Recursive case:
  - Process current node
  - Recurse on left subtree
  - Recurse on right subtree
```

**Traversal Orders:**
- **Inorder (Left-Root-Right)**: Gives sorted order in BST
- **Preorder (Root-Left-Right)**: Good for copying tree
- **Postorder (Left-Right-Root)**: Good for deleting tree
- **Level Order**: Use queue, visit level by level

### Step 3: BST Properties
- All left subtree values < node value
- All right subtree values > node value
- Searching: O(log n) in balanced BST, O(n) worst case

### Example Logic
**Problem**: Find height of tree
```
Approach: Recursion
1. If node is null, height = 0
2. Get height of left subtree (recursive)
3. Get height of right subtree (recursive)
4. Height = 1 + max(left height, right height)
```

**Problem**: Search in BST
```
Approach: Binary Search
1. Start at root
2. If target == current node, found!
3. If target < current, go left
4. If target > current, go right
5. Repeat until found or reach null
```

**Problem**: Level order traversal
```
Approach: BFS with Queue
1. Add root to queue
2. While queue not empty:
   - Remove front node
   - Process it
   - Add left child to queue
   - Add right child to queue
```

## Time Complexity Tips
- Search in balanced BST: O(log n)
- Search in unbalanced BST: O(n) worst case
- Insert/Delete in BST: O(log n) average
- Traversals: O(n) - visit all nodes
