# Graphs : Breadth-First Search

```````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/HZ5YTanv5QE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
Breadth-first search (BFS) is a graph traversal algorithm that visits all the vertices in a graph in level order, exploring all the vertices at a given distance from the starting vertex before moving on to vertices at a greater distance. BFS starts at a specified vertex (the starting vertex) and visits all its neighbors before visiting the neighbors of its neighbors, and so on.

BFS uses a queue data structure to keep track of the vertices that have been visited but not yet processed. The starting vertex is added to the queue, and then while the queue is not empty, the algorithm removes the first vertex from the queue, visits its neighbors, and adds them to the queue if they have not already been visited.

BFS can be used to perform a variety of operations on a graph, such as finding the shortest path between two vertices, checking whether the graph is connected, and identifying cycles in the graph.

BFS can be implemented using an iterative approach with a queue data structure, which is more memory-efficient than the recursive approach used in DFS.

Overall, BFS is an important algorithm in graph theory and is widely used in many applications, such as network analysis, data mining, and artificial intelligence.
```

``` {card} Additional Resources
- []()
```

`````
````````

## Breadth-first (in digraphs)

````````````` {div} full-width
````````````  {card}
```````````   {tab-set}
``````````    {tab-item} Shortest paths

``` {glossary}
Problem
    Find directed path from $s$ to each other vertex that uses the <i class="rhody">fewest edges</i>

Key idea
    Visit vertices in increasing order of distance from $s$
```

`````` {grid}
````` {grid-item} 
:columns: 6
``` {card} Try writing some of the paths from  0 $\Rightarrow$ 6
Click below to enter your path...
<div contenteditable>0 - 2 - 7 - 4 - 5 - 1 - 3 - 6</div>
`````
````` {grid-item} 
:columns: 6
``` {figure} imgs/19_22.png
:align: center
```
`````
````` {grid-item} 
:columns: 6
``` {dropdown} directed paths from $0$ to $6$
$$0 \rightarrow 2  \rightarrow 7  \rightarrow 4  \rightarrow 5  \rightarrow 1  \rightarrow 3  \rightarrow 6  $$
$$0 \rightarrow 4  \rightarrow 5  \rightarrow 1  \rightarrow 3  \rightarrow 6   $$
$$0 \rightarrow 2  \rightarrow 7  \rightarrow 3  \rightarrow 6 $$
$$0 \rightarrow 2  \rightarrow 7  \rightarrow 0  \rightarrow 2  \rightarrow 7  \rightarrow 3  \rightarrow 6  $$
```
`````
````` {grid-item} 
:columns: 6
``` {dropdown} shortest path from $0$ to $6\ (length = 4)$
$$0 \rightarrow 2  \rightarrow 7  \rightarrow 3  \rightarrow 6 $$
```
`````
``````
 
``` {glossary}
Key idea
    Visit vertices in increasing order of distance from $s$

Key data structure
    Queue of vertices to visit
```

``` {figure} imgs/19_23.png
:align: center
```
``````````
`````````` {tab-item} BFS
``` {glossary}
Repeat until queue is empty
    Remove vertex $v$ from queue  
    Add to queue all unmarked vertices adjacent from $v$ and mark them
```

`````` {grid}
````` {grid-item-card}
:columns: 12
```cpp
BFS (from source s)
-----------------------------------------------
Add s to FIFO queue and mark s
Repeat until the queue is marked empty:
- remove the least recently added vertex
- for each unmarked vertex w adjacent from v:
  - add w to queue and mark w
```
`````
````` {grid-item-card}
:columns: 4
```` {dropdown} ![image](imgs/19_24.png)
``` {figure} imgs/19_26.png
:align: center
graph g
```
````
_Fig 58_
`````
````` {grid-item-card}
:columns: 3
``` {figure} imgs/19_25.png
:align: center
```
`````
````` {grid-item-card}
:columns: 5
| $v$ | $edgeTo[]$ | $marked[]$ | $distTo[]$ |
| :--: | :--: | :--: | :--: |
| 0 | - | T | 0 | 
| 1 | 0 | T | 1 |
| 2 | 0 | T | 1 |
| 4 | 2 | T | 2 |
| 3 | 4 | T | 3 |
| 5 | 3 | T | 4 |
`````
``````
``````````
`````````` {tab-item} Properties
``` {glossary}
Proposition
    In the worst case, BFS takes $\Theta(E + V)$ time

Proof
    Each vertex reachable from $s$ is visited once
```

`````` {grid}
````` {grid-item-card}
:columns: 6
``` {figure} imgs/19_28.png
:align: center
digraph g
```
`````
````` {grid-item-card}
:columns: 6
``` {figure} imgs/19_29.png
:align: center
&nbsp;
```
`````
``````
``````````
`````````` {tab-item} Ex 1
````````` {admonition} Single-sink Shortest Paths

Given a digraph and a <i class="blue">target</i> vertex $t$, find shortest path from every vertex to $t$

``````` {card} Ex 1</i> $t = 0$  
`````` {grid}
````` {grid-item}
:columns: 4
``` {dropdown} Shortest path *from* $7$ 
$7 \rightarrow 6 \rightarrow 0$
```
``` {dropdown} Shortest path *from* $5$
$5 \rightarrow 4 \rightarrow 2 \rightarrow 0$
```
``` {dropdown} Shortest path *from* $12$
$12 \rightarrow 9 \rightarrow 11 \rightarrow 4 \rightarrow 2 \rightarrow 0$ 
```
`````
````` {grid-item-card}
:columns: 8
``` {figure} imgs/19_31.png
:align: center
```
`````
``````
`````````
``````````

`````````` {tab-item} Ex 2

````````` {admonition} Multiple-source Shortest Paths

Given a digraph and a <i class="rhody">set</i> of source vertices, find shortest path from <i class="rhody">any</i> vertex in the set to every other vertex

``````` {card} Example</i> $S = \{ 1, 7, 10 \}$  
`````` {grid}
````` {grid-item}
:columns: 4
``` {dropdown} Shortest path *to* $4$ 
$7 \rightarrow 6 \rightarrow 4$
```
``` {dropdown} Shortest path *to* $5$
$7 \rightarrow 6 \rightarrow 0 \rightarrow 5$
```
``` {dropdown} Shortest path *to* $12$
$10 \rightarrow 12$
```
`````
````` {grid-item-card}
:columns: 8
``` {figure} imgs/19_31.png
:align: center
```
`````
``````
`````````
``````````
````````````
`````````````

## Breadth-first Search (in graphs)

`````````` {div} full-width
`````````  {card}
````````   {tab-set}
```````    {tab-item} Application: routing
``` {card}
Fewest number of hops in a communication network
```

``` {figure} https://images.theconversation.com/files/144160/original/image-20161102-27228-1iicfpi.jpg?ixlib=rb-1.1.0&q=45&auto=format&w=600&h=390&fit=crop&dpr=1
:width: 500
ARPANET 1969 - 1977
```
```````    
```````    {tab-item} BFS: undirected graphs
``` {glossary}
Problem
    Find path between $s$ and each other vertex that uses fewest edges
Solution
    Treat as a digraph, replacing each undirected edge with two antiparallel edges
```

```cpp
BFS (from source s)
-----------------------------------------------
Add s to FIFO queue and mark s
Repeat until the queue is empty:
- remove the least recently added vertex v
- for each unmarked vertex w adjacent from v:
  - add w to queue and mark w
```
```````    
````````
`````````
``````````

## Summary

### Graph traversal

`````````` {div} full-width
````````` {card} BFS and DFS enables efficient solution to many (but not all) graph and digraph problems

| graph problem | BFS | DFS | time |
| :-- | :--: | :--: | :--: |
| s-t path | ✔︎ | ✔︎ | E + V |
| shortest s-t path | ✔︎ |  | E + V |
| shortest directed cycle | ✔︎ |  | E V |
| Euler cycle |  | ✔︎ | E + V |
| Hamilton cycle |  |  | $2^{1.657 V}$ |
| bipartiteness | ✔︎ | ✔︎ | E + V |
| connected components | ✔︎ |  ✔︎| E + V |
| strong conmponents |  | ✔︎ | E + V |
| planarity |  | ✔︎ | E + V |
| graph morphism |  |  | $2^{c\ ln^{3}\ V}$ |

`````````
``````````


%``` {figure} http://i1.wp.com/blog.hackerearth.com/wp-content/uploads/2015/05/dfsbfs_animation_final.gif?resize=640%2C333
%```