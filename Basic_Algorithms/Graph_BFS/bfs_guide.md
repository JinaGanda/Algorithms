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

# **BFS Implementation Patterns (C-style Adjacency Matrix & Arrays)**

## **1. Standard BFS Using a Queue**
This implementation uses a queue and an adjacency matrix for a graph.

```cpp
#include <iostream>
#include <queue>
#include <vector>
using namespace std;

#define MAX_NODES 100  // Maximum number of nodes

int graph[MAX_NODES][MAX_NODES];  // Adjacency matrix
bool visited[MAX_NODES];          // Visited array

void bfs(int start, int n) {
    queue<int> q;
    q.push(start);
    visited[start] = true;

    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";  // Process the node

        for (int i = 0; i < n; i++) {
            if (graph[node][i] == 1 && !visited[i]) {  // Check adjacency
                visited[i] = true;
                q.push(i);
            }
        }
    }
}

int main() {
    int n = 5;  // Example graph with 5 nodes
    graph[0][1] = graph[1][0] = 1;
    graph[1][2] = graph[2][1] = 1;
    graph[2][3] = graph[3][2] = 1;
    graph[3][4] = graph[4][3] = 1;
    
    cout << "BFS Traversal: ";
    bfs(0, n);  // Start BFS from node 0
    return 0;
}
```

---

## **2. BFS for 2D Grids (dx, dy Method)**
This uses `dx, dy` arrays to navigate in 4 directions.

```cpp
#include <iostream>
#include <queue>
using namespace std;

#define ROWS 5
#define COLS 5

int grid[ROWS][COLS] = { // Example grid
    {1, 1, 0, 0, 1},
    {0, 1, 1, 0, 1},
    {1, 0, 1, 1, 0},
    {0, 1, 0, 1, 1},
    {1, 1, 1, 0, 1}
};

bool visited[ROWS][COLS];  // Visited array

// Directions: right, down, left, up
int dx[] = {0, 1, 0, -1};
int dy[] = {1, 0, -1, 0};

void bfs_grid(int start_x, int start_y) {
    queue<pair<int, int>> q;
    q.push({start_x, start_y});
    visited[start_x][start_y] = true;

    while (!q.empty()) {
        auto [x, y] = q.front();
        q.pop();
        cout << "(" << x << "," << y << ") ";

        for (int i = 0; i < 4; i++) { // 4 possible directions
            int new_x = x + dx[i];
            int new_y = y + dy[i];

            if (new_x >= 0 && new_x < ROWS && new_y >= 0 && new_y < COLS &&
                !visited[new_x][new_y] && grid[new_x][new_y] == 1) {
                visited[new_x][new_y] = true;
                q.push({new_x, new_y});
            }
        }
    }
}

int main() {
    cout << "BFS Grid Traversal: ";
    bfs_grid(0, 0); // Start BFS from (0,0)
    return 0;
}
```

---

## **3. Multi-Source BFS**
This version starts from multiple points at the same time.

```cpp
#include <iostream>
#include <queue>
using namespace std;

#define ROWS 5
#define COLS 5

int grid[ROWS][COLS] = { 
    {1, 1, 0, 0, 1},
    {0, 1, 1, 0, 1},
    {1, 0, 1, 1, 0},
    {0, 1, 0, 1, 1},
    {1, 1, 1, 0, 1}
};

bool visited[ROWS][COLS];

// Directions: right, down, left, up
int dx[] = {0, 1, 0, -1};
int dy[] = {1, 0, -1, 0};

void multi_source_bfs(queue<pair<int, int>> sources) {
    while (!sources.empty()) {
        auto [x, y] = sources.front();
        sources.pop();
        cout << "(" << x << "," << y << ") ";

        for (int i = 0; i < 4; i++) {
            int new_x = x + dx[i];
            int new_y = y + dy[i];

            if (new_x >= 0 && new_x < ROWS && new_y >= 0 && new_y < COLS &&
                !visited[new_x][new_y] && grid[new_x][new_y] == 1) {
                visited[new_x][new_y] = true;
                sources.push({new_x, new_y});
            }
        }
    }
}

int main() {
    queue<pair<int, int>> sources;
    sources.push({0, 0});
    sources.push({2, 2});
    visited[0][0] = visited[2][2] = true;

    cout << "Multi-Source BFS Traversal: ";
    multi_source_bfs(sources);
    return 0;
}
```

---

## **Key BFS Concepts:**
- ✅ Uses a queue (FIFO)
- ✅ Explores all neighbors before going deeper
- ✅ Finds shortest paths in unweighted graphs
- ✅ Used in grid traversal (dx, dy method)
- ✅ Handles multi-source problems efficiently

---

## **Where is BFS Used?**
- **Pathfinding Algorithms**: Shortest path in unweighted graphs (Dijkstra’s for weighted).
- **Grid-based Games**: Movement in chess (Knight’s shortest path).
- **AI & Robotics**: Path planning for robots.
- **Computer Networks**: Broadcasting in networks.
- **Image Processing**: Flood fill (used in Paint).
- **Social Networks**: Finding shortest connections.
- **Maze Solving**: Shortest escape path.

---

## **Benefits of BFS**
✅ **Guaranteed shortest path in unweighted graphs**  
✅ **Efficient for connected components counting**  
✅ **Simple implementation using queue**  
✅ **Works well for multi-source problems**  

---

## Conclusion

BFS is a versatile algorithm used in a variety of competitive programming problems. Understanding its different implementations and applications will help solve many graph-related challenges efficiently.
