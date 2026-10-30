<h1>ExpNo 2 : Implementation of Breadth First Search Traversal</h1>
<h3>Name: Sanjeev D</h3>
<h3>Register Number: 212223040185</h3>

<h3>AIM:</h3>
<br>
<p>To Implement Breadth First Search Traversal of a Graph using Python 3.</p>
<br>

<h3>Theory</h3>
<h3>Breadth First Search (BFS):</h3>
<p>Breadth First Search is an uninformed search algorithm for traversing or searching tree or graph data structures. It begins at a selected root node and systematically explores all neighboring vertices at the present depth prior to moving on to vertices at the next depth level. To prevent re-processing nodes in cyclic graphs, a visited boolean table is maintained. BFS utilizes a First-In-First-Out (FIFO) queue (via collections.deque) to track adjacent frontier vertices, ensuring that the shortest path in terms of edge count is explored first.</p>
<hr>

<h3>DESIGN STEPS</h3>
<h3>STEP 1: Identifying the input:</h3>
<p>Number of nodes, number of edges, vertex pairs representing bidirectional edges, and the designated start node.</p>
<h3>STEP 2: Identifying the output:</h3>
<p>Constructed adjacency list of the graph and the sequential order of visited vertices during BFS traversal.</p>
<h3>STEP 3: Representing the Graph:</h3>
<p>Use a Python dictionary (<code>defaultdict(list)</code>) to build an adjacency list representing adjacent nodes for each vertex.</p>
<h3>STEP 4: Implementing the BFS Algorithm:</h3>
<p>Initialize a double-ended queue (<code>deque</code>), mark the start node as visited, enqueue it, and iteratively dequeue vertices while enqueuing all unvisited neighboring nodes.</p>
<h3>STEP 5: Displaying traversal results:</h3>
<p>Output the final traversal sequence as a connected path format (e.g., <code>A -> B -> C...</code>).</p>

<h3>PROGRAM</h3>
<hr>

```python
from collections import deque
from collections import defaultdict

def bfs(graph, start, visited, path):
    queue = deque()
    visited[start] = True
    queue.append(start)
    path.append(start)
    while queue:
        node = queue.popleft()
        for neighbour in graph[node]:
            if not visited[neighbour]:
                visited[neighbour] = True
                queue.append(neighbour)
                path.append(neighbour)
    return path

graph = defaultdict(list)
v, e = map(int, input("Enter the number of nodes and edges: ").split())
print("\nEnter the edges (Adjacent Nodes):")
for i in range(e):
    u, w = input(f"Edge {i+1} (u v): ").split()
    graph[u].append(w)
    graph[w].append(u)      

print("\nAdjacency List:")
for node in graph:
    print(node, "->", graph[node])

start = input("\nEnter the start node for BFS: ")
if start not in graph:
    print("Invalid start node!")
else:
    visited = defaultdict(bool)
    path = []
    traversedpath = bfs(graph, start, visited, path)
    print("\nBFS Traversal:", " -> ".join(traversedpath))
```
<hr>

<h3>OUTPUT:</h3>

```text
Enter the number of nodes and edges: 8 9

Enter the edges (Adjacent Nodes):
Edge 1 (u v): A B
Edge 2 (u v): A C
Edge 3 (u v): B E
Edge 4 (u v): C D
Edge 5 (u v): B D
Edge 6 (u v): C G
Edge 7 (u v): D F
Edge 8 (u v): G F
Edge 9 (u v): F H

Adjacency List:
A -> ['B', 'C']
B -> ['A', 'E', 'D']
C -> ['A', 'D', 'G']
E -> ['B']
D -> ['C', 'B', 'F']
G -> ['C', 'F']
F -> ['D', 'G', 'H']
H -> ['F']

Enter the start node for BFS: A

BFS Traversal: A -> B -> C -> E -> D -> G -> F -> H
```

<img width="873" height="363" alt="image" src="https://github.com/user-attachments/assets/03d320c1-fb5b-4d2f-aac3-4a8861b1a693" />
<img width="873" height="535" alt="image" src="https://github.com/user-attachments/assets/b3691f6c-e987-4071-a8dc-fd2924b5eff3" />


<h3>RESULT</h3>
<p>Thus, the Breadth First Search (BFS) Traversal of a graph was successfully implemented and executed using Python 3.</p>
