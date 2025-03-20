
# BFS Problems and Solutions

This document provides a structured breakdown of BFS problems, detailing problem descriptions and solution approaches.

---

## 1. Fire Spread

**Problem:**  
Fire spreads in a grid from an initial point(s). Can you reach the exit before fire catches you?  
Variation: Find the minimum time for the entire grid to be burned.  

**Solution:**  
- Use **multi-source BFS** to simulate fire spreading in the grid.
- Simultaneously perform BFS for the player's movement to see if escape is possible before fire reaches the exit.
- If fire reaches all possible paths before the player, return `-1` (no escape).

---

## 2. Grid Changing State (Game of Life Type)

**Problem:**  
A 4×4 or 5×5 grid where cells change based on neighboring states.  
Find the number of steps to reach a stable configuration.  

**Solution:**  
- Use **BFS or iterative simulation** to process the state changes at each step.
- Store the grid states in a queue and process each layer until no further changes occur.
- Use a **hash set** to detect cycles (if a state repeats, it’s stable).

---

## 3. Flood Spread and Damage Reduction

**Problem:**  
Water spreads every turn, and you can place up to `k` barriers to block it.  
Find the best strategy to minimize flooding.  

**Solution:**  
- Use **multi-source BFS** to simulate water spread.  
- Try different placements of `k` barriers and simulate flood containment.  
- Use a **priority queue** or **greedy search** to optimize barrier placement.  

---

## 4. Boundary or Grid Painting

**Problem:**  
Given a grid with different colored regions, paint the boundary of a given region with a new color.  

**Solution:**  
- Use **BFS or DFS** to find the boundary cells of the target region.  
- Change the color of only the boundary cells.  

---

## 5. Balls Dropped at the Same Time Over Grid

**Problem:**  
Balls are dropped simultaneously and roll downwards. Predict where each ball will land.  

**Solution:**  
- Simulate gravity using **BFS or DFS**.  
- Use a queue to track ball positions and update movement.  
- Handle obstacles and track the final position of each ball.  

---

## 6. Endoscope (Tunnels and Visibility)

**Problem:**  
A robot moves inside a grid of tunnels. Given the start position and movement constraints, find how many cells it can visit.  

**Solution:**  
- Use **BFS** to explore all reachable tunnel paths.  
- Apply movement constraints to restrict directions.  

---

## 7. Island Counting

**Problem:**  
Count the number of islands in a grid.  
Variation: Islands can be diagonally connected.  

**Solution:**  
- Use **BFS or DFS** to traverse all land cells (`1`s).  
- Mark visited islands to avoid counting them again.  
- Check **4 or 8 directions** based on the problem constraints.  

---

## 8. Maze (Shortest Path)

**Problem:**  
Find the shortest path in a maze with BFS.  
Variation: Walls that can be broken a limited number of times.  

**Solution:**  
- Use **BFS** since it finds the shortest path in an unweighted graph.  
- If walls can be broken, track the remaining break chances in the queue.  

---

## 9. Constellation Counting (Manhattan Distance)

**Problem:**  
Given a set of points, determine how many constellations exist.  
Two stars belong to the same constellation if their Manhattan distance is ≤ `k`.  

**Solution:**  
- Treat each star as a node and edges as **Manhattan distance ≤ k**.  
- Use **BFS or DFS** to count connected components.  

---

## 10. Cycle Detection

**Problem:**  
Detect if a cycle exists in an undirected graph represented as a grid.  

**Solution:**  
- Use **BFS with parent tracking** to detect cycles.  
- If a visited node is encountered again (excluding the parent), a cycle exists.  

---

## 11. Snake & Ladder

**Problem:**  
Find the shortest path to reach the last cell using ladders and avoiding snakes.  

**Solution:**  
- Treat the board as a **graph** where each square is a node.  
- Use **BFS** to simulate dice rolls, applying ladders/snakes as instant jumps.  

---

## 12. Laughing Bomb (Chain Reaction)

**Problem:**  
Bombs explode and trigger nearby bombs. Find how many bombs explode from an initial trigger.  

**Solution:**  
- Use **multi-source BFS** to simulate explosions spreading.  
- Track affected bombs and continue until no further explosions occur.  

---

## 13. Virus Spread

**Problem:**  
A virus spreads in a grid every second. Find how long until all cells are infected.  
Variation: Identify the best place to start the infection for the fastest spread.  

**Solution:**  
- Use **multi-source BFS** to spread the virus simultaneously from all infected cells.  
- Track time taken to reach each cell.  

---

## 14. Multi-Source BFS for Contamination

**Problem:**  
Multiple sources of contamination spread at the same time. Find the time taken for complete contamination.  

**Solution:**  
- Initialize all contaminated sources in a **queue**.  
- Process BFS in levels, marking newly infected cells.  

---

## 15. Rotten Oranges (Multi-Source BFS)

**Problem:**  
Some oranges are rotten and spread rot each second. Find the time for all oranges to rot.  

**Solution:**  
- Use **multi-source BFS** to spread rot from all rotten oranges.  
- Track time for complete contamination.  
- If fresh oranges remain uninfected, return `-1`.  

---

## 16. Moving Walls in a Grid

**Problem:**  
Walls shift every second, affecting paths. Find a way to escape while avoiding moving walls.  

**Solution:**  
- Use **BFS with dynamic grid updates** to track wall positions.  
- Consider wall movement when checking valid moves.  

---

## 17. Robot Vacuum Path Optimization

**Problem:**  
A vacuum must clean all dirty cells with the shortest path.  

**Solution:**  
- Use **BFS** to find the shortest path to each uncleaned cell.  
- Optimize order of cleaning using **priority queues**.  

---

## 18. Knight’s Shortest Path (Chessboard BFS)

**Problem:**  
Find the minimum moves for a knight to reach a target position.  

**Solution:**  
- Use **BFS** since knight movement is unweighted.  
- Use a **queue** to explore all legal knight moves.  

---

## 19. Word Ladder (Shortest Transformation Sequence)

**Problem:**  
Convert a word into another by changing one letter at a time.  

**Solution:**  
- Treat words as nodes and edges as one-letter transformations.  
- Use **BFS** to find the shortest transformation sequence.  

---

## 20. Password Cracking (Lexicographical BFS)

**Problem:**  
Generate all possible password sequences in order.  

**Solution:**  
- Use **BFS with lexicographical order** to generate possible sequences.  

---

This document provides insights into different BFS problem types and their solutions.
