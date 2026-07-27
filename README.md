# BREADTH-FIRST-SEARCH

# ExpNo 3: Implement Breadth First Search Traversal of a Graph

### Name: KATHIRESAN K
### Register Number: 212223110021   

## Aim

To implement Breadth First Search (BFS) Traversal of a Graph using Python 3.

---

## Theory

Breadth-First Traversal (or Search) for a graph is similar to the Breadth-First Traversal of a tree. The only difference is that, unlike trees, graphs may contain cycles, causing the same node to be encountered multiple times.

To avoid processing a node more than once, vertices are divided into two categories:

- Visited
- Not Visited

A Boolean **visited** array (or set) is used to keep track of visited vertices. For simplicity, it is assumed that all vertices are reachable from the starting vertex. BFS uses a **Queue** data structure for traversal.

### How does BFS work?

Starting from the source (root) vertex, BFS first visits all the vertices at the current level before moving to the next level.

The algorithm uses a **queue** to store vertices waiting to be explored.

The steps are:

1. Initially, the queue and visited array are empty.
2. Insert the starting vertex into the queue and mark it as visited.
3. Remove the front vertex from the queue.
4. Visit all its unvisited neighboring vertices.
5. Mark each neighbor as visited and insert it into the queue.
6. Repeat the process until the queue becomes empty.

---

### BFS Traversal Illustration

#### Step 1: Initially queue and visited arrays are empty.

![Step 1](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8acdebf8-ecc2-4d10-a208-45cce441f059)

---

#### Step 2: Push node 0 into the queue and mark it as visited.

![Step 2](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/0e9ce012-8e1f-43d7-b7b9-c0fb19fe0c3f)

---

#### Step 3: Remove node 0 and enqueue its unvisited neighbors.

![Step 3](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/67d8fa3b-ce9e-46c2-9dd7-089e204e667a)

---

#### Step 4: Remove node 1 and enqueue its unvisited neighbors.

![Step 4](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/b0cf0fde-8a86-41cb-a054-36875ac24ab0)

---

#### Step 5: Remove node 2 and enqueue its unvisited neighbors.

![Step 5](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8968a163-6b3a-4f7e-8ad4-bbf24f326b9b)

---

#### Step 6: Remove node 3.

Since all of its neighboring nodes have already been visited, move to the next node in the queue.

![Step 6](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/7a1c1b16-ea69-497f-a099-8440200f6dc0)

---

#### Step 7: Remove node 4.

All of its neighbors have already been visited. The queue becomes empty, so the traversal terminates.

![Step 7](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8e16ffa3-c3d6-4774-822b-6eb84adedad9)

---

## Algorithm

1. Construct a graph with vertices and edges.
2. Use a **Queue** for Breadth First Traversal.
3. Insert the starting node into the queue.
4. Mark the starting node as visited.
5. Remove the front node from the queue.
6. Visit all of its adjacent (neighboring) vertices.
7. If a neighboring vertex is not visited:
   - Mark it as visited.
   - Add it to the queue.
8. Repeat Steps 5–7 until the queue becomes empty.

---

## Program
```py
from collections import deque

# Read number of vertices and edges
n, m = map(int, input().split())

# Create adjacency list
graph = {}

# Read edges
for _ in range(m):
    u, v = input().split()

    if u not in graph:
        graph[u] = []
    if v not in graph:
        graph[v] = []

    graph[u].append(v)
    graph[v].append(u)   # Remove this line if the graph is directed

# BFS Function
def bfs(start):
    visited = set()
    queue = deque()
    traversal = []

    visited.add(start)
    queue.append(start)

    while queue:
        node = queue.popleft()
        traversal.append(node)

        for neighbour in graph[node]:
            if neighbour not in visited:
                visited.add(neighbour)
                queue.append(neighbour)

    return traversal

# Start BFS from the first vertex entered
start_node = list(graph.keys())[0]

# Print BFS Traversal
print(bfs(start_node))
```
## Sample Input 1

```text
7 9
A B
A C
A F
C E
C F
C D
D E
D G
G F
```

### Sample Output 1

```python
['A', 'B', 'C', 'F', 'E', 'D', 'G']
```

---

## Sample Input 2

```text
5 6
0 1
0 2
1 2
1 3
2 4
3 4
```

### Sample Output 2

```python
['0', '1', '2', '3', '4']
```

---

## Result

Thus, a graph was constructed and the implementation of Breadth First Search (BFS) traversal was completed successfully.
