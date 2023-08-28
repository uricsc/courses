## Heaps

``````` {div} full-width

````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/0wPlzMU-k00" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
A heap is a specialized tree-based data structure in computer science that is used to maintain a collection of elements with a specific ordering property. A heap is usually implemented as a binary tree, where each node has at most two children, and it satisfies the heap property.

The heap property ensures that the root node has either the minimum or maximum value among all the nodes in the heap, depending on whether it is a min-heap or max-heap. In a min-heap, the value of each node is greater than or equal to the value of its parent, while in a max-heap, the value of each node is less than or equal to the value of its parent.

Heaps are commonly used in algorithms that require efficient access to the maximum or minimum element in a collection, such as heap sort, priority queues, and graph algorithms like Dijkstra's algorithm for finding shortest paths. The advantage of using a heap data structure is that it allows these algorithms to access the minimum or maximum element in constant time, making them highly efficient.

In addition to binary heaps, there are other types of heaps, such as Fibonacci heaps, binomial heaps, and pairing heaps, each with its own advantages and disadvantages.
```
``` {card} Additional Resources
- [Data Structures: Heaps | HackerRank](https://youtu.be/t0Cq6tVNRBA)
- [Heaps in 6 minutes — Methods | Michael Sambol](https://youtu.be/pAU21g-jBiE)
- [Heap sort in 4 minutes | Michael Sambol](https://youtu.be/2DmK_H7IdTo)
```

`````

```````

### [(max) Heap](https://www.geeksforgeeks.org/difference-between-min-heap-and-max-heap/?ref=gcse)

``````````` {div} full-width
``` {card}
Structure Property
: a heap is a [*_complete binary tree_*](https://www.geeksforgeeks.org/complete-binary-tree/)

Heap-Order Property
: for every node $x$:
  - $key\ parent\ x\ \ge\ key \ x$
  - except the root, which has no parent
```

``` {image} https://media.geeksforgeeks.org/wp-content/uploads/20201106115254/MaxHeap.jpg
```
```````````

### [Height of a heap](https://www.geeksforgeeks.org/height-complete-binary-tree-heap-n-nodes/)

``````````` {div} full-width
```` {card}

What is the minimum number of nodes in a complete binary tree of height $h$?

``` {image} https://media.geeksforgeeks.org/wp-content/uploads/20201106115254/MaxHeap.jpg
```

$$n \ge 2^h\Rightarrow\ log\ n \ge log\ 2^h \Rightarrow\ log\ n \ge h$$
````
```````````

## Implementation

``````````` {div} full-width
``````` {card}
````` {grid}
```` {grid-item-card}
:columns: 12
``` {image} imgs/13_implement_2.png
```
````
```` {grid-item-card}
:columns: 12
``` {image} imgs/13_implement_1.png
```
````
``` {grid-item-card}
node(i)
: $$i$$
```
``` {grid-item-card}
parent(i)
: $$floor(\frac{i}{2})$$
```
``` {grid-item-card}
left_child(i)
: $$i * 2$$
```
``` {grid-item-card}
right_child(i)
: $$i * 2 + 1$$
```
`````
```````
```````````

````````` {div} full-width
```````` {grid}
``````` {grid-item-card}
$insert$

**Append new element to the end of array**

Check heap-order property
: if <b class="red">violated, *_Up-Heap_*</b> (swap with parent)
  : **repeat** until heap-order is restored
: if <b class="green">not</b>, $insert$ complete

Time Complexity
: $O(log\ n)$
```````
``````` {grid-item-card}
$removeMax$

Max element is the first element of the array
: the $root$ of the heap

Copy last element of array to the first position
: then decrement array size by 1 (removes the last element)

Check heap-order property
: if <b class="red">violated, _Down-Heap_</b> (swap with **larger** child)
  : **repeat** until heap-order is restored
: if <b class="green">not</b>, *_insert_* complete

Time Complexity
: $O(log\ n)$
```````
````````
`````````

``` {div} full-width
<iframe src="https://visualgo.net/en/heap" width="100%" height="800"></iframe>
```

## Performance

``````````` {div} full-width
```` {card}

``` {list-table}
:header-rows: 1

* - 
  - Sorted Array/List
  - Unsorted Array/List
  - Heap
* - insert
  - $O(n)$
  - $O(1)$
  - $O(log\ n)$
* - removeMax
  - $O(1)$
  - $O(n)$
  - $O(log\ n)$
* - max
  - $O(1)$
  - $O(n)$
  - $O(1)$
* - insert N
  - $O(n^2)$
  - $O(n)$
  - $O(n)^{**}$
```

(**) assuming we know the sequence in advance (*_buildHeap_*)

````
```````````
