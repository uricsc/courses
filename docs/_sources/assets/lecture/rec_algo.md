# Recursive Algorithms (Analysis)

`````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/6oDQaB2one8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
A recursive algorithm is an algorithm that calls itself to solve a problem. It is a powerful technique used in computer science to solve complex problems by breaking them down into smaller sub-problems.

The analysis of recursive algorithms involves determining the number of times the algorithm will call itself and the amount of work that is done at each level of recursion. This analysis is important because it helps us understand the efficiency of the algorithm and how it scales with input size.

The time complexity of a recursive algorithm is often expressed in terms of a recurrence relation, which describes the relationship between the time taken by the algorithm at each level of recursion. Solving the recurrence relation allows us to determine the overall time complexity of the algorithm.

Recursive algorithms are commonly used in data structures and algorithms, such as sorting, searching, and graph traversal. For example, the quicksort algorithm is a well-known sorting algorithm that uses recursion to divide a large array into smaller sub-arrays.

While recursive algorithms can be elegant and powerful, they can also be inefficient if not carefully designed. Recursive algorithms can lead to stack overflow if the depth of the recursion becomes too large, which can happen if the input size is large or if the recursion is not properly bounded. Therefore, careful analysis and design are necessary when using recursive algorithms.
```

``` {card} Additional Resources
<!-- <iframe width="560" height="315" src="https://www.youtube.com/embed/HXNhEYqFo0o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> -->
- [Programming Loops vs Recursion - Computerphile | Computerphile](https://youtu.be/HXNhEYqFo0o) : 12:31
```
`````
<!-- ``` {image} https://cdn-images-1.medium.com/max/1200/1*3Kti9X9KAL0_XCk1cdjbDw.jpeg
:align: center
``` -->
``````````

`````````` {div} full-width
``````````

## Recursion

`````````` {div} full-width
``````` {card}

``` {admonition} Define
The process of solving a problem by reducing it to smaller versions of itself

- Solve a task by reducing it to smaller tasks (of the same structure)
- Technically, a recursive function is one that calls itself
```

``` {figure} https://cdn.slidesharecdn.com/ss_thumbnails/recursion-130206094649-phpapp01-thumbnail-4.jpg?cb=1360144228
```
`````` {admonition} General Form
````` {grid}
```` {grid-item}
:columns: 12
```cpp
int someFunction() {
    if (base_case) {
        // calculate trivialSolution       
    } else {
        // break task into subtasks
        // solve each task recursively
        // merge solutions if necessary
    }
}
```
````

```` {grid-item}
:columns: 6
``` {dropdown} base case
- solution for a **trivial case**
- it can be used to stop the recursion (prevents _“stack overflow”_)  
- every recursive algorithm needs at least one base case
```
````
```` {grid-item}
:columns: 6
``` {dropdown} recursive calls
- divide problem into **smaller instance(s)** of the **same structure**
```
````
`````
``````

```` {admonition} Rules
:class: tip

1. Every recursive definition must have one (or more) base cases.
2. The general case must eventually be reduced to a base case.
3. The base case stops the recursion.
````

```` {card} Why recursion?

``` {dropdown} Can we live without it?
- yes, you can write “any program” with arrays, loops, and conditionals
```

``` {dropdown} However ...

The choice between a recursive algorithm and an iterative algorithm depends on several factors. Here are some scenarios where a recursive algorithm may be more suitable:

Problems with inherent recursive structure
: Recursive algorithms are well-suited for solving problems that have a natural recursive structure. If the problem can be easily divided into smaller sub-problems that are of the same type as the original problem, a recursive solution can be intuitive and concise.

Problems involving backtracking or tree/graph traversal
: Recursive algorithms are commonly used in backtracking scenarios, where you explore different paths or combinations to find a solution. Similarly, tree or graph traversal problems, such as depth-first search or recursive tree traversals, often lend themselves well to recursive solutions.

Problems with smaller problem sizes
: Recursive algorithms can be more efficient when dealing with smaller problem sizes. If the problem size is relatively small, the overhead of recursive function calls may not significantly impact performance.

Problems with divide-and-conquer approach
: Recursive algorithms are often employed in divide-and-conquer strategies. If the problem can be divided into independent sub-problems that can be solved individually and then combined to obtain the final result, a recursive approach can be beneficial.

```

``` {dropdown} Considerations

Recursive algorithms may have some drawbacks, such as increased memory usage due to the recursive function call stack, potential performance issues for large problem sizes, and the possibility of exceeding the stack size limit in certain programming languages.

Iterative algorithms can be advantageous in scenarios where a loop structure and mutable variables can be used to iteratively solve the problem without incurring the overhead of recursive function calls.

Ultimately, the choice between recursive and iterative algorithms depends on the nature of the problem, the problem size, the available resources, and the trade-offs between simplicity, efficiency, and readability of the code.
```



``` {figure} imgs/09_s05.png

[https://courses.cs.washington.edu/courses/cse120/17sp/labs/11/tree.html](https://courses.cs.washington.edu/courses/cse120/17sp/labs/11/tree.html)
```


````

```````
``````````


### Recursive Call Tree

`````````` {div} full-width


`````` {admonition} Sum Array
`````  {tab-set}
````   {tab-item} Code
```cpp
int sum_array(int *A, int n) {
  //basecase  
  if (n == 1)
    return A[0];

  //solve sub-task
  int sum = sum_array(A, n - 1);

  //return
  return A[n - 1] + sum;
}
```
````
```` {tab-item} Base & Recursive Cases

$$
T(n) =
\begin{cases}
A[0],  & \text{if $n\ = 1$},  & \text{// base case}  \\[2ex]
A[n - 1], & \text{if $n \gt 1$ },  & \text{// recursive calls}
\end{cases}
$$

````
`````

``` {card} [Visualize](https://pythontutor.com/iframe-embed.html#code=%23include%20%3Ciostream%3E%0A%0A%0Aint%20sum_array%28int%20*A,%20int%20n%29%20%7B%0A%20%20//basecase%20%20%0A%20%20if%20%28n%20%3D%3D%201%29%0A%20%20%20%20return%20A%5B0%5D%3B%0A%0A%20%20//solve%20sub-task%0A%20%20int%20sum%20%3D%20sum_array%28A,%20n%20-%201%29%3B%0A%0A%20%20//return%0A%20%20return%20A%5Bn%20-%201%5D%20%2B%20sum%3B%0A%7D%0A%0Aint%20main%20%28%29%20%7B%0A%20%20%20%20int%20arr%5B%5D%20%3D%20%7B%2010,%2020,%2030,%2040%7D%3B%0A%20%20%20%20sum_array%28arr,%204%29%3B%0A%20%20%20%20return%200%3B%0A%7D%0A&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false)
<iframe allow="fullscreen" width="675" height="675" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=%23include%20%3Ciostream%3E%0A%0A%0Aint%20sum_array%28int%20*A,%20int%20n%29%20%7B%0A%20%20//basecase%20%20%0A%20%20if%20%28n%20%3D%3D%201%29%0A%20%20%20%20return%20A%5B0%5D%3B%0A%0A%20%20//solve%20sub-task%0A%20%20int%20sum%20%3D%20sum_array%28A,%20n%20-%201%29%3B%0A%0A%20%20//return%0A%20%20return%20A%5Bn%20-%201%5D%20%2B%20sum%3B%0A%7D%0A%0Aint%20main%20%28%29%20%7B%0A%20%20%20%20int%20arr%5B%5D%20%3D%20%7B%2010,%2020,%2030,%2040%7D%3B%0A%20%20%20%20sum_array%28arr,%204%29%3B%0A%20%20%20%20return%200%3B%0A%7D%0A&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
```
``````

``````` {admonition} Largest
``````  {tab-set}
`````   {tab-item} Pseudocode

To find the largest element in list[a]...list[b]  

a. Find the largest element in `list[a + 1]...list[b]` and call it `max`
b. Compare the elements `list[a]` and `max`
  - `if (list[a] >= max)` the largest element in `list[a]...list[b]` is `list[a]`  
  - otherwise, the largest element in `list[a]...list[b]` is `max` 

`````
````` {tab-item} Code
``` {code-block} cpp
int largest (const int list[], int lowerIndex, int upperIndex) {
  int max;
  if (lowerIndex == upperIndex) //size of the sublist is one 
    return list[lowerIndex];
  else {
    max = largest(list, lowerIndex + 1, upperIndex);
    if (list[lowerIndex] >= max) 
      return list[lowerIndex];
    else
      return max;
  }
}
```
`````
````` {tab-item} Base & Recursive Cases

$$
T(n) =
\begin{cases}
size\ of\ list\ = 1,  & \text{// base case}  \\[2ex]
size\ of\ list\ is\ \gt 1, & \text{// recursive calls}
\end{cases}
$$

`````
``````
```````


``````` {admonition} [Serpinski](https://www.geeksforgeeks.org/sierpinski-triangle/)

````` {tab-set}
````  {tab-item} Code
``` {code-block} cpp
void printSierpinski(int n)
{
    for (int y = n - 1; y >= 0; y--) {
        for (int i = 0; i < y; i++)
            cout << " ";
    
        for (int x = 0; x + y < n; x++) {
            if(x & y)
            cout << " " << " ";
        else
            cout << "* ";
        }
        cout << endl;
    }
}
```
````

````  {tab-item} Visualize : Structure

``` {figure} https://runestone.academy/ns/books/published/pythonds/_images/stCallTree.png
```
````

```` {tab-item} Ex : Triangle
``` {figure} https://www.researchgate.net/profile/Askander-Kaka/publication/264872595/figure/fig4/AS:669568435494921@1536648963162/First-four-steps-to-configure-Sierpinski-triangle.png
```
````

```` {tab-item} Ex : Pyramid
``` {figure} https://upload.wikimedia.org/wikipedia/commons/b/b4/Sierpinski_pyramid.png
```
````
`````
```````
``````````

## Recursion v. Iteration

`````````` {div} full-width
``````` {card}

`````` {grid}

````` {grid-item} 
````  {admonition} Recursive

```cpp
#include <iostream>

int factorialRecursive(int n) {
    if (n == 0)
        return 1;
    else
        return n * factorialRecursive(n - 1);
}

int main() {
    int num = 5;
    int result = factorialRecursive(num);
    std::cout << "Factorial of " << num << " is: " << result << std::endl;
    return 0;
}

```

``` {card}
The recursive function `factorialRecursive` calculates the factorial by breaking down the problem into smaller sub-problems. The *base case* is when `n` equals `0`, and for any other value of `n`, the factorial is computed by multiplying `n` with the factorial of `n-1`.
```

````
`````

````` {grid-item} 
````  {admonition} Iterative

```cpp
#include <iostream>

int factorialIterative(int n) {
    int result = 1;
    for (int i = 1; i <= n; ++i) {
        result *= i;
    }
    return result;
}

int main() {
    int num = 5;
    int result = factorialIterative(num);
    std::cout << "Factorial of " << num << " is: " << result << std::endl;
    return 0;
}

```

``` {card}
The iterative function `factorialIterative` calculates the factorial by using a loop. It initializes result to `1` and then iterates over the numbers from `1` to `n`, multiplying each number with the current value of result to accumulate the factorial.
```

````
`````
```````
``````````

##  Recursion Tree Call


`````````` {div} full-width
`````` {card}

````` {admonition} [binary search](https://www.geeksforgeeks.org/binary-search/)
```cpp
int bsearch(int *A, int lo, int hi, int k) {
  //base case
  if (hi < lo)
    return NOT_FOUND;

  // calculate mid point index
  int mid = lo + ( (hi - lo) / 2);
  // key found?
  if (A[mid] == k)
    return mid;
  // key in upper subarray?
  if (A[mid] < k)
    return bsearch(A, mid + 1, hi, k);
  // key is in lower subarray?
  return bsearch(A, lo, mid - 1, k);
}
```
`````

````` {admonition} Visualize: General Form
:class: tip
[https://www.cs.usfca.edu/~galles/visualization/Search.html](https://www.cs.usfca.edu/~galles/visualization/Search.html)
`````
``````

`````` {admonition} [Visualize: in memory](https://pythontutor.com/iframe-embed.html#code=//%20C%2B%2B%20program%20to%20implement%20recursive%20Binary%20Search%0A%23include%20%3Cbits/stdc%2B%2B.h%3E%0Ausing%20namespace%20std%3B%0A%0A//%20A%20recursive%20binary%20search%20function.%20It%20returns%0A//%20location%20of%20x%20in%20given%20array%20arr%5Bl..r%5D%20is%20present,%0A//%20otherwise%20-1%0Aint%20binarySearch%28int%20arr%5B%5D,%20int%20l,%20int%20r,%20int%20x%29%0A%7B%0A%20%20%20%20if%20%28r%20%3E%3D%20l%29%20%7B%0A%20%20%20%20%20%20%20%20int%20mid%20%3D%20l%20%2B%20%28r%20-%20l%29%20/%202%3B%0A%0A%20%20%20%20%20%20%20%20//%20If%20the%20element%20is%20present%20at%20the%20middle%0A%20%20%20%20%20%20%20%20//%20itself%0A%20%20%20%20%20%20%20%20if%20%28arr%5Bmid%5D%20%3D%3D%20x%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20mid%3B%0A%0A%20%20%20%20%20%20%20%20//%20If%20element%20is%20smaller%20than%20mid,%20then%0A%20%20%20%20%20%20%20%20//%20it%20can%20only%20be%20present%20in%20left%20subarray%0A%20%20%20%20%20%20%20%20if%20%28arr%5Bmid%5D%20%3E%20x%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20binarySearch%28arr,%20l,%20mid%20-%201,%20x%29%3B%0A%0A%20%20%20%20%20%20%20%20//%20Else%20the%20element%20can%20only%20be%20present%0A%20%20%20%20%20%20%20%20//%20in%20right%20subarray%0A%20%20%20%20%20%20%20%20return%20binarySearch%28arr,%20mid%20%2B%201,%20r,%20x%29%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20//%20We%20reach%20here%20when%20element%20is%20not%0A%20%20%20%20//%20present%20in%20array%0A%20%20%20%20return%20-1%3B%0A%7D%0A%0Aint%20main%28void%29%0A%7B%0A%20%20%20%20int%20arr%5B%5D%20%3D%20%7B%202,%203,%204,%2010,%2040%20%7D%3B%0A%20%20%20%20int%20x%20%3D%2010%3B%0A%20%20%20%20int%20n%20%3D%20sizeof%28arr%29%20/%20sizeof%28arr%5B0%5D%29%3B%0A%20%20%20%20int%20result%20%3D%20binarySearch%28arr,%200,%20n%20-%201,%20x%29%3B%0A%20%20%20%20%28result%20%3D%3D%20-1%29%0A%20%20%20%20%20%20%20%20%3F%20cout%20%3C%3C%20%22Element%20is%20not%20present%20in%20array%22%0A%20%20%20%20%20%20%20%20%3A%20cout%20%3C%3C%20%22Element%20is%20present%20at%20index%20%22%20%3C%3C%20result%3B%0A%20%20%20%20return%200%3B%0A%7D&codeDivHeight=400&codeDivWidth=350&cppShowMemAddrs=true&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false)

<iframe allow="fullscreen" width="675" height="675" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=//%20C%2B%2B%20program%20to%20implement%20recursive%20Binary%20Search%0A%23include%20%3Cbits/stdc%2B%2B.h%3E%0Ausing%20namespace%20std%3B%0A%0A//%20A%20recursive%20binary%20search%20function.%20It%20returns%0A//%20location%20of%20x%20in%20given%20array%20arr%5Bl..r%5D%20is%20present,%0A//%20otherwise%20-1%0Aint%20binarySearch%28int%20arr%5B%5D,%20int%20l,%20int%20r,%20int%20x%29%0A%7B%0A%20%20%20%20if%20%28r%20%3E%3D%20l%29%20%7B%0A%20%20%20%20%20%20%20%20int%20mid%20%3D%20l%20%2B%20%28r%20-%20l%29%20/%202%3B%0A%0A%20%20%20%20%20%20%20%20//%20If%20the%20element%20is%20present%20at%20the%20middle%0A%20%20%20%20%20%20%20%20//%20itself%0A%20%20%20%20%20%20%20%20if%20%28arr%5Bmid%5D%20%3D%3D%20x%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20mid%3B%0A%0A%20%20%20%20%20%20%20%20//%20If%20element%20is%20smaller%20than%20mid,%20then%0A%20%20%20%20%20%20%20%20//%20it%20can%20only%20be%20present%20in%20left%20subarray%0A%20%20%20%20%20%20%20%20if%20%28arr%5Bmid%5D%20%3E%20x%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20binarySearch%28arr,%20l,%20mid%20-%201,%20x%29%3B%0A%0A%20%20%20%20%20%20%20%20//%20Else%20the%20element%20can%20only%20be%20present%0A%20%20%20%20%20%20%20%20//%20in%20right%20subarray%0A%20%20%20%20%20%20%20%20return%20binarySearch%28arr,%20mid%20%2B%201,%20r,%20x%29%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20//%20We%20reach%20here%20when%20element%20is%20not%0A%20%20%20%20//%20present%20in%20array%0A%20%20%20%20return%20-1%3B%0A%7D%0A%0Aint%20main%28void%29%0A%7B%0A%20%20%20%20int%20arr%5B%5D%20%3D%20%7B%202,%203,%204,%2010,%2040%20%7D%3B%0A%20%20%20%20int%20x%20%3D%2010%3B%0A%20%20%20%20int%20n%20%3D%20sizeof%28arr%29%20/%20sizeof%28arr%5B0%5D%29%3B%0A%20%20%20%20int%20result%20%3D%20binarySearch%28arr,%200,%20n%20-%201,%20x%29%3B%0A%20%20%20%20%28result%20%3D%3D%20-1%29%0A%20%20%20%20%20%20%20%20%3F%20cout%20%3C%3C%20%22Element%20is%20not%20present%20in%20array%22%0A%20%20%20%20%20%20%20%20%3A%20cout%20%3C%3C%20%22Element%20is%20present%20at%20index%20%22%20%3C%3C%20result%3B%0A%20%20%20%20return%200%3B%0A%7D&codeDivHeight=400&codeDivWidth=350&cppShowMemAddrs=true&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

``````
``````````








## Unimodal arrays

`````````` {div} full-width
``````` {card}

``` {admonition} Define
An array is (<span class="blue">strongly</span>) **unimodal** if it can be split into an increasing part followed by a decreasing part

An array is (<span class="blue">weakly</span>) **unimodal** if it can be split into a non-decreasing part followed by a non-increasing part
```

```` {card} Various modalities 
``` {figure} https://i0.wp.com/makemeanalyst.com/wp-content/uploads/2017/05/Unimodal-Bomodal-Multimodal-Uniform.png?resize=813%2C530
```
````

```````
``````````

### Find the max (strongly unimodal)

`````````` {div} full-width
``````` {card}

```` {admonition} code
```cpp
int max_s_unimodal (int *A, int low, int hi) {  
  if (low == hi)
    return A[low];

  int mid = (low + hi) / 2;  

  if (A[mid] < A[mid+1])
    return max_s_unimodal(A, mid + 1, hi);
  else 
    return max_s_unimodal(A, low, mid);
}
```
````

`````` {grid}
````` {grid-item-card}
``` {figure} imgs/09_s29.png
```
`````
<!-- ````` {grid-item-card}
``` {figure} imgs/09_unimodal_strong.png
```
````` -->
``````

```````
``````````

### Find the max (weakly unimodal)

`````````` {div} full-width
``````` {card}

```` {admonition} code
```cpp
int max_w_unimodal (int *A, int low, int hi) {
  if (low == hi)
    return A[low];

  int mid = (low + hi) / 2;

  if (A[mid] < A[mid + 1])
    return max_w_unimodal(A, mid + 1, hi);
  else if (A[mid] > A[mid + 1])
    return max_w_unimodal(A, low, mid);
  else {
    int left = max_w_unimodal(A, mid+1, hi);  
    int right = max_w_unimodal(A, low, mid);
    return std::max(left, right);
  }
}
```
````

`````` {grid}
````` {grid-item-card}
``` {figure} imgs/09_s31.png
```
`````
<!-- ````` {grid-item-card}
``` {figure} imgs/09_unimodal_weak.png
:width: 100%
```
````` -->
``````

```````
``````````