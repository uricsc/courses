# Graphs : Depth-First Search

```````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/Urx87-NMm6c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
Depth-first search (DFS) is a graph traversal algorithm that visits all the vertices in a graph by exploring as far as possible along each branch before backtracking. DFS starts at a specified vertex (the starting vertex) and then follows one of its edges to an adjacent vertex. It then recursively applies the same process to the adjacent vertex, and continues until it reaches a dead end (i.e., a vertex with no unvisited adjacent vertices). It then backtracks to the most recently visited vertex with unvisited adjacent vertices, and repeats the process until all vertices have been visited.

DFS can be used to perform a variety of operations on a graph, such as finding a path between two vertices, checking whether the graph is connected, and identifying cycles in the graph. DFS can also be modified to search for solutions in a problem space, such as finding the shortest path between two points in a maze.

DFS can be implemented using either a recursive or iterative approach. The recursive approach uses a function call stack to keep track of the visited vertices and backtrack when necessary. The iterative approach uses a stack data structure to keep track of the visited vertices and their adjacent vertices.

Overall, DFS is an important algorithm in graph theory and is widely used in many applications, such as network analysis, data mining, and artificial intelligence.
```

``` {card} Additional Resources
- []()
```

`````
````````

## DFS

```````````` {div} full-width
```````````  {card} 
``````````   {tab-set}
`````````    {tab-item} Reachability
``` {glossary}
Problem
    Given a digraph $G$ and vertex $s$, find all the vertices <i class="rhody">reachable</i> from $s$
```

``` {figure} imgs/19_07.png
:align: center
```
`````````
`````````    {tab-item} DFS
```{figure} https://media.geeksforgeeks.org/wp-content/uploads/20200507074112/ezgif.com-gif-maker61.gif
```
``` {glossary}
Goal
   Systemically traverse a digraph 
```

```cpp
void Graph::dfs( Vertex v )
{
  v.visited = true;
  for each Vertex w adjacent to v
    if( !w.visited )
      dfs( w );
}
```

``` {glossary} 
Typical applications
    Reachability: finding all vertices reachable from a given vertex  
    Path finding: find directed path from one vertex to another
```
`````````
`````````    {tab-item} Directed-DFS
``` {glossary}
To visit vertex $v$:  
    Mark vertex $v$  
    Recursively visit all unmarked vertices adjacent from $v$ 
```

``` {figure} https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg
:align: center

directed dfs
```

<!-- _Errata: E(G,J) should read, E(G,I)_ -->

`````````
`````````    {tab-item} Properties
``` {glossary}
Proposition
    DFS marks all vertices reachable from $s$ in $\Theta(E+V)$ time in the worst case
```

``` {glossary}
Proof
    Initializing an array of length $v$ takes $\Theta(V)$ time  
    Each vertex is visited at most once  
    Visiting a vertex takes time proportional to its outdegree:  
```

$$outdegree(v_0) + outdegree(v_1) + outdegree(v_2) + \dots = E$$
$$in\ worst\ case,\ all\ V\ vertices\ reachable\ from\ s$$

``` {glossary}
Note
    If all vertices are reachable from $s$, then $E \ge V - 1$, so $V$ is a lower-order term
```
`````````
`````````    {tab-item} Application 1
```````` {admonition} Program control-flow analysis
``````` {grid}

`````` {grid-item-card}
``` {glossary}
Every program is a digraph
    Vertex = basic block of instructions (straight-line program)  
    Edge = jump

Dead-code elimination
    Find (and remove) unreachable code

Infinite-loop detection
    Determine whether exit is unreachable
```
``````
`````` {grid-item-card}
``` {figure} imgs/19_12.png
:align: center
```
``````
```````
````````
`````````
`````````    {tab-item} Application 2
```````` {admonition} Mark-sweep garbage collection
``````` {grid}

`````` {grid-item-card}
``` {glossary}
Every program is a digraph
    Vertex = basic block of instructions (straight-line program)
    Edge = jump

Roots
    Objects known to be directly accessible by a program (eg stack frame)

Reachable objects
    Objects indirectly accessible by program (starting at a root and following a chain of pointers)

Memory cost
    Uses 1 extra mark bit per object (plus DFS function-call stack)
```
``````
`````` {grid-item-card}
``` {figure} imgs/19_13.png
:align: center
```
``````
```````
````````
`````````
``````````
```````````
````````````

## Path Finding

````````````` {div} full-width
````````````  {card}
```````````   {tab-set}
``````````    {tab-item} Directed Path DFS
``` {glossary}
Goal
    DFS determines which vertices are reachable from s. How to reconstruct paths?

Solution
    Use <i class="blue">parent-link representation</i>
```

`````` {grid}
````` {grid-item}
``` {figure} imgs/19_10.png
:align: center
reachable from $0$
```
`````
````` {grid-item}
``` {figure} imgs/19_14.png
:align: center
parent-link representation of paths from vertex $0$
```
`````
``````
``````````
``````````    {tab-item} Parent-link
``` {glossary}
Parent-link representation of paths from $s$
    Maintain an integer array $edgeTo[]$  
    Interpretation: $edgeTo[v]$ is the next-to-last vertex on a path from $s$ to $v$  
    To reconstruct path from $s$ to $v$, trace $edgeTo[]$ backward from $s$ to $v$ (and reverse)
```

`````` {grid}
````` {grid-item}
``` {figure} imgs/19_15.png
:align: center
reachable from $0$
```
`````
````` {grid-item}
``` {figure} imgs/19_16.png
:align: center
parent-link representation of paths from vertex $0$
```
`````
````` {grid-item}
``` {code-block} cpp
public Iterable<Integer> pathTo(int v) {
  if (!marked[v]) return null; 
  Stack<Integer> path = new Stack<>(); 
  for (int x = v; x != s; x = edgeTo[x]) 
    path.push(x); 
  path.push(s); 
  return path; 
}
```
`````
``````
``````````
```````````
````````````
`````````````

## Undirected Graphs

````````````` {div} full-width
````````````  {card}
```````````   {tab-set}
``````````    {tab-item} Flood Fill
``` {glossary}
Problem
    Implement flood fill (Photoshop magic wand)
```

``` {figure} https://static.wixstatic.com/media/bb1bd6_591167b0be9940758124b35badf1da3a~mv2.gif
:align: center
magic wand tool
```
``````````
``````````    {tab-item} Graphs
``` {glossary}
Problem
    Given an undirected graph $G$ and vertex $s$, find all vertices connected to $s$

Solution
    Treat undirected graph as a digraph, replacing each edge with two antiparallel edges
```

``` cpp
DFS (to visit a vertex v)
------------------------
Mark vertex v.
Recursively visit all unmarked
    vertices w adjacent to v
```

``` {glossary}
Typical applications
    Find all vertices connected to a given vertex
    Find a path between two vertices
```
``````````
``````````    {tab-item} Undirected Search
``` {glossary}
To visit vertex $v$:  
    Mark vertex $v$  
    Recursively visit all unmarked vertices adjacent from $v$ 
```

`````` {grid}
````` {grid-item}
:columns: 6
```` {dropdown} ![image](imgs/19_17.png)
``` {figure} imgs/19_19.png
:align: center
vertices connected to $0$ (and associated paths)
```
`````
````` {grid-item}
:columns: 6
```` {dropdown} ![image](imgs/19_18.png)
``` {figure} imgs/19_20.png
:align: center

```
`````
``````
``````````
``````````    {tab-item} Search
``` {glossary}
Tree traversal
    Many ways in a binary tree
```

`````` {grid}
````` {grid-item}
```` {card} 
``` {glossary}
stack/recursion  
    $$\begin{align}
    Inorder      & \ \ \ \ \ \{ A, C, E, H, M, R, S, X \} \\ 
    Preorder     & \ \ \ \ \ \{ S, E, A, C, R, H, M, X \}\\
    Postorder    & \ \ \ \ \ \{ C, A, M, H, R, E, X, S \}  \\
    \end{align}$$

queue  
    $$Level-order \ \ \ \ \ \{ S, E, X, A, R, C, H, M \} $$
```
````
`````
````` {grid-item}
``` {figure} imgs/19_21.png
:align: center
parent-link representation of paths from vertex $0$
```
`````
``````

``` {glossary}
Graph search
    Many ways to explore a graph
```

``` {card}
- DFS preorder: vertices in order of calls to $dfs(G,v)$
- DFS postorder: vertices in order of return calls from $dfs(G,v)$
- Breadth-first: vertices in increasing order of distance from $s$
```
``````````
```````````
````````````
`````````````

