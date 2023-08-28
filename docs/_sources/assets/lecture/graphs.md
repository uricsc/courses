# Graphs

````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/tq3zPnrQIpU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
A graph is a data structure that consists of a set of vertices (also known as nodes) and a set of edges connecting them. The edges represent the relationships or connections between the vertices, and can be directed (pointing from one vertex to another) or undirected (connecting two vertices in both directions).

Graphs can be used to represent a wide range of real-world systems and networks, such as social networks, transportation networks, and computer networks. They are an important tool in computer science and are used in many applications, such as data mining, machine learning, and optimization.

Graphs can be represented in different ways, such as adjacency lists, adjacency matrices, and edge lists. Adjacency lists are a common representation, where each vertex is associated with a list of its adjacent vertices (i.e., the vertices that it is directly connected to).

Graph algorithms are used to analyze and manipulate graphs. Some common graph algorithms include traversal algorithms (such as depth-first search and breadth-first search), shortest path algorithms (such as Dijkstra's algorithm and the Bellman-Ford algorithm), and minimum spanning tree algorithms (such as Kruskal's algorithm and Prim's algorithm).

Overall, graphs are an important data structure in computer science, and understanding them is essential for solving many problems in fields such as computer networking, social network analysis, and transportation planning.
```

``` {card} Additional Resources
- []()
```

`````

% ```````` {image} https://miro.medium.com/max/4106/1*HpYMnHjGZWmH9NKRG05lAg.jpeg
```````` {image} https://miro.medium.com/max/2664/1*HYPtf5Vk135snk07gFzy2w.png
:align: center
````````
`````````

````````` {div} full-width
```````` {card} 
:link: https://www.geeksforgeeks.org/graph-and-its-representations/
`````` {grid}
````` {grid-item-card} Graph
:columns: 12
- a set of <i class="blue">vertices</i> connect pairwise by <i class="blue">edges</i>
`````
````` {grid-item-card}
:columns: 4
**Vertices**
- fundamental units of the graph known as vertex or nodes;
- every node/vertex can be labeled or unlabelled

**Edges**
- are drawn or used to connect two nodes of the graph
- can connect any two nodes in any possible way
- can be labeled or unlabelled
`````
````` {grid-item-card}
:columns: 8
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20200630111809/graph18.jpg
:align: center
gfg: graph vertices and edges
`````
``````

````````
`````````

## Examples

````````` {div} full-width
```````` {card} 
````` {grid}

```` {grid-item-card}
:columns: 6
``` {figure} https://www.maureeneppstein.com/mve_journal/wp-content/uploads/underground-map1.gif
:align: center
:height: 200px
London Underground (Tube) Map <br> vertex = subway stop;<br> edge = direct route
```
````
```` {grid-item-card}
:columns: 6
``` {figure} https://revolution-computing.typepad.com/.a/6a010534b1db25970b0147e0ae51b2970b-800wi
:align: center
:height: 200px
Facebook Social Network Map:<br> vertex = person;<br> edge = social relationship
```
````
```` {grid-item-card}
:columns: 6
``` {figure} https://allthingsgraphed.com/public/images/twitter/twitter-follower-graph-avatars.png
:align: center
:height: 200px
Twitter followers <br> vertex = Twitter account;<br> edge = Twitter follower
```
````
```` {grid-item-card}
:columns: 6
``` {figure} https://www.researchgate.net/publication/314491781/figure/fig5/AS:470414003576837@1489166846626/Protein-protein-network-analysis-based-on-regulated-genes-in-HEK293-cells-Interactions.png
:align: center
:height: 200px
Protein-protein interation network <br> vertex = protein;<br> edge = interaction
```
````

`````
````````
`````````

## Applications

````````` {div} full-width
```````` {card} 

| graph | vertex | edge |
| :-- | :--: | :--: |
| cell phone | phone | placed call |
| infectious disease | person | infection |
| financial | stock, currency | transactions |
| transportation | intersection | street |
| internet | router | fiber cable |
| web | web page | URL link |
| social relationship | person | friendship |

````````
`````````

```` {div} full-width

````

## Graph Types

```````````` {div} full-width
```````````  {card} 
``````````   {tab-set}
`````````    {tab-item} Types
`````` {figure} https://cdn-images-1.medium.com/max/1600/1*fYG3B8hi4O2kk6aHvFB5mg.png
``````
`````````
`````````    {tab-item} Undirected
``````` {grid}
`````` {grid-item-card}
:columns: 6
```` {glossary}
Graph
    a set of <i class="blue">vertices</i> connect pairwise by <i class="blue">edges</i> 

Path
    sequence of vertices connected by edges, with no repeated edges
````
``````
`````` {grid-item-card} 
:columns: 6
```` {glossary}
Definition
    two vertices are <i class="blue">connected</i> if there is a path between them 

Cycle
    path (with $\ge 1$ edge) whose first and last vertices are the same 
````
``````
`````` {grid-item-card}
:columns: 12
```` {figure} imgs/19_01.png
:align: center
````
``````
```````
`````````
`````````    {tab-item} Directed
``````` {grid}
`````` {grid-item-card}
:columns: 6
```` {glossary}
Graph
    a set of <i class="blue">vertices</i> connect pairwise by <i class="blue">edges</i> 

Directed Path
    sequence of vertices connected by edges, with no repeated edges 
````
``````
`````` {grid-item-card} 
:columns: 6
```` {glossary}
Definition
    vertex $w$ is <i class="rhody">reachable</i> from vertex $v$ if there is a directed path from $v$ to $w$

Directed Cycle
    directed path (with $\ge 1$ edge) whose first and last vertices are the same 
````
``````
`````` {grid-item-card}
:columns: 12
```` {figure} imgs/19_02.png
:align: center
````
``````
```````
`````````
``````````
```````````
````````````

## Graph Processing Problems

````````` {div} full-width
```````` {card} 

| problem | description |
| :--: | :--: |
| s-t path | Find a path between $s$ and $t$ |
| shortest s-t path | Find a path with the fewest edges between $s$ and $t$ |
| cycle | Find a cycle |
| Euler cycle | Find a cycle that uses each edge exactly once |
| Hamilton cycle | Find a cycle that uses each vertex exactly once |
| connectivity | Is there a path between ev ery pair of vertices? |
| graph isomorphism | Are two graphs isomorphic? |
| planarity | Draw the graph in the plane with no crossing edges |

````````
`````````

## Representation

```````````` {div} full-width
```````````  {card} 
``````````   {tab-set}
`````````    {tab-item} Digraph
``` {glossary}
Vertex representation
    For 0 through all positive values $V-1$
    Applications: use <i class="blue">symbol table</i> to convert between names and integers
```

``` {figure} imgs/19_03.png
:align: center
```

<br>

``` {glossary}
Definition
    a digraph is <i class="blue">simple</i> if it has no self-loops or parallel edges
```

``` {figure} imgs/19_04.png
:align: center
```
`````````
`````````    {tab-item} Adjacency-matrix
``` {card}
Maintain a $V-by-V$ boolean array; 

For each edge $v \rightarrow w$ in the digraph   
    
$$adj[v][w] \ =\ true$$
```

``` {figure} imgs/19_05.png
:align: center
```
`````````
`````````    {tab-item} Adjacency-lists
``` {card}
Maintain vertex-indexed array of lists
```

``` {figure} imgs/19_06.png
:align: center
```
`````````
`````````    {tab-item} In practice
``` {glossary}
Use adjacency-lists
    Algorithms based on iterating over vertices adjacent from $v$  
    Real-world graphs tend to be <i class="blue">sparce</i> ($\Theta(V)$ edges), not <i class="blue">dense</i> ($\Theta(V^2)$ edges)
```

<br>

| representation | space | add edge from <br> $v$ to $w$ | has edge from <br> $v$ to $w$ | iterate over vertices <br> adjacent from $v$? |
| :--: | :--: | :--: | :--: | :--: |
| adjacent matrix | $V^2$ | 1<sup>*</sup> | 1 | $V$ |
| adjacent lists | $E+V$ | 1 | $outdegree(v)$ | $outdegree(v)$ |

\* disallows parallel edges

`````````
``````````
```````````
````````````

