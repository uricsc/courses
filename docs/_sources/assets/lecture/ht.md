# Hash Tables

````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/knV86FlSXJ8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
A hash table is a data structure that provides efficient insertion, deletion, and lookup operations on key-value pairs. It works by using a hash function to map each key to a position in an array, called the hash table, where the corresponding value is stored.

The hash function takes a key as input and generates a hash code, which is used to determine the position in the array where the value should be stored. Ideally, the hash function should distribute the keys uniformly across the hash table, to minimize collisions (i.e., when two or more keys map to the same position in the array).

To handle collisions, a hash table typically uses a collision resolution strategy, such as chaining or open addressing. Chaining involves storing all the values that hash to the same position in a linked list, while open addressing involves finding the next available position in the array to store the value.

One of the advantages of hash tables is their speed. In the average case, operations on a hash table have a constant-time complexity of $O(1)$, meaning that the time taken to perform an operation does not depend on the size of the hash table. This makes hash tables ideal for applications where fast lookup and insertion times are important.

Overall, hash tables are an important data structure in computer science, and are widely used in applications such as databases, compilers, and web servers. However, the efficiency of hash tables depends on the quality of the hash function used, and collisions can still occur, which can degrade performance.
```

``` {card} Additional Resources
- []()
```

`````
<!-- ```````` {image} https://i.pinimg.com/originals/23/de/a8/23dea88650c8401a13af985eddee6731.jpg
:align: center
```````` -->
`````````

<!-- ## Storing data

````````` {div} full-width
```````` {card} 

```` {figure} imgs/hash/18_00.png
:align: center
Summary Table
````

````````
````````` -->

## Overview

````````` {div} full-width
```````` {grid} 

```` {grid-item-card}
:columns: 5

``` {figure} https://miro.medium.com/v2/resize:fit:3328/1*88wdGX8QKZDrGPEFkFuYrw.jpeg
```

````
```` {grid-item-card} Definition
:columns: 7

> A hash table is a data structure that maps keys to values using a hash function.
``` {card} Efficiency functions
`insert`  
`delete`  
`get`
```

``` {card} a.k.a.
`hash maps`  
`associative arrays`  
`dictionaries`  
```
````


````````
`````````

## Hash Functions

````````` {div} full-width
````````  {grid}

`````` {grid-item-card}
:columns: 8

``` {card} Definition
> A hash function maps keys to indices of an array (or buckets).
```

````` {card} Properties

- Deterministic
: always produces the same output

- Uniform Distribution
: minimizes collisions by evenly distributing the keys across the table.

- Efficiency
: fast computation to ensure constant-time complexity.

`````
``````
`````` {grid-item-card}
:columns: 4

``` {figure} https://www.researchgate.net/profile/Michal-Turcanik/publication/310624366/figure/fig1/AS:515735291797504@1499972283541/Hash-algorithm-III-HASH-FUNCTION.png
```

``````


````````  
`````````

## Collision Resolution

````````````` {div} full-width
````````````  {card}

``` {admonition} Collision
:class: tip dropdown

> when two or more keys map to the same index
```

````````  {grid}

`````` {grid-item-card}
:columns: 8

``` {card} Definition
> A hash function maps keys to indices of an array (or buckets).
```

````` {card} Properties

- Deterministic
: always produces the same output

- Uniform Distribution
: minimizes collisions by evenly distributing the keys across the table.

- Efficiency
: fast computation to ensure constant-time complexity.

`````
``````
`````` {grid-item-card}
:columns: 4

``` {figure} https://www.researchgate.net/profile/Michal-Turcanik/publication/310624366/figure/fig1/AS:515735291797504@1499972283541/Hash-algorithm-III-HASH-FUNCTION.png
```

``````


```````````` 
`````````````

