# Comprehensive Guide to Breadth-First Search (BFS) in Competitive Programming

## Overview

Breadth-First Search (BFS) is a fundamental graph traversal algorithm that explores vertices in the order of their distance from the source vertex, making it particularly useful for finding the shortest path in unweighted graphs. This guide provides an in-depth look at BFS applications, common problem patterns, coding techniques, and references to competitive programming problems.

## BFS Problem Patterns and Solutions

### 1. Shortest Path in Unweighted Graphs

**Problem:** Find the shortest path from a source vertex to all other vertices in an unweighted graph.

**Solution:** Use BFS starting from the source vertex. As BFS explores all vertices at the present depth level before moving on to vertices at the next depth level, it naturally finds the shortest path in terms of the number of edges.

**Competitive Programming Example:** ["Shortest Path in an Unweighted Graph" on LeetCode](https://leetcode.com/problems/shortest-path-in-unweighted-graph/).

### 2. Connected Components in a Graph

**Problem:** Determine the number of connected components in an undirected graph.

**Solution:** Iterate through all vertices, and for each unvisited vertex, perform BFS to mark all reachable vertices. Each BFS traversal represents a distinct connected component.

**Competitive Programming Example:** ["Number of Connected Components in an Undirected Graph" on LeetCode](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/).

### 3. Bipartite Graph Check

**Problem:** Check if a given graph is bipartite.

**Solution:** Use BFS to attempt to color the graph using two colors. If you can color the graph such that no two adjacent vertices share the same color, the graph is bipartite.

**Competitive Programming Example:** ["Is Graph Bipartite?" on LeetCode](https://leetcode.com/problems/is-graph-bipartite/).

### 4. Cycle Detection in Undirected Graphs

**Problem:** Detect if there is a cycle in an undirected graph.

**Solution:** Perform BFS, and for each visited vertex, track its parent. If you encounter an already visited vertex that is not the parent of the current vertex, a cycle exists.

**Competitive Programming Example:** ["Detect Cycle in an Undirected Graph" on GeeksforGeeks](https://www.geeksforgeeks.org/detect-cycle-undirected-graph/).

### 5. Topological Sorting (Kahn’s Algorithm)

**Problem:** Perform topological sorting on a Directed Acyclic Graph (DAG).

**Solution:** Use Kahn's Algorithm, which employs BFS to repeatedly remove nodes with zero in-degree and append them to the topological order.

**Competitive Programming Example:** ["Course Schedule II" on LeetCode](https://leetcode.com/problems/course-schedule-ii/).

### 6. Shortest Path in a Grid (4 or 8 Directions)

**Problem:** Find the shortest path from a start cell to a target cell in a 2D grid with obstacles, moving in 4 or 8 possible directions.

**Solution:** Apply BFS from the start cell, exploring all possible moves (up, down, left, right, and optionally diagonals) while checking for boundaries and obstacles.

**Competitive Programming Example:** ["Shortest Path in Binary Matrix" on LeetCode](https://leetcode.com/problems/shortest-path-in-binary-matrix/).

### 7. Flood Fill Algorithm

**Problem:** Given a 2D grid, change the color of a connected component.

**Solution:** Use BFS to traverse all connected cells with the same color and change them to the new color.

**Competitive Programming Example:** ["Flood Fill" on LeetCode](https://leetcode.com/problems/flood-fill/).

### 8. Number of Islands

**Problem:** Count the number of distinct islands in a binary grid.

**Solution:** Iterate through each cell, and upon encountering an unvisited land cell, perform BFS to mark all connected land cells. Each BFS corresponds to a distinct island.

**Competitive Programming Example:** ["Number of Islands" on LeetCode](https://leetcode.com/problems/number-of-islands/).

### 9. Rotten Oranges (Multi-Source BFS)

**Problem:** Given a grid of oranges where some are rotten and others fresh, determine the minimum time required for all oranges to rot.

**Solution:** Use multi-source BFS by enqueuing all initially rotten oranges and then perform BFS to simulate the rotting process.

**Competitive Programming Example:** ["Rotting Oranges" on LeetCode](https://leetcode.com/problems/rotting-oranges/).

### 10. Walls and Gates

**Problem:** Fill each empty room in a grid with the distance to its nearest gate.

**Solution:** Perform multi-source BFS from all gates simultaneously, updating distances as you traverse.

**Competitive Programming Example:** ["Walls and Gates" on LeetCode](https://leetcode.com/problems/walls-and-gates/).

## BFS Implementation Patterns

### BFS Using Queue (Standard BFS)

```python
from collections import deque

def bfs(graph, start):
    queue = deque([start])
    visited = set([start])
    
    while queue:
        node = queue.popleft()
        print(node)  # Process the node
        
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

### BFS for 2D Grids (dx, dy method)

```python
from collections import deque

# Directions: right, down, left, up
dx = [0, 1, 0, -1]
dy = [1, 0, -1, 0]

def bfs_grid(grid, start_x, start_y):
    rows, cols = len(grid), len(grid[0])
    queue = deque([(start_x, start_y)])
    visited = set([(start_x, start_y)])
    
    while queue:
        x, y = queue.popleft()
        
        for i in range(4):  # 4 possible directions
            new_x, new_y = x + dx[i], y + dy[i]
            if 0 <= new_x < rows and 0 <= new_y < cols and (new_x, new_y) not in visited:
                visited.add((new_x, new_y))
                queue.append((new_x, new_y))
```

### Multi-Source BFS

```python
def multi_source_bfs(grid, sources):
    rows, cols = len(grid), len(grid[0])
    queue = deque(sources)
    visited = set(sources)
    
    while queue:
        x, y = queue.popleft()
        
        for i in range(4):
            new_x, new_y = x + dx[i], y + dy[i]
            if 0 <= new_x < rows and 0 <= new_y < cols and (new_x, new_y) not in visited:
                visited.add((new_x, new_y))
                queue.append((new_x, new_y))
```

## Conclusion

BFS is a versatile algorithm used in a variety of competitive programming problems. Understanding its different implementations and applications will help solve many graph-related challenges efficiently.
