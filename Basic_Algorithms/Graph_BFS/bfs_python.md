# Breadth-First Search (BFS) Algorithm in Python

## Introduction to BFS
Breadth-First Search (BFS) is a graph traversal algorithm that explores all the nodes at the present depth level before moving on to nodes at the next depth level. It uses a queue to keep track of nodes to be visited.

### Applications of BFS:
- Shortest path in an unweighted graph
- Finding connected components in a graph
- Solving puzzles like sliding puzzles, word ladder, etc.
- Network broadcasting
- AI pathfinding (e.g., in games, robotics)

---

## BFS Implementation in Python

### 1. BFS Using an Adjacency Matrix
An adjacency matrix represents a graph using a 2D array, where `graph[i][j] = 1` means there's an edge between node `i` and node `j`.

```python
from collections import deque

def bfs_adj_matrix(graph, start):
    n = len(graph)
    visited = [False] * n
    queue = deque([start])
    visited[start] = True
    
    while queue:
        node = queue.popleft()
        print(node, end=" ")  # Process the node
        
        for neighbor in range(n):
            if graph[node][neighbor] == 1 and not visited[neighbor]:
                visited[neighbor] = True
                queue.append(neighbor)

# Example usage
graph_matrix = [
    [0, 1, 1, 0],
    [1, 0, 1, 1],
    [1, 1, 0, 1],
    [0, 1, 1, 0]
]
bfs_adj_matrix(graph_matrix, 0)
```

---

### 2. BFS Using an Adjacency List
An adjacency list stores graph edges as a dictionary, where each node has a list of its neighbors.

```python
from collections import deque

def bfs_adj_list(graph, start):
    visited = set([start])
    queue = deque([start])
    
    while queue:
        node = queue.popleft()
        print(node, end=" ")  # Process the node
        
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)

# Example usage
graph_list = {
    0: [1, 2],
    1: [0, 2, 3],
    2: [0, 1, 3],
    3: [1, 2]
}
bfs_adj_list(graph_list, 0)
```

---

### 3. BFS for 2D Grid (dx, dy method)
When working with a 2D grid, we can use `dx` and `dy` arrays to navigate in 4 directions.

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
        print(f"({x}, {y})", end=" ")  # Process the cell
        
        for i in range(4):  # 4 possible directions
            new_x, new_y = x + dx[i], y + dy[i]
            if 0 <= new_x < rows and 0 <= new_y < cols and (new_x, new_y) not in visited:
                visited.add((new_x, new_y))
                queue.append((new_x, new_y))

# Example grid usage
grid_example = [
    [0, 1, 0],
    [0, 0, 1],
    [1, 0, 0]
]
bfs_grid(grid_example, 0, 0)
```

---

### 4. Multi-Source BFS (Used for Fire Spread, Virus Spread, Rotten Oranges, etc.)
Multi-source BFS starts from multiple points at once and expands outward.

```python
def multi_source_bfs(grid, sources):
    rows, cols = len(grid), len(grid[0])
    queue = deque(sources)
    visited = set(sources)
    
    while queue:
        x, y = queue.popleft()
        print(f"({x}, {y})", end=" ")  # Process the cell
        
        for i in range(4):
            new_x, new_y = x + dx[i], y + dy[i]
            if 0 <= new_x < rows and 0 <= new_y < cols and (new_x, new_y) not in visited:
                visited.add((new_x, new_y))
                queue.append((new_x, new_y))

# Example usage
sources_example = [(0, 1), (2, 2)]
bfs_grid(grid_example, 0, 0)
```

---

## Benefits of BFS
- **Guarantees shortest path in an unweighted graph.**
- **Can handle disconnected components in a graph.**
- **Useful in AI, shortest path problems, and connectivity checks.**

---

## Where is BFS Used?
1. **Finding shortest paths in an unweighted graph** (e.g., road maps, social networks).
2. **AI & Pathfinding** (e.g., solving mazes, robotics).
3. **Connected Components detection** (e.g., islands in a matrix).
4. **Cycle Detection** (e.g., finding cycles in undirected graphs).
5. **Network Broadcasting** (e.g., spreading messages efficiently).
6. **Puzzle Solving** (e.g., word ladder, Sudoku solving).

---

## Conclusion
BFS is a fundamental algorithm with numerous applications in graph traversal and search problems. Understanding BFS in adjacency matrix, adjacency list, and 2D grid format is essential for competitive programming and real-world problem solving.
