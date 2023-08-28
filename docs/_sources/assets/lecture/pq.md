# Priority Queues

``````````` {div} full-width
``````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/wptevk0bshY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
A priority queue is an abstract data type in computer science that stores a collection of elements with associated priorities, and provides operations for adding and removing elements in a way that respects their priorities.

A priority queue is similar to a queue data structure, but unlike a queue, the order in which elements are removed from a priority queue is based on their priority rather than their order of insertion. In other words, the element with the highest priority is removed first, regardless of when it was added to the priority queue.

Priority queues are commonly used in applications where tasks or events have different levels of importance, such as task scheduling, event-driven simulations, and network routing protocols.

Priority queues can be implemented using various data structures, such as arrays, linked lists, heaps, and binary search trees. However, heap-based implementations are the most common, as they provide efficient $O(log\ n)$ time complexity for both insertion and removal operations, making them suitable for large collections.
```

``` {card} Additional Resources
- [Priority Queues | davefeinberg](https://youtu.be/5HC6qrWGrpA)
- [Priority Queues 2 | davefeinberg](https://youtu.be/2iSJJSci5u4)
- [Priority Queues 3 | davefeinberg](https://youtu.be/fFbtftih_eY)
- [Priority Queues 4 | davefeinberg](https://youtu.be/ujbhsL1Ngg8)
```
```````
```````````

## Definitions

``````````` {div} full-width
```` {card}

``` {card}
Collections
: Insert and delete items. Which items to delete?
```

``` {card}
Stack
: Remove the item most recently added

Queue
: Remove the item least recently added

Randomized Queue
: Remove a random item

Generalizes
: stack, queue, randomized queue
```

``` {card}
Priority Queue
: Remove the largest (or smallest) item
```

````
```````````

## [Queues](https://www.geeksforgeeks.org/queue-data-structure/?ref=gcse)

``````````` {div} full-width
```` {card}
``` {image} https://miro.medium.com/max/3148/0*TRbfsq86lqDoqW6b.png
```
````
```````````

## [Priority Queue](https://www.geeksforgeeks.org/priority-queue-set-1-introduction/)

``````````` {div} full-width
```` {card}
``` {image} https://netmatze.files.wordpress.com/2014/08/priorityqueue.png
```
````
```````````

## [Applications](https://www.geeksforgeeks.org/applications-of-queue-data-structure/)

`````` {div} full-width
````` {grid}
:padding: 2 2 2 2
```` {grid-item-card} Data compression in Huffman code
:columns: 4
``` {image} https://forum.nwoods.com/uploads/db3963/optimized/2X/a/aee3daf4aaa56da16df5f083c5c6f5a3c8324eb8_2_1024x749.png
:width: 100%
```
````
```` {grid-item-card} Network Routing
:columns: 4
``` {image} https://cdncontribute.geeksforgeeks.org/wp-content/uploads/DVP1.jpg
:width: 100%
```
````
```` {grid-item-card} CPU Scheduling
:columns: 4
``` {image} https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https:%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F2110D84751C24CE41C
:width: 100%
```
````
```` {grid-item-card} Other examples...
:columns: 12
- Artificial Intelligence (search)
- Graph Algorithms
- Stream Data Algorithms
- HPC Task Scheduling
- Graph algorithms like [Dijkstra’s shortest path algorithm](https://www.geeksforgeeks.org/greedy-algorithms-set-7-dijkstras-algorithm-for-adjacency-list-representation/), [Prim’s Minimum Spanning Tree](https://www.geeksforgeeks.org/greedy-algorithms-set-5-prims-mst-for-adjacency-list-representation/), etc.
- Stack Implementation
- All queue applications where priority is involved.
- Event-driven simulation such as customers waiting in a queue.
- Finding Kth largest/smallest element.
````
`````
``````

### Priority Queues

````` {div} full-width
```` {card}
**Collections of $<key, value>$ pairs**
- *_keys_* are objects on which an *_order_* is defined

Every pair of keys must be comparable according to a *_total order_*:
````
`````

`````` {div} full-width
````` {card} Properties
```` {grid}
``` {grid-item-card} Reflexive
$$k_1 \le k_2$$
```
``` {grid-item-card} Antisymmetric
$$k_1 \le\ k_2 \ \ \ \land \ \ \ k_2 \le k_1$$
$$\Rightarrow$$
$$k_1 = k_2$$
```
``` {grid-item-card} Transitive
$$k_1 \le k_2 \ \ \ \land \ \ \ k_2 \le k_3$$
$$\Rightarrow$$
$$k_1 \le k_3$$
```
````
`````
``````

`````` {div} full-width
````` {grid}
```` {grid-item-card} Queues
:columns: 6
- basic operations: 
  - *_$enqueue$_*, *_$dequeue$_*
- always remove the item least recently added
````
```` {grid-item-card} Priority Queues
:columns: 6
- basic operations: 
  - *_$insert$_*, *_$removeMax$_*
- MaxPQ: 
  - always remove the item with the highest (max) priority
- MinPQ: 
  - always remove the item with the lowest (min) priority
````
```` {grid-item-card}
:columns: 12
``` {image} https://studyalgorithms.com/wp-content/uploads/2013/12/priority_queue.png
:align: center
```
````
`````
``````

`````` {div} full-width
``` {figure} https://media.geeksforgeeks.org/wp-content/cdn-uploads/Priority-Queue-min-1024x512.png
:width: 100%
Working with PQ's
```
``````


### Performance

``````````` {div} full-width
```` {card}
``` {list-table}
:header-rows: 1

* -
  - Sorted Array/List
  - Unsorted Array/List
* - insert
  - $O(n)$<br><br>must find place where to insert item
  - $O(1)$<br><br>item can be inserted at head or tail
* - removeMax<br>max
  - $O(1)$<br><br>largest/smallest key is at:<br> $arr[0]$/$arr[n-1]$
  - $O(n)$<br><br>must traverse entire sequence to find largest/smallest
```
````
```````````

### cppreference.com

`````` {div} full-width

<iframe src="https://en.cppreference.com/w/cpp/container/priority_queue" frameborder="0" width="100%" height="800"></iframe>

``````

### Implementations

`````````` {div} full-width
`````````  {card}

```````    {list-table}
:header-rows: 0

* - [Arrays](https://www.geeksforgeeks.org/priority-queue-using-array-in-c/)
  - `enqueue` <br> $O(1)$
  - `dequeue` <br> $O(n)$
  - `peek` <br> $O(n)$
* - [Linked List](https://www.geeksforgeeks.org/priority-queue-using-linked-list/)
  - `push` <br> $O(n)$
  - `pop` <br> $O(1)$
  - `peek` <br> $O(1)$
* - [Binary Heap](https://www.geeksforgeeks.org/priority-queue-using-binary-heap/)
  - `insert` <br> $O(log\ n)$
  - `remove` <br> $O(log\ n)$
  - `peek` <br> $O(1)$
* - [Binary Tree]()
  - `insert` <br> $O(log\ n)$
  - `delete` <br> $O(log\ n)$
  - `peek` <br> $O(1)$

```````

*Note: assume all collections are unsorted...*

`````````
``````````

### Advantages & Disadvantages

`````````` {div} full-width
`````````  {card}

```````` {grid}
```````  {grid-item-card} Advantages

``` {dropdown} Faster elemental access
This is because elements in a priority queue are ordered by priority, one can easily retrieve the highest priority element without having to search through the entire queue.
```
``` {dropdown} Dynamic ordering 
Elements in a priority queue can have their priority values updated, which allows the queue to dynamically reorder itself as priorities change.
```
``` {dropdown} Efficient algorithms can be implemented
Priority queues are used in many algorithms to improve their efficiency, such as Dijkstra’s algorithm for finding the shortest path in a graph and the A* search algorithm for pathfinding.
```
``` {dropdown} Included in real-time systems
This is because priority queues allow you to quickly retrieve the highest priority element, they are often used in real-time systems where time is of the essence.
```
```````
```````  {grid-item-card} Disadvantage

``` {dropdown} High complexity  
Priority queues are more complex than simple data structures like arrays and linked lists, and may be more difficult to implement and maintain.  
```
``` {dropdown} High consumption of memory  
Storing the priority value for each element in a priority queue can take up additional memory, which may be a concern in systems with limited resources.  
```
``` {dropdown} Not always the most efficient data structure  
In some cases, other data structures like heaps or binary search trees may be more efficient for certain operations, such as finding the minimum or maximum element in the queue.  
```
``` {dropdown} Less predictable at times  
This is because the order of elements in a priority queue is determined by their priority values, the order in which elements are retrieved may be less predictable than with other data structures like stacks or queues, which follow a first-in, first-out (FIFO) or last-in, first-out (LIFO) order.
```
```````
````````

`````````
``````````