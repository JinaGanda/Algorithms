 
# **Breadth-First Search (BFS) Algorithm**

## **Introduction**
Breadth-First Search (BFS) is a graph traversal algorithm used to explore nodes layer by layer. It visits all the nodes at the current depth level before moving on to nodes at the next depth level.

## **How BFS Works**
1. Start from a given node (source).
2. Use a **queue** (FIFO) to maintain the order of visiting nodes.
3. Mark visited nodes to avoid redundant processing.
4. Dequeue a node from the queue, process it, and enqueue all its unvisited neighbors.
5. Repeat until the queue is empty.

---

# **BFS Algorithm (Graph Representation using Adjacency Matrix - C Style)**

## **Adjacency Matrix Representation**
- We use a **2D array** where `adj[i][j] = 1` indicates an edge between `i` and `j`.
- If there’s no edge, `adj[i][j] = 0`.

## **C++ Code for BFS (Adjacency Matrix)**
```cpp
#include <iostream>
#include <queue>
using namespace std;

#define MAX_NODES 100  // Maximum number of nodes

int adj[MAX_NODES][MAX_NODES]; // Adjacency matrix
bool visited[MAX_NODES];       // Visited array

void BFS(int start, int nodes) {
    queue<int> q;
    q.push(start);
    visited[start] = true;

    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " "; // Process the node

        for (int i = 0; i < nodes; i++) {
            if (adj[node][i] == 1 && !visited[i]) { // Check unvisited neighbors
                q.push(i);
                visited[i] = true;
            }
        }
    }
}

int main() {
    int nodes, edges, u, v;
    cout << "Enter number of nodes and edges: ";
    cin >> nodes >> edges;

    // Initialize adjacency matrix
    for (int i = 0; i < nodes; i++)
        for (int j = 0; j < nodes; j++)
            adj[i][j] = 0;

    cout << "Enter edges (u v format, 0-based index): 
";
    for (int i = 0; i < edges; i++) {
        cin >> u >> v;
        adj[u][v] = 1; // Mark the edge
        adj[v][u] = 1; // Since it's an undirected graph
    }

    int start;
    cout << "Enter starting node: ";
    cin >> start;
    
    cout << "BFS Traversal: ";
    BFS(start, nodes);

    return 0;
}
```

---

# **BFS for a 2D Grid (dx/dy Method for Neighbor Traversal)**

## **dx/dy or d[4][2] Approach for 2D Grid**
Instead of checking each neighbor manually, we use arrays to represent movement directions.

### **dx/dy Arrays**  
- `dx = {0, 0, -1, 1}` → Moves: Left, Right, Up, Down  
- `dy = {-1, 1, 0, 0}` → Corresponding y-coordinate changes  

### **d[4][2] Array Approach**  
```cpp
int d[4][2] = { {0,1}, {0,-1}, {1,0}, {-1,0} };
```
- First column represents x-movement, second column represents y-movement.

## **C++ Code for BFS on a 2D Grid**
```cpp
#include <iostream>
#include <queue>
using namespace std;

#define N 5  // Grid size

struct Point {
    int x, y;
};

int grid[N][N] = {
    {1, 1, 0, 1, 0},
    {0, 1, 1, 1, 1},
    {1, 0, 1, 0, 1},
    {1, 1, 1, 1, 0},
    {0, 1, 0, 1, 1}
};

bool visited[N][N] = {false};

// Directions for movement (left, right, up, down)
int dx[4] = {0, 0, -1, 1};
int dy[4] = {-1, 1, 0, 0};

void BFS(int startX, int startY) {
    queue<Point> q;
    q.push({startX, startY});
    visited[startX][startY] = true;

    while (!q.empty()) {
        Point p = q.front();
        q.pop();
        cout << "(" << p.x << "," << p.y << ") ";

        for (int i = 0; i < 4; i++) {
            int nx = p.x + dx[i];
            int ny = p.y + dy[i];

            if (nx >= 0 && ny >= 0 && nx < N && ny < N && grid[nx][ny] == 1 && !visited[nx][ny]) {
                q.push({nx, ny});
                visited[nx][ny] = true;
            }
        }
    }
}

int main() {
    cout << "BFS Traversal starting from (0,0): ";
    BFS(0, 0);
    return 0;
}
```

---

# **Benefits of BFS**
1. **Finds the shortest path in an unweighted graph.**
2. **Systematic exploration of nodes** (layer-by-layer).
3. **Useful in real-time applications** (e.g., shortest distance in GPS).
4. **Multi-source BFS is efficient** for problems with multiple starting points.
5. **Cycle detection and connectivity checking** in graphs.

---

# **Where is BFS Used?**
### **Graph Problems**
- Shortest path in an **unweighted** graph.
- **Connected components** in a graph.
- **Cycle detection** in undirected graphs.

### **Grid Problems**
- **Maze solving** (shortest path).
- **Island counting** (connected components in a matrix).
- **Flood fill algorithm** (e.g., paint bucket tool in graphics).
- **Fire spreading simulation** (multi-source BFS).

### **Real-World Applications**
1. **Network Routing** – Finding the shortest path in a computer network.
2. **AI & Game Development** – Pathfinding in games.
3. **Web Crawlers** – Crawling websites systematically.
4. **Social Networks** – Finding degrees of separation between users.
5. **Robotics** – Path planning for robots.

---

# **Example Graph & Execution of BFS**
**Graph Representation:**
```
    0 --- 1 --- 2
    |     |     |
    3 --- 4 --- 5
```
Adjacency Matrix:
```
   0  1  3
   1  0  2  4
   2  1  5
   3  0  4
   4  1  3  5
   5  2  4
```
### **Execution Order for BFS starting from node `0`**
- Start at `0`, visit `1` and `3`.
- Visit `2` (neighbor of `1`), visit `4` (neighbor of `1` and `3`).
- Visit `5` (neighbor of `2` and `4`).
- **Final BFS Order: `0 → 1 → 3 → 2 → 4 → 5`**

---

# **Conclusion**
BFS is a **powerful** algorithm used for shortest paths, connectivity checks, and various search problems in graphs and grids. Mastering BFS and its variations (multi-source, bidirectional, etc.) is crucial for competitive programming and real-world applications.

# **See Next**
- [BFS Question Comprehensive Guide] (bfs_guide.md)
- [BFS Problem Patterns] (bfs_problem_patterns.md)
- [BFS Coding Approaches] (bfs_problem_solutions.md)
