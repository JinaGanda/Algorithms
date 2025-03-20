# Breadth-First Search (BFS) Problem Patterns and Examples

## 1. Shortest Path in Unweighted Graphs

BFS efficiently finds the shortest path between nodes in unweighted graphs. This is crucial in scenarios like:

- **Maze Navigation**: Finding the shortest route from a start to an end point in a maze.
- **Word Transformation**: Determining the minimum number of single-letter changes to transform one word into another, with each intermediate word being valid.

## 2. Connected Components and Clustering

Identifying connected components or clusters within a graph or grid is a common application:

- **Island Counting**: Counting distinct islands in a binary grid, where islands are groups of connected '1's.
- **Cluster Detection**: Identifying clusters of connected nodes or regions, such as in image segmentation.

## 3. Cycle Detection

BFS can detect cycles in graphs:

- **Cycle Detection**: Determining if a cycle exists in an undirected graph.
- **Smallest Cycle**: Finding the shortest cycle in a graph.

## 4. Multi-Source BFS

When multiple starting points are involved, multi-source BFS is applicable:

- **Virus Spread Simulation**: Modeling how a virus spreads from multiple initial infection points in a network.
- **Fire Spread**: Simulating fire spreading from multiple sources in a forest grid.

## 5. Grid-Based Problems

BFS is particularly useful in grid-based scenarios:

- **Flood Fill Algorithm**: Filling connected regions in image processing.
- **Boundary Painting**: Changing the color of the boundary of a region in a grid.

## 6. Game Simulations

Simulating moves in games often utilizes BFS:

- **Snake and Ladder**: Finding the minimum dice throws required to reach the last cell in a board game.
- **Knight’s Shortest Path**: Calculating the minimum moves for a knight to reach a target position on a chessboard.

## 7. Advanced Variations

Certain problems require modified BFS approaches:

- **0-1 BFS**: Handling graphs with edges weighted 0 or 1 to find the shortest path efficiently.
- **Teleporting Maze**: Finding paths in mazes where certain cells act as teleporters.

## Common BFS Problem Patterns

Recognizing these patterns can aid in identifying when to apply BFS:

- **Level Order Traversal**: Processing nodes level by level, useful in tree structures.
- **Shortest Path in Unweighted Graphs**: Finding the minimum number of edges between nodes.
- **Connected Component Identification**: Finding all distinct connected subgraphs.
- **Cycle Detection**: Identifying cycles within graphs.
- **Multi-Source Shortest Path**: Calculating shortest paths from multiple sources simultaneously.

## BFS Problems from Competitive Programming Platforms

Here are some BFS problems from various competitive programming sites:

1. **Shortest Path in an Unweighted Graph**: Find the shortest path from a source node to all other nodes.
2. **Connected Components in a Graph**: Count the number of connected components in an undirected graph.
3. **Bipartite Graph Check**: Use BFS to determine if a graph is bipartite.
4. **Cycle Detection in an Undirected Graph**: Detect cycles using BFS.
5. **Topological Sorting (Kahn’s Algorithm)**: Perform topological sorting using BFS in a Directed Acyclic Graph (DAG).
6. **Shortest Path in a Grid (4 or 8 Directions)**: Find the shortest path from a start cell to a target cell in a `N × M` grid with obstacles.
7. **Flood Fill Algorithm**: Implement BFS to color a region in an image or grid.
8. **Number of Islands**: Count the number of distinct islands in a binary grid.
9. **Rotten Oranges (Multi-Source BFS)**: Find the minimum time for all fresh oranges to rot.
10. **Walls and Gates**: Fill a grid with the shortest distance from each gate using BFS.
11. **Knight’s Shortest Path (Chessboard BFS)**: Find the minimum moves for a knight to reach a target position.
12. **Bishop’s Minimum Moves**: Find the shortest path for a bishop in a chessboard.
13. **Cycle Detection in a Grid**: Detect if a cycle exists in a grid representation of a graph.
14. **Fire Spread Simulation**: Given a grid where fire spreads each second, find the shortest escape route.
15. **Virus Spread**: A virus spreads in a grid each second; determine when it will infect all cells.
16. **Escape from a Grid with Moving Obstacles**: Find a way to escape while avoiding moving walls.
17. **Laughing Bomb (Chain Reaction with BFS)**: When one bomb explodes, it triggers adjacent bombs; find the number of bombs that explode.
18. **Find the Shortest Cycle in a Graph**: Find the length of the smallest cycle using BFS.
19. **Count the Number of Cycles in a Graph**: Find all distinct cycles using BFS.
