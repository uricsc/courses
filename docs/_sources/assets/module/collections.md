# Collections

```` {div} full-width
``` {card}
> Programming collections refer to data structures that allow you to store and organize multiple values or elements within a single entity. These collections provide various operations and methods for adding, accessing, modifying, and removing elements, making it easier to work with groups of related data.
>
> Programming collections come in different forms and serve different purposes. 
```
````

## [`array`](https://en.cppreference.com/w/cpp/container/array)

````````` {div} full-width

> An array is a fixed-size collection of elements of the same type. The size of the array is determined at compile-time and cannot be changed at runtime. Elements in an array are accessed using their indices, starting from 0. Arrays offer direct and efficient element access, but their size is fixed.

````````  {grid}
```````   {grid-item-card}
:columns: 12
``` {figure} https://www.simplilearn.com/ice9/free_resources_article_thumb/Vaibhav-Arrays%20Article/Arrays_in_ds-what-is-array-img1.PNG

`array` structure
```
```````
```````   {grid-item-card}
:columns: 6
``` {card}
:text-align: center

<iframe width="100%" height="315" src="https://www.youtube.com/embed/T76E09hnEuo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
``` {code-block} cpp
// Syntax

// Declaration
// <datatype> <array_name>[<size>];
int numbers[5];

// Instantiation
// <datatype> <array_name>[<size>] = {<comma-separated_values>};
int numbers[5] = {1, 2, 3, 4, 5};

// Declaration and Instantiation
char characters[3] = {'a', 'b', 'c'};

```
```````
```````   {grid-item-card}
:columns: 6
``` {code-block} cpp
// Example

// C++ program to illustrate If statement
#include <iostream>
using namespace std;

#include <iostream>

int main() {
    // Declare an array of integers with a fixed size of 5
    int myArray[5];

    // Assign values to array elements
    myArray[0] = 10;
    myArray[1] = 20;
    myArray[2] = 30;
    myArray[3] = 40;
    myArray[4] = 50;

    // Access and print array elements
    for (int i = 0; i < 5; i++) {
        std::cout << myArray[i] << " ";
    }

    return 0;
}


```
<!-- TODO: UPDATE EXAMPLE OUTPUT -->
``` {code-block} bash
// Output

Number is positive.
```
```````
````````
`````````


## [`vector`](https://en.cppreference.com/w/cpp/container/vector)

````````` {div} full-width

> A vector is a dynamic array that can grow or shrink in size at runtime. It provides a convenient way to store and manipulate a sequence of elements. Vectors are similar to arrays, but they have additional member functions to manage their size dynamically. Vectors offer constant time access to elements and efficient insertion/deletion at the end, but slower for insertion/deletion in the middle.

````````  {grid}
```````   {grid-item-card}
:columns: 12
``` {figure} https://www.mycplus.com/mycplus/wp-content/uploads/2018/03/vectors.jpg

`vector` structure
```
```````
```````   {grid-item-card}
:columns: 6
``` {card}
:text-align: center

<iframe width="100%" height="315" src="https://www.youtube.com/embed/RXzzE2wnnlo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
``` {code-block} cpp
// Syntax

// Declaration
// std::vector<<datatype>> <vector_name>;
std::vector<int> numbers;

// Instantiation
// std::vector<<datatype>> <vector_name>(<initial_size>);
std::vector<int> numbers(5);

// Instantiation
// std::vector<<datatype>> <vector_name>(<initial_size>, <initial_value>);
std::vector<int> numbers(5, 0);

// Declaration and Instantiation
std::vector<char> characters = {'a', 'b', 'c'};

```
```````
```````   {grid-item-card}
:columns: 6
``` {code-block} cpp
// Example

#include <iostream>
#include <vector>

std::vector<int> numbers;

numbers.push_back(10);
numbers.push_back(20);
numbers.push_back(30);

std::cout << "Size: " << numbers.size() << std::endl;
std::cout << "First element: " << numbers.at(0) << std::endl;

```

``` {tip}
*dot notation is used to access the `size()` member function and the `at()` member function of the numbers vector*
```

<!-- TODO: UPDATE EXAMPLE OUTPUT -->
``` {code-block} bash
// Output

Number is positive.
```
```````
````````
`````````


## [`forward list`](https://en.cppreference.com/w/cpp/container/forward_list)

````````` {div} full-width

> A forward list is a singly-linked list that allows efficient insertion and deletion at the beginning and in the middle. It is similar to the list but consumes less memory as it only stores a pointer to the next element. Forward lists are suitable when bidirectional traversal is not required.

````````  {grid}
```````   {grid-item-card}
:columns: 12
``` {figure} https://simplesnippets.tech/wp-content/uploads/2019/06/singly-linked-list-data-structure.jpg

`array` structure
```
```````
```````   {grid-item-card}
:columns: 6
``` {card}
:text-align: center

<iframe width="100%" height="315" src="https://www.youtube.com/embed/HKfj0l7ndbc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
``` {code-block} cpp
// Syntax

// Declaration
// <datatype> <array_name>[<size>];
int numbers[5];

// Instantiation
// <datatype> <array_name>[<size>] = {<comma-separated_values>};
int numbers[5] = {1, 2, 3, 4, 5};

// Declaration and Instantiation
char characters[3] = {'a', 'b', 'c'};

```
```````
```````   {grid-item-card}
:columns: 6
``` {code-block} cpp
// Example

#include <iostream>

struct Node {
    int data;
    Node* next;
};

int main() {
    Node* head = new Node();
    Node* second = new Node();
    Node* third = new Node();

    head->data = 10;
    head->next = second;

    second->data = 20;
    second->next = third;

    third->data = 30;
    third->next = nullptr;

    // Traverse and print the linked list
    Node* current = head;
    while (current != nullptr) {
        std::cout << current->data << " ";
        current = current->next;
    }

    // Deallocate memory
    delete head;
    delete second;
    delete third;

    return 0;
}

```
``` {code-block} bash
// Output

10 20 30
```
``` {card}
Define a structure Node that represents a node in the linked list. Each node has an int data value and a Node* pointer to the next node. We create three nodes (head, second, and third) using the new keyword and assign data values to them. We also set the next pointers to establish the links between nodes. To traverse the linked list, we use a current pointer that starts from the head and moves to the next node until it reaches the end (indicated by a nullptr). We print the data values of each node while traversing the list. Finally, we deallocate the memory for each node using the delete operator.
```
``` {tip}
*Remember to free the memory allocated dynamically using `delete` to avoid memory leaks when working with pointers in both vectors and linked lists.*
```
```````
````````
`````````

## For Good Measure...

The following are worthwhile to know of but unnecessary for the scope of this course.

### When order matters...

```````` {div} full-width
```````  {card}
``````  {tab-set}
`````   {tab-item} Stack

``` {figure} https://www.mycplus.com/mycplus/wp-content/uploads/2008/09/Stack.png
```

> A stack is a Last-In-First-Out (LIFO) container that allows insertion and removal of elements from one end called the top. It follows the principle of "last in, first out." Elements are inserted and removed from the same end, making it useful for managing function calls, undo operations, etc. The stack container does not provide direct access to elements in the middle.
`````
`````   {tab-item} Queue

``` {figure} https://miro.medium.com/v2/resize:fit:3148/0*TRbfsq86lqDoqW6b.png
:width: 600px
```

> A queue is a First-In-First-Out (FIFO) container that allows insertion at one end (rear) and removal from the other end (front). It follows the principle of "first in, first out." Elements are inserted at the rear and removed from the front, making it suitable for managing tasks, waiting lists, etc. The queue container does not provide direct access to elements in the middle.
`````
`````   {tab-item} Deque

``` {figure} https://pythontic.com/deque.jpg
```

> A deque (short for double-ended queue) is a dynamic array-like container that allows efficient insertion and deletion at both ends. It combines the benefits of arrays and lists, providing fast random access to elements and efficient insertion/deletion at the front and back. Deques are less efficient than vectors for random access but are better suited for frequent insertions and deletions at both ends.
`````
`````   {tab-item} Priority Queue

``` {figure} https://netmatze.files.wordpress.com/2014/08/priorityqueue.png
:width: 600px
```

> A priority queue is a container that provides constant time insertion and retrieval of the element with the highest priority. It does not maintain the elements in a specific order but allows you to access the element with the highest priority first. Priority queues are typically implemented using heaps.
`````
``````
```````
````````

### When location & distance matter...

```````` {div} full-width
```````  {card}
``````  {tab-set}
`````   {tab-item} Set
> A set is an ordered collection of unique elements. It automatically sorts the elements in a specific order, such as ascending or descending. Set containers do not allow duplicate elements. Searching for an element in a set is efficient, and insertions/removals maintain the sorted order of elements.
`````
`````   {tab-item} Multiset
> A multiset is similar to a set, but it allows duplicate elements. It stores the elements in a specific order and supports efficient insertion, removal, and search operations. Multisets are useful when multiple occurrences of an element need to be stored.
`````
`````   {tab-item} Map
> A map is an associative container that stores key-value pairs. Each key in a map is unique, and the elements are sorted by their keys. Map provides efficient search, insertion, and deletion of elements based on the key. Map containers are useful when data needs to be stored and accessed based on a unique identifier.
`````
`````   {tab-item} Multimap
> A multimap is similar to a map, but it allows multiple elements with the same key. It stores key-value pairs and allows efficient search, insertion, and deletion based on the key. Multimaps are suitable when multiple elements need to be associated with the same key.
`````
``````
```````
````````
