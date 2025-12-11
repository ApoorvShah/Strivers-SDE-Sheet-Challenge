# Graph

## What is a Graph?
A graph is a collection of nodes (vertices) connected by edges. Think of it like a map of cities (nodes) connected by roads (edges), or social networks where people (nodes) are connected by friendships (edges).

## When to Use Graphs?
- Network problems (social networks, computer networks)
- Path finding (GPS, maze solving)
- Dependencies (task scheduling, course prerequisites)
- Connectivity (finding groups, islands)

## Common Types
- **Directed Graph**: Edges have direction (A → B)
- **Undirected Graph**: Edges go both ways (A — B)
- **Weighted Graph**: Edges have costs/weights
- **Unweighted Graph**: All edges are equal

## Common Problems You Can Solve

1. **Traversal** - Visit all nodes (BFS, DFS)
2. **Shortest path** - Find shortest route between nodes (Dijkstra, Bellman-Ford)
3. **Cycle detection** - Check if graph has loops
4. **Connectivity** - Find connected components, islands
5. **Minimum Spanning Tree** - Connect all nodes with minimum cost (Prim's, Kruskal's)
6. **Topological sort** - Order tasks respecting dependencies
7. **Bipartite check** - Can nodes be divided into two groups?

## How to Develop Solutions

### Step 1: Represent the Graph
**Adjacency List** (Most common)
```
graph[node] = [list of neighbors]
Example: graph[1] = [2, 3]
```

**Adjacency Matrix**
```
matrix[i][j] = 1 if edge exists, 0 otherwise
```

### Step 2: Choose Traversal Method

**BFS (Breadth-First Search)** - Use Queue
- Explores level by level
- Good for shortest path in unweighted graphs
```
1. Start from source, add to queue
2. Mark as visited
3. While queue not empty:
   - Remove front node
   - Visit all unvisited neighbors
   - Add them to queue
```

**DFS (Depth-First Search)** - Use Stack/Recursion
- Explores as deep as possible first
- Good for cycle detection, path finding
```
1. Start from source
2. Mark as visited
3. For each unvisited neighbor:
   - Recursively call DFS
```

### Step 3: Common Algorithms

**Dijkstra's Algorithm** (Shortest path with positive weights)
- Use priority queue (min-heap)
- Greedily pick closest unvisited node

**Bellman-Ford** (Shortest path with negative weights)
- Relax all edges V-1 times
- Can detect negative cycles

**Kruskal's/Prim's** (Minimum Spanning Tree)
- Connect all nodes with minimum total edge weight

**Topological Sort** (Order tasks)
- Only for Directed Acyclic Graphs (DAG)
- Use DFS or BFS (Kahn's algorithm)

### Example Logic
**Problem**: Detect cycle in undirected graph
```
Approach: DFS
1. For each node, run DFS
2. During DFS, track parent
3. If we visit a node that's already visited
   AND it's not the parent → cycle found!
```

**Problem**: Find shortest path (unweighted)
```
Approach: BFS
1. Start BFS from source
2. Keep distance array
3. For each neighbor:
   - distance[neighbor] = distance[current] + 1
4. Return distance[destination]
```

## Time Complexity Tips
- BFS/DFS: O(V + E) where V=vertices, E=edges
- Dijkstra: O((V+E) log V) with priority queue
- Bellman-Ford: O(V × E)
- Kruskal's: O(E log E)
