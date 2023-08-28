# Left-Leaning Red-Black Trees

````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/qvZGUFHWChY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
Left-leaning red-black trees (LLRB trees) are a type of self-balancing binary search tree data structure. They are similar to red-black trees, but they use a simpler set of rules for maintaining balance, and are left-leaning, meaning that all red nodes are left children.

Like red-black trees, LLRB trees use color to represent whether a node is red or black. The color of a node is used to ensure that the tree remains balanced and that the height of the tree is logarithmic in the number of elements stored in the tree.

In LLRB trees, a red node always has a black parent, and no red node has a red parent. Additionally, all null links (i.e., links to non-existent children) are considered to be black. These rules ensure that the tree remains balanced, and that no two red nodes are adjacent.

One of the advantages of LLRB trees over other self-balancing trees is their simplicity. The rules for maintaining balance in an LLRB tree are straightforward, and it is relatively easy to implement them in code.

Overall, LLRB trees are an important data structure in computer science, and are commonly used in database systems, compilers, and other applications where efficient search and insertion are important.
```

``` {card} Additional Resources

- [Red-black trees in 3 minutes — Rotations](https://youtu.be/95s3ndZRGbk)
- [Red-black trees in 5 minutes — Insertions (strategy)](https://youtu.be/5IBxA-bZZH8)
- [Red-black trees in 5 minutes — Insertions (examples)](https://youtu.be/A3JZinzkMpk)
- [Red-black trees in 8 minutes — Deletions](https://youtu.be/lU99loSvD8s)
- [Red-black trees in 6 minutes — Delete Fixes](https://youtu.be/iw8N1_keEWA)
```

`````
`````````

<!-- ```````` {card}
``` {image} http://mew.org/~kazu/proj/red-black-tree/okasaki.png
:align: center
```
```````` -->


## Left-leaning red-black BSTs

````````` {div} full-width


``` {admonition} Structure
:class: tip

A left-leaning red-black tree is a type of self-balancing binary search tree that maintains the following properties:

- Every node is colored either red or black.
- The root node is always black.
- Every leaf (null node) is considered black.
- If a node is red, both its children are black.
- Every path from a node to its descendant leaves contains the same number of black nodes.
```

<!-- `````` {grid}

````` {grid-item-card}
:columns: 6
```` {figure} imgs/llrb/17_05.png
:align: center
$3-node$
````
`````

````` {grid-item-card}
:columns: 6
```` {figure} imgs/llrb/17_06.png
:align: center
$b\ is\ the\ larger\ root\ key$
````
`````

`````` -->

`````````

### [Why Red-Black Trees?](https://www.geeksforgeeks.org/introduction-to-red-black-tree/)

````````` {div} full-width
```````` {card}
``````` {tab-set}

`````` {tab-item} Applications

> - Most of the self-balancing BST library functions like map, multiset, and multimap in C++ use Red-Black Trees.  
> - Implementing CPU Scheduling Linux.
> - K-mean clustering algorithm in machine learning for reducing time complexity.  
> - MySQL also uses the Red-Black tree for indexes on tables in order to reduce the searching and insertion time.  
> - Implementation of the virtual memory manager in some operating systems, to keep track of memory pages and their usage.  
> - Many programming languages (such as Java, C++, and Python) have implemented Red Black Trees as a built-in data structure for efficient searching and sorting of data.  
> - Implementation of graph algorithms such as Dijkstra’s shortest path algorithm and Prim’s minimum spanning tree algorithm.  
> - Implementation of game engines.  
>
> -- Geeks For Geeks

``````
`````` {tab-item} Advantages

> - Guaranteed time complexity of O(log n) for basic operations like insertion, deletion, and searching.
> - Self-balancing.
> - Used in a wide range of applications due to their efficient performance and versatility. 
> - The mechanism used to maintain balance in Red Black Trees is relatively simple and easy to understand.
> 
> -- Geeks For Geeks


``````

`````` {tab-item} Disadvantages

> - Red Black Trees require one extra bit of storage for each node to store the color of the node (red or black). 
> - Complexity of Implementation.
> - Although Red Black Trees provide efficient performance for basic operations, they may not be the best choice for certain types of data or specific use cases.
> 
> -- Geeks For Geeks

``````

```````
````````
`````````

### Implementing 2-3 trees with binary trees

````````` {div} full-width
```````` {card}
``````` {tab-set}

`````` {tab-item} Challenge

**How to represent a 3-node?**

``` {figure} https://iq.opengenus.org/content/images/2020/06/2-3-Tree-1.png
:align: center
```
``````
`````` {tab-item} Approach 1

``` {dropdown} Regular BST
- No way to tell a 3-node from a 2-node
- Can't (uniquely) map from BST back to 2-3 tree
```
``` {figure} imgs/llrb/17_02.png
:align: center
```

``````

`````` {tab-item} Approach 2

``` {dropdown} Regular BST with red "glue" nodes
- Wastes space for extra node
- Messy code 
```
``` {figure} imgs/llrb/17_03.png
:align: center
```
``````

`````` {tab-item} Approach 3

``` {dropdown} Regular BST with red "glue" links
- Widely used in practice
- Arbitrary restriction: red links lean left  
```
``` {figure} imgs/llrb/17_04.png
:align: center
```
``````

```````
````````
`````````

### 1-1 correspondence with 2-3 trees

````````` {div} full-width
```````` {card} Key Properties

`````` {grid}

````` {grid-item-card}
:columns: 5
```` {figure} imgs/llrb/17_07.png
:align: center

$2-3\ tree$
````
`````

````` {grid-item-card}
:columns: 7
```` {figure} imgs/llrb/17_09.png
:align: center

$horizontal\ red\ links$
````
`````


````` {grid-item-card}
:columns: 12
```` {figure} imgs/llrb/17_08.png
:align: center

$red-black\ tree$
````
`````
``````

````````
`````````

### Definition of LLRB trees (without reference to 2-3)

````````` {div} full-width
```````` {card}

```` {card} A BST such that
- No node has two red links connected to it
- Red links lean left
- Every path from root to null has the same number of black links
````

``` {figure} imgs/llrb/17_08.png
:align: center

$red-black\ tree$
````````
`````````

### Search

#### Observation

````````` {div} full-width
```````` {card}

``` {card}
Search is the same as for BST (ignore color)
```

`````` {grid}
````` {grid-item}
:columns: 5
```cpp
public Value get(Key key) {
  Node x = root;  
  while (x != null) {
    int cmp = key.compareTo(x.key);
    if      (cmp <  0)  x = x.left;
    else if (cmp >  0)  x = x.right;
    else if (cmp == 0)  return x.val;
  }
  return null;
}
```
`````
````` {grid-item}
:columns: 7
``` {figure} imgs/llrb/17_08.png
:align: center
$red-black\ tree$
```
`````

``````

``` {card}
Remark: Many other ops (floor, iteration, rank, selection) are also identical
```

````````
`````````

### Representation

````````` {div} full-width
```````` {card}

``` {card}
Each node is pointed to by precisely one link (from its parent) $\Rightarrow$ can encode color of links in nodes
```

`````` {grid}
````` {grid-item-card}
:columns: 7
```java
private static final boolean RED   = true;
private static final boolean BLACK = false;

private class Node {
  Key     key;  
  Value   val;
  Node    left;
  Node    right;
  // color of parent link
  Boolean color;
}

private boolean isRed(Node x) {
  // null links are black
  if (x == null) return false;    
  return x.color == red;
}
```
`````
````` {grid-item-card}
:columns: 5
``` {figure} imgs/llrb/17_10.png
:align: center
```
``` {card}
$$h = root\\$$  
$$h.left.color\ is\ RED\\$$  
$$h.right.color\ is\ BLACK$$
```
`````

``````

````````
`````````

### The road to LLRB trees

````````` {div} full-width
```````` {card}

`````` {tab-set}
````` {tab-item} 1
``` {figure} imgs/llrb/17_11.png
:align: center
:width: 300px
BSTs can get imbalanced
```
`````
````` {tab-item} 2
``` {figure} imgs/llrb/17_07.png
:align: center
2-3 trees (balanced but awkward to implement)
```
`````
````` {tab-item} 3
``` {figure} imgs/llrb/17_09.png
:align: center
3-nodes "glued" together with red links
```
`````
````` {tab-item} 4
``` {figure} imgs/llrb/17_08.png
:align: center
LLRB trees (color in links)
```
`````
````` {tab-item} 5
``` {figure} imgs/llrb/17_12.png
:align: center
implementing LLRB trees (color in nodes)
```
`````
``````

````````
`````````

## Red-Black Tree Operations

````````` {div} full-width
````````  {card} 
```````   {tab-set}
``````    {tab-item} Overview

``` {card} Basic strategy
Maintain 1-1 correspondence with 2-3 trees
```

``` {card} During internal operations, maintain
- Symmetric order.
- Perfect black balance.
- [ but not necessarily color invariants ]
```

````` {grid} Example violations of color invariants
```` {grid-item-card}
:columns: 3
``` {figure} img/llrb/17_13.png
right-leaning red link
```
````
```` {grid-item-card}
:columns: 3
``` {figure} img/llrb/17_14.png
two red children (a temporary 4-node)
```
````
```` {grid-item-card}
:columns: 3
``` {figure} img/llrb/17_15.png
left-left red (a temporary 4-node)
```
````
```` {grid-item-card}
:columns: 3
``` {figure} img/llrb/17_16.png
left-right red (a temporary 4-node)
```
````
`````

``` {card}
<var class="blue">To restore color invariants</var>: perform <var class="red">rotations</var> and <var class="red">color flips</var>
```

``````
``````    {tab-item} Left rotation
``` {card}
**Orient a (temporarily) right-leaning red link to lean left**
```

````` {grid}
```` {grid-item-card} Rotate E left
:columns: 4
``` {figure} imgs/llrb/17_17.png
:align: center
before...
```
````
```` {grid-item-card} Pseudocode
:columns: 4
```cpp
private Node rotateLeft(Node h) {
  assert isRed(h.right);
  Node x  = h.right;
  h.right = x.left;
  x.left  = h
  x.color = h.color;
  h.color = RED;
  return x;
}
```
````
```` {grid-item-card} Rotate E left
:columns: 4
``` {figure} imgs/llrb/17_18.png
:align: center
after...
```
````
`````

``` {card}
<var class="blue">Invariants</var>: Maintains symmetric order and perfect balance
```
``````
``````    {tab-item} Right rotation

``` {card}
**Orient a left-leaning red link to (temporarily) lean right**
```

````` {grid}
```` {grid-item-card} Rotate E right
:columns: 4
``` {figure} imgs/llrb/17_18.png
:align: center
before...
```
````
```` {grid-item-card} Pseudocode
:columns: 4
```cpp
private Node rotateLeft(Node h) {
  assert isRed(h.right);
  Node x  = h.left;
  h.left  = x.right;
  x.right = h
  x.color = h.color;
  h.color = RED;
  return x;
}
```
````
```` {grid-item-card} Rotate E right
:columns: 4
``` {figure} imgs/llrb/17_17.png
:align: center
after...
```
````
`````

``` {card}
<var class="blue">Invariants</var>: Maintains symmetric order and perfect balance
```

``````
``````    {tab-item} Color flip

``` {card}
**Recolor to split a (temporary) 4-node**
```

````` {grid}
```` {grid-item-card} Color flip
:columns: 4
``` {figure} imgs/llrb/17_19.png
:align: center
before...
```
````
```` {grid-item-card} Pseudocode
:columns: 4
```cpp
private Node rotateLeft(Node h) {
  assert isRed(h);
  assert isRed(h.left);
  assert isRed(h.right);
  h.color        = RED;
  h.left.color   = BLACK;
  h.right.color  = BLACK;
}
```
````
```` {grid-item-card} Color flip
:columns: 4
``` {figure} imgs/llrb/17_20.png
:align: center
after...
```
````
`````

``` {card}
<var class="blue">Invariants</var>: Maintains symmetric order and perfect balance
```

``````
```````
````````
`````````

### Insertions

``````````` {div} full-width
`````````` {card} 

``` {card}
**Do standard BST insert** $\ \ \ \ \ \ \ \ \ \ \ \ \leftarrow$ preserves symmetric  order
```

``` {card}
**Color new link red** $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \leftarrow$ preserve perfect black balance
```

``` {card} Repeat up the tree until color invariants restored
- two left red links in a row?      $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \Rightarrow$ rotate right
- left and right links both red?    $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \Rightarrow$ color flip
- right link only red?              $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \Rightarrow$ rotate left
```

````````` {grid}
```````` {grid-item}
:columns: 6
``````` {card} Inserting H
`````` {tab-set}
````` {tab-item} 1
``` {figure} imgs/llrb/17_21.png
:align: center
[R]: add new node here
```
`````
````` {tab-item} 2
``` {figure} imgs/llrb/17_22.png
:align: center
[S]: two lefts in a row, rotate right
```
`````
````` {tab-item} 3
``` {figure} imgs/llrb/17_23.png
:align: center
[R]: both children red, flip colors
```
`````
````` {tab-item} 4
``` {figure} imgs/llrb/17_24.png
:align: center
[E]: right link, so rotate left
```
`````
````` {tab-item} 5
``` {figure} imgs/llrb/17_25.png
:align: center
complete
```
`````
``````
```````
````````
```````` {grid-item}
:columns: 6
``````` {card} Inserting P
`````` {tab-set}
````` {tab-item} 1
``` {figure} imgs/llrb/17_26.png
:align: center
[M]: add new node here
```
`````
````` {tab-item} 2
``` {figure} imgs/llrb/17_27.png
:align: center
[M]: both children red, flip colors
```
`````
````` {tab-item} 3
``` {figure} imgs/llrb/17_28.png
:align: center
right link red, rotate left
```
`````
````` {tab-item} 4
``` {figure} imgs/llrb/17_29.png
:align: center
two lefts in a row, rotate right
```
`````
````` {tab-item} 5
``` {figure} imgs/llrb/17_30.png
:align: center
both children red, flip colors
```
`````
````` {tab-item} 6
``` {figure} imgs/llrb/17_31.png
:align: center
complete
```
`````
``````
```````
````````

``````````
```````````

<!-- SLIDE 15 -->
### Visualize

````````` {div} full-width
```````` {card} Click the image to hyperlink and interact
:link: https://www.cs.usfca.edu/~galles/visualization/RedBlack.html
```` {image} imgs/llrb/17_rbt.png
:align: center
````

````````
`````````

### Implementation

````````` {div} full-width
```````` {card}

```` {card}
**Do standard BST insert and color new link red**
````

```` {card} Repeat up the tree until color invariants restored
- two left red links in a row?      $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \Rightarrow$ rotate right
- left and right links both red?    $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \Rightarrow$ color flip
- right link only red?              $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \Rightarrow$ rotate left
````

```cpp
private Node put(Node h, Key, k, Value v) {
  if (h == null) return new Node(key, val, RED;         // insert at bottom and color red
  
  int cmp = key.compareTo(h.key)
  if      (cmp <  0) h.left = put(h.left, key, val);
  else if (cmp >  0) h.left = put(h.right, key, val);
  else if (cmp == 0) h.val  = val);
  
  // following lines restore color invariants
  if (isRed(h.right) && !isRed(h.left))        h = rotateLeft(h);
  if (isRed(h.left ) && !isRed(h.left.left))   h = rotateRight(h);
  // only a few extra lines of code provides near-perfect balance
  if (isRed(h.left ) && isRed(h.right))        h = flipColors(h);           
  
  return h;
}
```

````````
`````````

### Visualizations | $n=255$

````````` {div} full-width
```````` {card} 

`````` {tab-set}
````` {tab-item} Random order

$height = 9$  
$average\ depth = 6.3$

``` {figure} imgs/llrb/17_32.png
:align: center
random
```
`````
````` {tab-item} Ascending order

$height = 7$  
$average\ depth = 6.0$

``` {figure} imgs/llrb/17_33.png
:align: center
ascending
```
`````
````` {tab-item} Descending order

$height = 13$  
$average\ depth = 6.5$

``` {figure} imgs/llrb/17_34.png
:align: center
descending
```
`````
``````

````````
`````````

## Balance

````````` {div} full-width
```````` {card} 

``` {card} Proposition
Height of corresponding 2-3 tree is $\le log_2\ n$ 
```

``` {card} Proof
- Black height = height of corresponding 2-3 tree $\le log_2\ n$
- Never two red links in a row  
$\ \ \ \ \ \Rightarrow$ height of LLRB tree $\le (2 \times black\ height) + 1 \le 2\ log_2\ n$
- [A slightly more refined argument show $height\ \le 2\ log_\ n$]
```

``` {figure} imgs/llrb/17_35.png
:align: center
$height\ \le 2\ log_2\ n$
```
````````
`````````

## Summary

````````` {div} full-width
```````` {card} 
``` {figure} imgs/llrb/17_table.png
:align: center
hidden constant $c$ is small for r-b BST<br> (at most $2\ log_2\ n$ compares)
```
````````
`````````
