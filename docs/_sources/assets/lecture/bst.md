# Binary Search Trees

````` {div} full-width

<style>
summary:first-of-type {text-align: center;}
</style>

``` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/GzJoqJO1zdI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
`````

<!-- ![](https://miro.medium.com/max/1104/1*WEIGkEtQndEvPVwHAh4aSA.png) -->

## Binary Tree

````` {div} full-width

``` {admonition} Overview
:class: tip

- A binary tree is a hierarchical data structure consisting of nodes.
- Each node contains a value and references to its left and right children.
- The left child is smaller than the parent, while the right child is larger.
```

```` {card}

``` {figure} https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Binary_tree_v2.svg/1920px-Binary_tree_v2.svg.png
:align: center
:width: 50%

```
$$bin\_tree = \{1, 7, 9, 2, 6, 9, 5, 11, 5 \}$$

````
`````

### [Implementing binary trees](https://www.geeksforgeeks.org/applications-priority-queue/)  

``````` {div} full-width
`````` {card}
````` {grid}
```` {grid-item-card}
:columns: 3
Node
: $data$
: $left$ child
: $right$ child

````
```` {grid-item-card}
:columns: 9
``` {figure} imgs/15_s7.png
```
 
$tree = \{a, b, c, d, e, f\}$
````
`````
``````
```````


## [$k$-ary trees](https://www.geeksforgeeks.org/k-ary-heap/?ref=gcse)

``````````` {div} full-width
`````````` {card}
````````` {tab-set}
```````` {tab-item} k-ary trees




``` {figure} https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.7TSf_YpdLyF0uIfW0Rm_GgHaHa%26pid%3DApi&f=1&ipt=1187f0ed9de515a480afca769ea805a6e4e566d0faeae559c7cf2c0b42873442&ipo=images
Every node has between $0$ and $k$ children
```



````````
```````` {tab-item} types

``` {figure} https://miro.medium.com/v2/resize:fit:1400/format:webp/1*CMGFtehu01ZEBgzHG71sMg.png

```
````````
```````` {tab-item} full

``` {figure} https://miro.medium.com/max/1400/1*fh2By4u-SxTlt6u2xHqnCg.png
<br>Full Binary Tree is a Binary Tree in which every node has 0 or 2 children.  
-- [towardsdatascience.com](https://towardsdatascience.com/5-types-of-binary-tree-with-cool-illustrations-9b335c430254)
```
````````
```````` {tab-item} complete

``` {figure} https://miro.medium.com/max/1400/1*M1qfRR59TR9-i4pmI-_Clg.png
<br>Complete Binary Tree has all levels completely filled with nodes except the last level and in the last level, all the nodes are as left side as possible.
-- [towardsdatascience.com](https://towardsdatascience.com/5-types-of-binary-tree-with-cool-illustrations-9b335c430254)
```
````````
```````` {tab-item} perfect

``` {figure} https://miro.medium.com/max/1400/1*EgcvwUHXnmdOpbHQwgCknA.png
<br>Perfect Binary Tree is a Binary Tree in which all internal nodes have 2 children and all the leaf nodes are at the same depth or same level.
-- [towardsdatascience.com](https://towardsdatascience.com/5-types-of-binary-tree-with-cool-illustrations-9b335c430254)
```
````````
```````` {tab-item} degenerate

``` {figure} https://miro.medium.com/max/1400/1*m5BjLJeSrSGH4US-QXj4aA.png
<br>Degenerate Binary Tree is a Binary Tree where every parent node has only one child node.
-- [towardsdatascience.com](https://towardsdatascience.com/5-types-of-binary-tree-with-cool-illustrations-9b335c430254)
```
````````
```````` {tab-item} balanced

``` {figure} https://miro.medium.com/max/1400/1*jSq-xjEZYytNDIBpZNQC2w.png
<br>Balanced Binary Tree is a Binary tree in which height of the left and the right sub-trees of every node may differ by at most 1.
-- [towardsdatascience.com](https://towardsdatascience.com/5-types-of-binary-tree-with-cool-illustrations-9b335c430254)
```
````````
`````````
``````````
```````````

<!-- ![](https://mathworld.wolfram.com/images/eps-gif/BinaryTrees_800.gif) -->


## Binary Search Trees

````````` {div} full-width

```` {admonition} Understanding BSTs
:class: tip

``` {figure} https://blog.penjee.com/wp-content/uploads/2015/11/binary-search-tree-sorted-array-animation.gif
```

- Each node in a binary tree can have at most two children.
  - This means that a node can have either zero, one, or two children.
- The left child of a node is typically smaller than the node, while the right child is larger (or equal) than the node.
  - This rule is often associated with binary search trees (BSTs), where the values are arranged in a specific order for efficient searching and retrieval.
- The order of children matters.
  - In a binary tree, the left child is typically referenced before the right child.
  - The order of children affects the tree's traversal and interpretation.
- Nodes are connected by edges.
  - The connections between nodes are represented by edges in a binary tree.
  - Each node (except the root) has exactly one incoming edge from its parent.
- The height of a binary tree.
  - The height of a binary tree is the maximum number of edges from the root to a leaf node.
  - It represents the longest path from the root to any leaf node in the tree.
- The depth (level) of a node.
  - The depth (or level) of a node in a binary tree represents the number of edges from the root to that node.
  - The root node is at depth 0, its children are at depth 1, and so on.
- The number of nodes in a binary tree.
  - The total number of nodes in a binary tree can vary.
  - The minimum number of nodes in a binary tree is 0, while the maximum number depends on the height of the tree.
````

```````` {grid}
`````` {grid-item-card}
:columns: 3

Simplified is <var class="rd">bst</var>

A BST has <var class="rd">symmetric order</var>

- each node $x$ in a BST has a key 

$$key(x)$$

- for all nodes $y$ in the left subtree of $x$, 

$$key(y) < key(x)^{**}$$

- for all nodes $y$ in the right subtree of $x$, 

$$key(y) > key(x)^{**}$$
``````
`````` {grid-item-card}
:columns: 9

`````  {tab-set}
```` {tab-item} Example

``` {figure} https://i.pinimg.com/originals/4e/5a/00/4e5a00c98d5b46ed4cbf224ac11dc115.png
:align: center
```
(**) assume that the keys of a BST are pairwise distinct
````
```` {tab-item} Tree Parts

``` {figure} https://res.cloudinary.com/practicaldev/image/fetch/s--od-naD9n--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://miro.medium.com/max/975/1*PWJiwTxRdQy8A_Y0hAv5Eg.png
```
````
`````
<!-- ![](https://codestandard.net/articles/en/images/binary-search-tree_0.jpg#article_image) -->
``````
````````
`````````

<!-- SLIDE 10 -->
### BST Classes

``````` {div} full-width
`````` {card}
````` {grid}
```` {grid-item-card} BSTNode
```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 
class BSTNode { 
  
  private: 
    int data;  
    BSTNode *left;  
    BSTNode *right;
  
  public:
    BSTNode(int d);
    ~BSTNode();
  
  friend class BSTree;

};

```
````

```` {grid-item-card} BSTree
```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 
class BSTree{
  
  private:
    BSTNode *root;
    void destroy(BSTNode *p);
    
  public:
    BSTree();
    ~BSTree();
    void insert(int d);
    void remove(int d);  
    BSTNode *search(int d);

};
```
````
`````
``````
```````

### `search`

``````` {div} full-width
`````` {card}
````` {grid}
```` {grid-item-card}
:columns: 4

1. Start at root node
2. If the search key:  
    a. matches the current node’s key  
        * then <span class="green">found</span>  
    b. If search key $>$ current node’s key  
        * <span class="red">search</span> on $right$ child  
    c. If search key is less than current node’s  
        * <span class="red">search</span> on $left$ child   
3. Stop when current node is NULL (<span class="rrd">not found</span>)
````
```` {grid-item-card}
:columns: 8

``` {image} https://www.happycoders.eu/wp-content/uploads/2021/06/binary-search-tree-insertion-800x467.png
:align: center
```
$Search\ for\ \ 8$
````
`````
```` {admonition} visualize
:class: dropdown seealso
<iframe src="https://opendsa-server.cs.vt.edu/embed/BSTsearchCON" height="600" width="100%"></iframe>
````
```` {admonition} try it
:class: dropdown caution
<iframe src="https://opendsa-server.cs.vt.edu/embed/BSTsearchPRO" height="950" width="100%" scrolling="no"></iframe>
````
``````
```````

### [`insert`](https://www.geeksforgeeks.org/height-complete-binary-tree-heap-n-nodes/)

`````` {div} full-width
````` {card}
```` {grid}
``` {grid-item-card}
To insert a new value into a BST:
- Start at the root node.
- If the value is smaller, go to the left subtree; if larger, go to the right subtree.
- Repeat steps 2 until an empty spot is found.
- Insert the new node in the empty spot.
```
``` {grid-item-card}
![](https://blog.penjee.com/wp-content/uploads/2015/11/binary-search-tree-insertion-animation.gif)
```
````
```` {admonition} visualize
:class: dropdown seealso
<iframe src="https://opendsa-server.cs.vt.edu/embed/BSTinsertCON" height="600" width="100%"></iframe>
````
```` {admonition} try it
:class: dropdown caution
<iframe src="https://opendsa-server.cs.vt.edu/embed/BSTinsertPRO" height="950" width="100%" scrolling="no"></iframe>
````
`````
``````

### `remove`

`````` {div} full-width
````` {card} 

To delete a node from a BST:
- Find the node to delete.
- If the node has **no children**, simply remove it.
- If the node has **one child**, replace it with its child.
- If the node has **two children**, find the node's successor (smallest value in the right subtree) or predecessor (largest value in the left subtree).
- Replace the node with its successor/predecessor and delete the successor/predecessor from its original position.

```` {tab-set} 
``` {tab-item} leaf
![remove : leaf](https://mycloudology.com/algorithm-binary-tree-search/algorithm-binary-tree-search_4.JPG)
```
``` {tab-item} 1 child
![$remove:\ with\ 1\ child$](https://mycloudology.com/algorithm-binary-tree-search/algorithm-binary-tree-search_5.JPG)
```
``` {tab-item} 2 children
![$remove:\ with\ 2\ children$](https://mycloudology.com/algorithm-binary-tree-search/algorithm-binary-tree-search_6.JPG)
```
````
```` {admonition} visualize
:class: dropdown seealso
<iframe src="https://opendsa-server.cs.vt.edu/embed/BSTremoveCON" height="600" width="100%"></iframe>
````
```` {admonition} try it
:class: dropdown caution
<iframe src="https://opendsa-server.cs.vt.edu/embed/BSTremovePRO" height="950" width="100%" scrolling="no"></iframe>
````
`````
``````

### [Traversals](https://www.geeksforgeeks.org/binary-search-tree-traversal-inorder-preorder-post-order/)

### Implications

`````````` {div} full-width
````````` {card}

> Traversal of a tree `T` is a systematic way of accessing, or “visiting,” all the positions of `T` . The specific action associated with the “visit” of a position `p` depends on the application of this traversal, and could involve anything from incrementing a counter to performing some complex computation for `p`.

``` {figure} https://www.bogotobogo.com/GoLang/images/BinarySearchTree_BST/print_functions.png
```

```````` {tab-set} 

``````` {tab-item} preorder
`````` {grid}
````` {grid-item}
:columns: 5
``` {code-block} cpp
// nodes of the BST are visited in a
// pre-defined order before visiting
// their child nodes.

algorithm preorder (p) {
  if (p) {
    visit(p)
    preorder(p -> left)
    preorder(p -> right)
  }
}
```
`````
````` {grid-item}
:columns: 7
``` {figure} https://sbme-tutorials.github.io/2020/data-structure-FALL/images/Tree06.png

[preorder](https://sbme-tutorials.github.io/2020/data-structure-FALL/notes/week08.html#preorder-traversals)
```
`````
``````
```` {admonition} animation
:class: dropdown tip
``` {figure} https://miro.medium.com/v2/resize:fit:1000/1*UGoV21qO6N8JED-ozsbXWw.gif
```
````
```` {admonition} try it
:class: dropdown caution
<iframe src="https://opendsa-server.cs.vt.edu/embed/GenTreePreTravCON" height="600" width="100%"></iframe>
````
```````

``````` {tab-item} postorder
````` {grid}
```` {grid-item} 
:columns: 5
``` {code-block} cpp
// nodes of the BST are visited in a 
// pre-defined order after visiting 
// their child nodes.

algorithm postorder (p) {
  if (p) {
    postorder(p -> left)
    postorder(p -> right)
    visit(p)
  }
}
```
````
```` {grid-item}
:columns: 7

``` {figure} https://sbme-tutorials.github.io/2020/data-structure-FALL/images/Tree07.png
[postorder](https://sbme-tutorials.github.io/2020/data-structure-FALL/notes/week08.html#postorder-traversals)
```
````
`````
```` {admonition} animation
:class: dropdown tip
``` {figure} https://miro.medium.com/v2/resize:fit:1000/1*UGrzA4qtLCaaCiNAKZyj_w.gif
```
````
```` {admonition} try it
:class: dropdown caution
<iframe src="https://opendsa-server.cs.vt.edu/embed/GenTreePostTravCON" height="600" width="100%"></iframe>
````
```````

``````` {tab-item} inorder
````` {grid}
```` {grid-item}
:columns: 5
``` {code-block} cpp
// nodes of the BST are visited in
// ascending order of their values.

algorithm inorder (p) {
  if (p) {
    inorder(p -> left)
    visit(p)
    inorder(p -> right)
  }
}
```
````
```` {grid-item}
:columns: 7
``` {figure} https://sbme-tutorials.github.io/2020/data-structure-FALL/images/Tree08.png
[inorder](https://sbme-tutorials.github.io/2020/data-structure-FALL/notes/week08.html#inorder-traversals)
````
`````
```` {admonition} animation
:class: dropdown tip
``` {figure} https://miro.medium.com/v2/resize:fit:1000/1*bxQlukgMC9cGv_MFUllX2Q.gif
```
````
```````
````````
`````` {card}
How would we:

````` {admonition} Destroy a binary tree
:class: dropdown danger

**Post Order**

``` {figure} https://miro.medium.com/v2/resize:fit:1000/1*UGrzA4qtLCaaCiNAKZyj_w.gif
<br>Post Order
```
Why?
: It's the only traversal that visits all the subtree nodes before visiting the root. All child nodes must be removed before we can delete the root.

`````

````` {admonition} Print all elements ascending order
:class: dropdown danger

**In Order**

``` {figure} https://miro.medium.com/v2/resize:fit:1000/1*bxQlukgMC9cGv_MFUllX2Q.gif
```

Why?
: to output in ascending order, we would need to start with the lowest value sequentially and work our way to the largest; as BST's are built in sequential order, $in-order$ fits best 
`````
``````
`````````
``````````

``````` {div} full-width
`````` {card}
````` {tab-set}
```` {tab-item} incomplete
``` {list-table}
:header-rows: 1

* - 
  - best-case
  - worst-case
  - average-case
* - search
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
* - insert
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
* - remove
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
```
$$Cost\ of\ basic\ operations??$$
````

```` {tab-item} complete
``` {list-table}
:header-rows: 1

* - 
  - best-case
  - worst-case
  - average-case
* - search
  - $O(1)$
  - $O(n)$
  - $O(log\ n)$
* - insert
  - $O(1)$
  - $O(n)$
  - $O(log\ n)$
* - remove
  - $O(log\ n)$
  - $O(n)$
  - $O(log\ n)$
```
$$Cost\ of\ basic\ operations??$$
````
`````
``````
```````

### Average-case analysis

``````` {div} full-width
````` {card}
If **$n$** **distinct keys** are inserted into a BST in random  order, expected number of compares for basic  operations is

$$\ \sim2\ ln\ n \approx 1.39\ log\ n\ $$  

- proof: 1-1 correspondence with quick-sort

``` {figure} https://mycloudology.com/algorithm-binary-tree-search/algorithm-binary-tree-search_10.JPG
```
<!-- ![](imgs/15_s32.png) -->

$$ \ \ h = O(log\ n) \ \ $$

```` {admonition} inserting n keys in a random order
:class: dropdown tip

$n = 255$

``` {figure} https://algs4.cs.princeton.edu/32bst/media/bst-255random.mov

[https://algs4.cs.princeton.edu/32bst/](https://algs4.cs.princeton.edu/32bst/)
```
````
`````
```````

## Collections / Dictionaries


````` {div} full-width
```` {card}
``` {list-table}
:header-rows: 1

* - 
  - What?
  - Sequential (unordered)
  - Sequential (ordered)
  - BST
* - search
  - search for a key
  - $O(n)$
  - $O(log\ n)$
  - $O(h)$
* - insert
  - insert a key
  - $O(n)$
  - $O(n)$
  - $O(h)$
* - delete
  - delete a key
  - $O(n)$
  - $O(n)$
  - $O(h)$
* - min/max
  - smallest/largest key
  - $O(n)$
  - $O(1)$
  - $O(h)$
* - floor/ceiling
  - predecessor / successor
  - $O(n)$
  - $O(log\ n)$
  - $O(h)$
* - rank
  - \# of keys less than key
  - $O(n)$
  - $O(log\ n)$
  - $O(h)$**
```
````
`````

(**) requires the use of ‘size’ at every node
