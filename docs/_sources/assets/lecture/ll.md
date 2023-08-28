# Linked Lists

```````````` {div} full-width

```` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/F8AbOfQwl1c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
A linked list is a data structure in computer science that consists of a sequence of nodes, where each node contains data and a reference (or pointer) to the next node in the sequence.

Unlike arrays, where the elements are stored in contiguous memory locations, the nodes in a linked list can be scattered throughout the memory. This makes linked lists more flexible than arrays, as they can be easily modified by adding, removing or rearranging the nodes.

Linked lists come in different types, such as singly linked lists, doubly linked lists, and circular linked lists. In a singly linked list, each node has a reference to only the next node in the sequence. In a doubly linked list, each node has references to both the previous and the next nodes in the sequence. In a circular linked list, the last node in the sequence has a reference to the first node, thus forming a circular chain.

Linked lists are commonly used in programming for various purposes, such as implementing dynamic data structures, like stacks, queues, and hash tables, and for managing memory allocation and deallocation in operating systems. However, linked lists can be less efficient than arrays for certain operations, such as random access and searching, as they require traversing the list sequentially from the beginning.
```
``` {card} Additional Resources
- [Data Structures: Linked Lists | HackerRank](https://youtu.be/njTh_OwMljA)
```
````

````````````

## Background

`````````` {div} full-width
````` {card}

```` {admonition} 🐍 Timing Sample
:class: tip

```python
import time

n =- 100000

start  = time.time()
array = []
for i in range(n):
  array.append('s')
print(time.time() - start)

start  = time.time()
array = []
for i in range(n):
  array = array + ['s']
print(time.time() - start)
```

````

```` {admonition} How are lists implemented in CPython

CPython’s lists are really variable-length arrays, not Lisp-style linked lists. The implementation uses a contiguous array of references to other objects, and keeps a pointer to this array and the array’s length in a list head structure.

This makes indexing a list $a[i]$ an operation whose cost is independent of the size of the list or the value of the index.

When items are appended or inserted, the array of references is resized. Some cleverness is applied to improve the performance of appending items repeatedly; when the array must be grown, some extra space is allocated so the next few times don’t require an actual resize.

<i><b>CPython</b> is the reference implementation of the Python programming language</i>
````

`````
``````````

## Some STL Containers


`````````` {div} full-width

```` {card}
``` {glossary}
Sequence Containers
  Maintain the ordering of inserted elements that you specify.
```
````

`````````  {card}

````````   {tab-set}
```````    {tab-item} Containers
Arrays, vectors, forward lists, and lists are all data structures used in computer science and programming to store collections of data. Each of these data structures has its own strengths and weaknesses, and understanding the differences between them can help you choose the best one for your particular application.

``` {glossary}
Array
  a data structure that stores a fixed-size sequential collection of elements of the same type. The elements of an array are stored in contiguous memory locations, making it easy to access them using an index. Arrays are efficient when you know the size of the data in advance, and you need to access the elements randomly.

Vector
  a dynamic array that can grow or shrink as needed. It is similar to an array, but it can change its size dynamically during runtime. The elements of a vector are stored in contiguous memory locations, making it easy to access them using an index. Vectors are useful when you don't know the size of the data in advance, or when you need to insert or delete elements from the middle of the collection.

Forward List
  a singly linked list that stores a sequence of elements. Each element in a forward list contains a pointer to the next element in the list, but not to the previous one. This means that you can only traverse a forward list in one direction. Forward lists are useful when you need to insert or delete elements from the beginning or middle of the collection, but not the end.
  
List
  a doubly linked list that stores a sequence of elements. Each element in a list contains a pointer to the next and previous elements in the list, allowing you to traverse the list in both directions. Lists are useful when you need to insert or delete elements from any position in the collection, or when you need to maintain a sorted collection.
```

In summary, arrays and vectors are best for situations where you need random access to elements and the size of the collection is known in advance. Forward lists and lists are better for situations where you need to insert or delete elements from the beginning, middle, or end of the collection, or when you need to maintain a sorted collection.
```````
```````    {tab-item} Array Allocation
``````     {grid}
`````     {grid-item-card}
:columns: 6

**Stack Allocation**

When an array is declared as a local variable inside a function without using the new operator, the memory for the array is allocated on the stack. The size of the array must be known at compile-time. Here's an example:

``` {code-block} cpp
void foo() {
    int myArray[10]; // allocate 10 integers on the stack
    // ...
}
```

Stack allocation is fast and efficient, but the size of the array is limited by the available stack space, which is typically smaller than the heap.
`````
`````     {grid-item-card}
:columns: 6

**Heap Allocation**

When an array is declared using the new operator, the memory for the array is allocated on the heap. The size of the array can be determined at runtime. Here's an example:

``` {code-block} cpp
void bar() {
    int* myArray = new int[10]; // allocate 10 integers on the heap
    // ...
    delete[] myArray; // free the memory when done
}
```

Heap allocation is more flexible than stack allocation, but it's slower and more prone to memory leaks if the programmer forgets to free the memory when done.

It's important to note that C++ also provides a number of container classes, such as `std::vector`, `std::list`, and `std::array`, which provide more advanced memory management capabilities than plain C-style arrays.
`````
```````
```````    {tab-item} Array Functions
```` {admonition} [array](https://en.cppreference.com/w/cpp/container/array)

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

#include <iostream>
#include <array>
#include <algorithm>

int main() {
    // Declare an array with initial values
    std::array<int, 5> arr = {1, 2, 3, 4, 5};

    // Access an element by index
    std::cout << arr[0] << std::endl; // prints 1

    // Modify an element by index
    arr[0] = 10; // arr is now {10, 2, 3, 4, 5}

    // Get the length of the array
    std::cout << arr.size() << std::endl; // prints 5

    // Add an element to the end of the array
    arr.fill(0);
    arr.back() = 6; // arr is now {0, 0, 0, 0, 6}

    // Remove and return the last element of the array
    int last_element = arr.back();
    arr.back() = 0; // arr is now {0, 0, 0, 0, 0}

    // Add an element to the beginning of the array
    arr.fill(0);
    for (int i = arr.size()-1; i > 0; i--) {
        arr[i] = arr[i-1];
    }
    arr[0] = 0; // arr is now {0, 0, 0, 0, 0}

    // Remove and return the first element of the array
    int first_element = arr.front();
    for (int i = 0; i < arr.size()-1; i++) {
        arr[i] = arr[i+1];
    }
    arr.back() = 0; // arr is now {0, 0, 0, 0, 0}

    // Find the index of a given element in the array
    int index = std::distance(arr.begin(), std::find(arr.begin(), arr.end(), 4));

    // Sort the array in ascending order
    std::sort(arr.begin(), arr.end());

    // Reverse the order of the elements in the array
    std::reverse(arr.begin(), arr.end());

    // Concatenate two arrays into a new array
    std::array<int, 3> arr2 = {6, 7, 8};
    std::array<int, 8> concatenated;
    std::copy(arr.begin(), arr.end(), concatenated.begin());
    std::copy(arr2.begin(), arr2.end(), concatenated.begin()+arr.size());

    // Slice a portion of the array into a new array
    std::array<int, 2> slice;
    std::copy(arr.begin()+1, arr.begin()+3, slice.begin());

    // Iterate over the elements of the array
    for (auto i : arr) {
        std::cout << i << std::endl;
    }

    return 0;
}

```

[link: cppreference](https://en.cppreference.com/w/cpp/container/array)
````
```````
```````    {tab-item} Vector Allocation
``````     {grid}
`````     {grid-item-card}
:columns: 6

In C++, `std::vector` is a dynamic container that is implemented as a wrapper around a dynamically-allocated array. The memory for a std::vector is allocated on the heap, and it grows or shrinks dynamically as elements are added or removed.

When a `std::vector` is created, it allocates a block of memory on the heap to hold the elements of the vector. The size of this block of memory is determined by the vector's capacity, which is the maximum number of elements that the vector can hold without allocating more memory. By default, a vector's capacity is 0, and it grows dynamically as elements are added.

When a `std::vector` is resized (by calling `resize()` or by inserting or erasing elements), it may need to allocate more memory on the heap. To avoid reallocating memory too often, which can be expensive, a `std::vector` typically over-allocates by reserving more memory than it needs. The amount of over-allocation is implementation-dependent, but it is usually at least enough to double the capacity of the vector.
`````
`````     {grid-item-card}
:columns: 6

Here's an example of creating and using a `std::vector`:

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

#include <vector>
#include <iostream>

int main() {
    std::vector<int> v; // create an empty vector
    v.reserve(10); // reserve space for 10 integers (but size is still 0)

    // add some elements to the vector
    for (int i = 0; i < 5; i++) {
        v.push_back(i); // append an element to the vector
    }

    // iterate over the elements of the vector
    for (auto it = v.begin(); it != v.end(); ++it) {
        std::cout << *it << std::endl;
    }

    return 0;
}

```

In this example,
- the `std::vector` is created with a default capacity of 0
- `reserve()` is called to allocate space for 10 integers on the heap
- `push_back()` is called to add elements to the vector
  - the vector grows dynamically as needed
- elements of the vector are iterated over using a forward iterator
`````
```````

```````    {tab-item} Vector Functions
```` {admonition} [vector](https://en.cppreference.com/w/cpp/container/vector)

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    // Declare a vector with initial values
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // Access an element by index
    std::cout << vec[0] << std::endl; // prints 1

    // Modify an element by index
    vec[0] = 10; // vec is now {10, 2, 3, 4, 5}

    // Get the length of the vector
    std::cout << vec.size() << std::endl; // prints 5

    // Add an element to the end of the vector
    vec.push_back(6); // vec is now {10, 2, 3, 4, 5, 6}

    // Remove and return the last element of the vector
    int last_element = vec.back();
    vec.pop_back(); // vec is now {10, 2, 3, 4, 5}

    // Add an element to the beginning of the vector
    vec.insert(vec.begin(), 0); // vec is now {0, 10, 2, 3, 4, 5}

    // Remove and return the first element of the vector
    int first_element = vec.front();
    vec.erase(vec.begin()); // vec is now {10, 2, 3, 4, 5}

    // Find the index of a given element in the vector
    auto itr = std::find(vec.begin(), vec.end(), 4);
    int index = std::distance(vec.begin(), itr);

    // Sort the vector in ascending order
    std::sort(vec.begin(), vec.end());

    // Reverse the order of the elements in the vector
    std::reverse(vec.begin(), vec.end());

    // Concatenate two vectors into a new vector
    std::vector<int> vec2 = {6, 7, 8};
    std::vector<int> concatenated;
    concatenated.reserve(vec.size() + vec2.size());
    concatenated.insert(concatenated.end(), vec.begin(), vec.end());
    concatenated.insert(concatenated.end(), vec2.begin(), vec2.end());

    // Slice a portion of the vector into a new vector
    std::vector<int> slice(vec.begin()+1, vec.begin()+3);

    // Iterate over the elements of the vector
    for (auto i : vec) {
        std::cout << i << std::endl;
    }

    return 0;
}
```

[link: cppreference](https://en.cppreference.com/w/cpp/container/vector)
````
```````

```````    {tab-item} Forward-list Allocation
``````     {grid}
`````     {grid-item-card}
:columns: 6

In C++, `std::forward_list` is a dynamic container that is implemented as a singly linked list. Each element in the list is stored in a separate node on the heap, and each node contains a pointer to the next node in the list.

When a `std::forward_list` is created, it allocates memory on the heap to hold the first node of the list. Each subsequent node is allocated as needed when elements are added to the list. When an element is added to the list, a new node is allocated on the heap to hold the element, and the new node's pointer is inserted into the list by updating the pointers of the existing nodes.
`````
`````     {grid-item-card}
:columns: 6

Here's an example of creating and using a `std::forward_list`:

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

#include <forward_list>
#include <iostream>

int main() {
    std::forward_list<int> flist; // create an empty forward list

    // add some elements to the list
    for (int i = 0; i < 5; i++) {
        flist.push_front(i); // insert an element at the beginning of the list
    }

    // iterate over the elements of the list
    for (auto it = flist.begin(); it != flist.end(); ++it) {
        std::cout << *it << std::endl;
    }

    return 0;
}

```

In this example, 

- `std::forward_list` is created with no elements
- `push_front()` is called to insert elements at the beginning of the list
- element is stored in a new node on the heap
  - the pointers of the existing nodes are updated to insert the new node into the list
- elements of the list are iterated over using a forward iterator

Because `std::forward_list` is implemented as a singly linked list, it has some advantages over other containers in terms of memory usage and performance for certain operations. However, it also has some limitations, such as the inability to access elements by index and the inability to iterate in reverse.

`````
```````

```````    {tab-item} Forward-list Functions
```` {admonition} [forward-list](https://en.cppreference.com/w/cpp/container/forward_list)

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

#include <iostream>
#include <forward_list>

int main() {
    // Declare a forward list with initial values
    std::forward_list<int> flist = {1, 2, 3, 4, 5};

    // Access the first element of the list
    std::cout << flist.front() << std::endl; // prints 1

    // Modify the first element of the list
    flist.front() = 10; // flist is now {10, 2, 3, 4, 5}

    // Add an element to the beginning of the list
    flist.push_front(0); // flist is now {0, 10, 2, 3, 4, 5}

    // Remove the first element of the list
    flist.pop_front(); // flist is now {10, 2, 3, 4, 5}

    // Insert an element after a given position in the list
    auto pos = flist.begin();
    std::advance(pos, 2);
    flist.insert_after(pos, 6); // flist is now {10, 2, 6, 3, 4, 5}

    // Remove an element after a given position in the list
    pos = flist.begin();
    std::advance(pos, 3);
    flist.erase_after(pos); // flist is now {10, 2, 6, 4, 5}

    // Find the position of a given element in the list
    pos = std::find(flist.begin(), flist.end(), 4);

    // Iterate over the elements of the list
    for (auto i : flist) {
        std::cout << i << std::endl;
    }

    return 0;
}

```

[link: cppreference](https://en.cppreference.com/w/cpp/container/forward_list)
````
```````
```````    {tab-item} List Allocation
``````     {grid}
`````     {grid-item-card}
:columns: 6

In C++, `std::list` is a dynamic container that is implemented as a doubly linked list. Each element in the list is stored in a separate node on the heap, and each node contains pointers to the previous and next nodes in the list.

When a `std::list` is created, it allocates memory on the heap to hold the first node of the list. Each subsequent node is allocated as needed when elements are added to the list. When an element is added to the list, a new node is allocated on the heap to hold the element, and the new node's pointers are inserted into the list by updating the pointers of the existing nodes.
`````
`````     {grid-item-card}
:columns: 6

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

#include <list>
#include <iostream>

int main() {
    std::list<int> l; // create an empty list

    // add some elements to the list
    for (int i = 0; i < 5; i++) {
        l.push_back(i); // insert an element at the end of the list
    }

    // iterate over the elements of the list
    for (auto it = l.begin(); it != l.end(); ++it) {
        std::cout << *it << std::endl;
    }

    return 0;
}

```

In this example, 

- `std::list` is created with no elements
- `push_back()` is called to insert elements at the end of the list
- element is stored in a new node on the heap
  - the pointers of the existing nodes are updated to insert the new node into the list
- elements of the list are iterated over using a bidirectional iterator.

Because `std::list` is implemented as a doubly linked list, it has some advantages over other containers in terms of flexibility and performance for certain operations. However, it also has some disadvantages, such as higher memory overhead due to the need for extra pointers and slower performance for accessing elements by index.

`````
```````
```````    {tab-item} List Functions
```` {admonition} [list](https://en.cppreference.com/w/cpp/container/list)

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

#include <iostream>
#include <list>

int main() {
    // Declare a list with initial values
    std::list<int> mylist = {1, 2, 3, 4, 5};

    // Access an element by iterator
    std::list<int>::iterator it = mylist.begin();
    std::advance(it, 2);
    std::cout << *it << std::endl; // prints 3

    // Modify an element by iterator
    *it = 10; // mylist is now {1, 2, 10, 4, 5}

    // Get the length of the list
    std::cout << mylist.size() << std::endl; // prints 5

    // Add an element to the end of the list
    mylist.push_back(6); // mylist is now {1, 2, 10, 4, 5, 6}

    // Remove the last element of the list
    mylist.pop_back(); // mylist is now {1, 2, 10, 4, 5}

    // Add an element to the beginning of the list
    mylist.push_front(0); // mylist is now {0, 1, 2, 10, 4, 5}

    // Remove the first element of the list
    mylist.pop_front(); // mylist is now {1, 2, 10, 4, 5}

    // Insert an element before a given position in the list
    it = mylist.begin();
    std::advance(it, 3);
    mylist.insert(it, 6); // mylist is now {1, 2, 10, 6, 4, 5}

    // Remove an element at a given position in the list
    it = mylist.begin();
    std::advance(it, 2);
    mylist.erase(it); // mylist is now {1, 2, 6, 4, 5}

    // Find the position of a given element in the list
    it = std::find(mylist.begin(), mylist.end(), 4);

    // Iterate over the elements of the list
    for (auto i : mylist) {
        std::cout << i << std::endl;
    }

    return 0;
}
```

[link: cppreference](https://en.cppreference.com/w/cpp/container/list)
````
```````
````````

`````````
``````````

## Linked Lists

### Arrays

`````````` {div} full-width
````` {card}

```` {card}
Think about making **insertions** and **deletions** efficiently...

``` {admonition} What is the computational cost of inserting or deleting 1 element?
:class: dropdown tip

In C++, arrays are fixed-size data structures, which means that the size of the array is determined at the time of declaration and cannot be changed afterwards. Therefore, inserting or deleting elements in an array requires shifting the existing elements to create or close gaps.

Here are the computational costs of inserting and deleting from the rear, front, and at an index of an array:

- Inserting or deleting from the **rear** of an array takes constant time $O(1)$
  - only requires updating the index of the last element in the array.

- Inserting or deleting from the **front** of an array takes linear time $O(n)$ where `n` is the number of elements in the array
  - requires shifting all existing elements by one position to make room for the new element or to close the gap left by the deleted element.

- Inserting or deleting at an arbitrary **index** of an array takes linear time $O(n)$, where `n` is the number of elements in the array
  - requires shifting all elements from the insertion or deletion index to the end of the array by one position to create or close gaps.

*Note that in addition to the computational costs, inserting or deleting from an array also incurs memory costs, as the size of the array may need to be adjusted to accommodate the new or deleted elements. Also, if the array is dynamically allocated, memory allocation and de-allocation costs may apply.*
```
- rear?
- front?
- index?

``` {figure} https://www.simplilearn.com/ice9/free_resources_article_thumb/Vaibhav-Arrays%20Article/Arrays_in_ds-what-is-array-img1.PNG
```

````

`````
``````````

### [Linked Lists](https://www.geeksforgeeks.org/data-structures/linked-list/)

`````````` {div} full-width
````` {card}
``` {admonition} Defined
Collections of sequential elements stored at <b class="orange">non-contiguous</b> locations in memory

Elements are stored in <b class="green">nodes</b>

Nodes are connected by <b class="green">links</b>

- every node keeps a pointer to the next node

Can **grow** and **shrink** dynamically

Allow for fast insertions/deletions
```
```` {admonition} Supported operations
**Linked lists are just *_collections_* of sequential data**

can `insert` 1 or more elements  
    - _front, end, by index, by value (sorted lists)_ 

can `delete` 1 or more elements  
    - <span class="green">_front, end, by index, by value_</span>  

can `search` for a specific element  

can `get` an element at a given index  

can `traverse` the list  
    - visit all nodes and perform an operation (e.g. print or destroy)
````
`````
``````````

## [Singly Linked List](https://www.geeksforgeeks.org/data-structures/linked-list/singly-linked-list/)

`````````` {div} full-width
````` {card}
```` {card}

``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20220816144425/LLdrawio.png
```

``` {note}
Node Left: **data**  
Node Right: **memory location of next element in LL**
```
````
`````
``````````

### Implementing a Singly Linked List


`````````` {div} full-width

````` {card} Linked lists in C++

```` {admonition} Prerequisites
:class: warning

- C++ Classes
- Pointers  
  - `NULL` pointers
- Dynamic Memory Allocation
  - `new`  
  - `delete`  
- Pointers and Classes
  - dot notation (`.`)  
  - arrow notation (`->`)

````

`````
``````````

### Creating a Linked List

`````````` {div} full-width
`````` {card}

````` {grid}

```` {grid-item-card} 
:columns: 6

class `Node`

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

class Node
{
    private:
        int data;
        Node *next;
        // private data/methods
        // ...

    public:
        Node (int d);
        ~Node();

        Friend class List;
};
```

````

```` {grid-item-card} 
:columns: 6

class `List`

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

class List
{
  private:
    Node *head;
    Node *tail;
    // private data/methods
    // ...

  public:
    List();
    ~List();
    // public methods
    // ...
};
```

````

[https://www.geeksforgeeks.org/what-is-linked-list/](https://www.geeksforgeeks.org/what-is-linked-list/)

`````

``````
``````````

### Linked List Operations

`````````` {div} full-width
`````````  {card}
````````   {tab-set}
```````    {tab-item} Insert@Head
``````     {grid}
`````      {grid-item-card} Algorithm of insertion at the beginning
:columns: 4

- Create a new node
- Assign its data value
- Assign newly created node’s next ptr to current head reference. So, it points to the previous start node of the linked list address
- Change the head reference to the new node’s address.
`````
`````      {grid-item-card}
:columns: 8

``` {figure} img/ll_ins_head.png
:width: 600
```

`````
``````
```````
```````    {tab-item} Insert@Tail
``````     {grid}
`````      {grid-item-card} To insert element in linked list last we would use the following steps to insert a new Node at the last of the doubly linked list.
:columns: 4

- Create a new node
- Assign its data value
- Assign its next node to NULL as this will be the last(tail) node
- Check if the list is empty
- Change the head node to the new node
- If not then traverse till the last node
- Assign the last node’s next pointer to this new node
- Now, the new node has become the last node.

`````
`````      {grid-item-card}
:columns: 8

``` {figure} img/ll_ins_tail.png
:width: 600
```

`````
``````
```````
```````    {tab-item} Insert@Nth
``````     {grid}
`````      {grid-item-card} Insertion at After nth position node
:columns: 4

- First we will create a new node named by newnode and put the position where u want to insert the node.
- Now give the address of the new node in previous node means link the new node with previous node.
- After this, give the address of current node in new node.Means link your new node also with current node.

`````
`````      {grid-item-card}
:columns: 8

``` {figure} img/ll_ins_nth.png
:width: 600
```

`````
``````
```````
```````    {tab-item} Delete@Tail
``````     {grid}
`````      {grid-item-card} Delete an element from end in singly linked list
:columns: 4

- Check if the Linked List is empty as we can not delete from an empty Linked List
- Check if the Linked List has only one Node
- In this case, just point the head to NULL and free memory for the existing node
- Otherwise, if the linked list has more than one node, traverse to the end of the Linked List
- Point next of 2nd Last node to NULL
- Free the memory for the last node.

`````
`````      {grid-item-card}
:columns: 8

``` {figure} img/ll_del_tail.png
:width: 600
```

`````
``````
```````
```````    {tab-item} Delete@Head
``````     {grid}
`````      {grid-item-card} Insertion at After nth position node
:columns: 4

- First we will create a new node named by newnode and put the position where u want to insert the node.
- Now give the address of the new node in previous node means link the new node with previous node.
- After this, give the address of current node in new node.Means link your new node also with current node.

`````
`````      {grid-item-card}
:columns: 8

``` {figure} img/ll_del_head.png
:width: 600
```

`````
``````
```````
```````    {tab-item} Delete@Nth
``````     {grid}
`````      {grid-item-card} Delete a Linked List node at a given position
:columns: 4

- Insert the initial items in the linked list
- Calculate the current size of the linked list
- Ask the user for nth position he wants to delete
- if(n < 1 || n > size) then say invalid
- If deleting the first node, just change the head to the next item in Linked List
- Else traverse to the nth node to delete
- Change the next of (n-1)th node to (n+1)th node
- Free the memory for th nth node

`````
`````      {grid-item-card}
:columns: 8

``` {figure} img/ll_del_nth.png
:width: 600
```

`````
``````
```````
````````
*Images: [Prepinsta](https://prepinsta.com/cpp-program/linked-list-insertion-and-deletion/)*
`````````
``````````

<!-- ### Pseudocode : Operations on Linked Lists 

``````` {div} full-width
`````` {card}
`````  {tab-set}
````   {tab-item} insert {@tail}
```    {image} https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/Linkedlist_insert_last.png
:width: 600
:align: center
```
```    {code-block}
InsertAtEnd(list, value)
    node = Node(value)
    if list.head is null
        list.head = node
        return
    current = list.head
    while current.next is not null
        current = current.next
    current.next = node
```
````
````  {tab-item} insert {@head}
``` {image} https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/Linkedlist_insert_at_start.png
:width: 600
:align: center
```
```    {code-block}
InsertAtBeginning(list, value)
    node = Node(value)
    node.next = list.head
    list.head = node
```
````
````  {tab-item} insert {@index}
``` {image} https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/Linkedlist_insert_middle.png
:width: 600
:align: center
```
``` {code-block}
InsertAtPosition(list, value, position)
    if position == 0
        InsertAtBeginning(list, value)
        return
    node = Node(value)
    current = list.head
    for i in 1 to position - 1
        if current is null
            return
        current = current.next
    node.next = current.next
    current.next = node
```
````
````  {tab-item} remove {@tail}
``` {image} https://static.javatpoint.com/ds/images/deleting-a-node-from-the-last.png
:width: 600
:align: center
```
```    {code-block}
DeleteAtEnd(list)
    if list.head is null
        return
    if list.head.next is null
        list.head = null
        return
    current = list.head
    while current.next.next is not null
        current = current.next
    current.next = null
```
````
````  {tab-item} remove {@head}
``` {image} https://iq.opengenus.org/content/images/2018/08/delete_first_ll.jpg
:width: 600
:align: center
```
```    {code-block}
DeleteAtBeginning(list)
    if list.head is null
        return
    list.head = list.head.next
```
````
````  {tab-item} remove {@index}
``` {image} https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2014/05/Linkedlist_deletion.png
:width: 600
:align: center
```
```    {code-block}
DeleteAtPosition(list, position)
    if list.head is null
        return
    if position == 0
        DeleteAtBeginning(list)
        return
    current = list.head
    for i in 1 to position - 1
        if current.next is null
            return
        current = current.next
    current.next = current.next.next
```
````
````  {tab-item} search {value found}
```    {code-block}
Search(list, value)
    current = list.head
    while current is not null
        if current.value == value
            return true
        current = current.next
    return false
```
````
````  {tab-item} traverse
```    {code-block}
Traverse(list)
    current = list.head
    while current is not null
        // do something with current.value
        current = current.next
```
````
````  {tab-item} size
```    {code-block}
GetSize(list)
    size = 0
    current = list.head
    while current is not null
        size = size + 1
        current = current.next
    return size

```
````
`````
For virtual walkthroughs : [https://visualgo.net/en/list](https://visualgo.net/en/list)
``````
``````` -->

## Linked Lists : Variations

`````````` {div} full-width
`````````  {card}
````````   {tab-set}
``````` {tab-item} Visualize
``` {figure} https://i1.faceprep.in/Companies-1/types-of-linked-list.png
```
```````
``````` {tab-item} Circular Singly Linked
[Circular Singly Linked List](https://www.geeksforgeeks.org/circular-singly-linked-list-insertion/)

```` {admonition} Pseudocode

``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20220817185024/CircularSinglyLinkedList.png
```

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

// Define a Node class to represent each node in the circular singly-linked list
class Node {
public:
    T data; // data stored in the node
    Node* next; // pointer to the next node in the list

    // constructor to initialize a new node with the given data and next pointer
    Node(T data, Node* next = nullptr) {
        this->data = data;
        this->next = next;
    }
};

// Define the CircularSinglyLinkedList class to represent the circular singly-linked list
class CircularSinglyLinkedList {
private:
    Node* tail; // pointer to the last node in the list

public:
    // constructor to initialize an empty list with a null tail pointer
    CircularSinglyLinkedList() {
        tail = nullptr;
    }
};

```

Note a circular singly-linked list has the following built-in functions:

- `empty()`: returns true if the list is empty, false otherwise.
- `size()`: returns the number of elements in the list.
- `push_front(const T& value)`: inserts a new node with the given value at the front of the list.
- `pop_front()`: removes the first node from the list.
- `front()`: returns a reference to the data stored in the first node of the list.
- `insert_after(Node* position, const T& value)`: inserts a new node with the given value after the node pointed to by position.
- `erase_after(Node* position)`: removes the node after the node pointed to by position.
- `clear()`: removes all nodes from the list.
- `rotate()`: rotates the list by moving the first element to the end of the list.

[https://www.geeksforgeeks.org/circular-linked-list/?ref=lbp](https://www.geeksforgeeks.org/circular-linked-list/?ref=lbp)

````
```````
```````    {tab-item} Doubly Linked
[Doubly Linked List](https://www.geeksforgeeks.org/doubly-linked-list-tutorial/)



```` {admonition} Pseudocode

``` {figure} https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2014/03/DLL1.png
```

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

// Node of a doubly linked list
class Node {
public:
    int data;

    // Pointer to next node in DLL
    Node* next;

    // Pointer to previous node in DLL
    Node* prev;
};
```

[https://www.geeksforgeeks.org/doubly-linked-list/?ref=lbp](https://www.geeksforgeeks.org/doubly-linked-list/?ref=lbp)

````
```````
``````` {tab-item} Circular Doubly Linked
[Circular Doubly Linked List](https://www.javatpoint.com/circular-doubly-linked-list)

```` {admonition} Pseudocode

``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20220830114920/doubly.jpg
```

[https://www.geeksforgeeks.org/doubly-circular-linked-list-set-1-introduction-and-insertion/](https://www.geeksforgeeks.org/doubly-circular-linked-list-set-1-introduction-and-insertion/)

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

// Define a Node class to represent each node in the circular doubly-linked list
class Node {
public:
    T data; // data stored in the node
    Node* prev; // pointer to the previous node in the list
    Node* next; // pointer to the next node in the list

    // constructor to initialize a new node with the given data and next pointer
    Node(T data, Node* next = nullptr) {
        this->data = data;
        this->prev = prev;
        this->next = next;
    }
};

// Define the CircularDoublyLinkedList class to represent the circular doubly-linked list
class CircularDoublyLinkedList {
private:
    Node* tail; // pointer to the last node in the list

public:
    // constructor to initialize an empty list with a null tail pointer
    CircularDoublyLinkedList() {
        head = nullptr;
        tail = nullptr;
        size = 0;
    }
};

```
````
```````
``````````

## [Time Complexities](https://www.geeksforgeeks.org/time-complexities-of-different-data-structures/)

````````` {div} full-width
```````` {admonition} array v. linked list

``````` {tab-set} 
``````  {tab-item} Best-case

``` {list-table}
:header-rows: 1

* -
  - access
  - search
  - insert
  - remove
* - array
  - $O(1)$
  - $O(1)$
  - $O(1)$
  - $O(1)$
* - singly linked list
  - $O(1)$
  - $O(1)$
  - $O(1)$
  - $O(1)$
* - doubly linked list
  - $O(1)$
  - $O(1)$
  - $O(1)$
  - $O(1)$
```
``````

`````` {tab-item} Worst-case
``` {list-table}
:header-rows: 1

* -
  - access
  - search
  - insert
  - remove
* - array
  - $\color{red}{O(1)}$
  - $O(n)$
  - $O(n)$
  - $O(n)$
* - singly linked list
  - $O(n)$
  - $O(n)$
  - $O(n)$
  - $O(n)$
* - doubly linked list
  - $O(n)$
  - $O(n)$
  - $\color{red}{O(1)}$
  - $\color{red}{O(1)}$
```
``````

`````` {tab-item} Average-case
``` {list-table}
:header-rows: 1

* -
  - access
  - search
  - insert
  - remove
* - array
  - $\color{red}{O(1)}$
  - $O(n)$
  - $O(n)$
  - $O(n)$
* - singly linked list
  - $O(n)$
  - $O(n)$
  - $\color{red}{O(1)}$
  - $\color{red}{O(1)}$
* - doubly linked list
  - $O(n)$
  - $O(n)$
  - $\color{red}{O(1)}$
  - $\color{red}{O(1)}$
```
``````

```````
````````
`````````

