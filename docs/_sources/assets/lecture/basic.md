# Basic Sorts (Analysis)

`````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/RfXt_qHDEPw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
Sorting is a fundamental problem in computer science, and it involves arranging a collection of data in a specific order. There are various sorting algorithms available that can be used to sort data in ascending or descending order based on a specific criterion.

Some of the most basic sorting algorithms include:

Bubble Sort
: It is a simple sorting algorithm that repeatedly compares adjacent elements and swaps them if they are in the wrong order. This algorithm has a time complexity of $O(n^2)$.

Insertion Sort
: It is a simple sorting algorithm that works by inserting each element in its proper place in a sorted sub-array. This algorithm has a time complexity of $O(n^2)$ but performs better than bubble sort for small data sets.

Selection Sort
: It is a sorting algorithm that repeatedly selects the smallest element from an unsorted sub-array and swaps it with the first element of the sub-array. This algorithm has a time complexity of $O(n^2)$.

Merge Sort
: It is a divide-and-conquer sorting algorithm that recursively divides the input array into two halves, sorts them separately, and then merges them back together. This algorithm has a time complexity of $O(n\ log\ n\)$.

Quick Sort
: It is also a divide-and-conquer sorting algorithm that picks a pivot element and partitions the array around it. This algorithm has a time complexity of $O(n\ log\ n)$ on average but can degrade to $O(n^2)$ in the worst-case scenario.

Each sorting algorithm has its advantages and disadvantages in terms of time and space complexity, stability, adaptability, and implementation complexity. Understanding and comparing the different sorting algorithms is an important skill for anyone studying data structures and algorithms as it enables them to select the best algorithm for their use case.
```

``` {card} Additional Resources
- [Selection sort in 3 minutes | Michael Sambol](https://youtu.be/g-PGLbMth_g)
- [Insertion sort in 2 minutes | Michael Sambol](https://youtu.be/JU767SDMDvA)
```
``` {figure} https://cdn-images-1.medium.com/max/1600/1*bPpvELo9_QqQsDz7CSbwXQ.gif
:align: center
```
``````````

## Internships & Jobs

`````````` {div} full-width
``````` {grid}
`````` {grid-item-card}
:columns: 6
:link: https://careers.google.com/how-we-hire/interview
````` {image} https://www.salesforceben.com/wp-content/uploads/2021/03/google-logo-icon-PNG-Transparent-Background-2048x2048.png
:align: center
:height: 300px
:width: 300px
`````
``````
`````` {grid-item-card}
:columns: 6
:link: https://www.amazon.jobs/en/landing_pages/software-development-topics
````` {image} https://www.pngkey.com/png/full/480-4803237_amazon-icon-amazon-logo-png-icon.png
:align: center
:height: 300px
:width: 300px
`````
``````
`````` {grid-item-card}
:columns: 6
:link: https://www.metacareers.com/life/
````` {image} https://sanganan.com/wp-content/uploads/2021/12/Meta-logo.png
:align: center
:height: 300px
:width: 300px
`````
``````
`````` {grid-item-card}
:columns: 6
:link: https://uri.joinhandshake.com/login
````` {image} https://www.wpi.edu/sites/default/files/handshake-logo.png
:align: center
:height: 300px
:width: 300px
`````
``````
```````
``````````

## Worst-case, Average-case, Best-case

`````````` {div} full-width
````` {grid}



```` {grid-item-card} Warm-up 1
:columns: 6
Analyze this code

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

unsigned int argmin (const std::vector<int> &values) { 
    unsigned int length = values.size();
    assert(length > 0);
    unsigned int idx = 0;
    int current = values[0];
    for (unsigned int i = 1; i < length; i++) {
        if (values[i] < current) {
            current = values[i];
            idx = i;
        }
    }
    return idx;
}
```

``` {dropdown} $T(n)\ =\ ?$ <br> $based\ on\ number\ of\ comparisons$
$$T(n)\ =\ n - 1$$

The number of comparisons in this program is `n - 1`, where n is the size of the vector.
```

````

```` {grid-item-card} Warm-up 2
:columns: 6
Analyze this code

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

bool argk (const std::vector<int> &values, 
                                    int k, 
                        unsigned int &idx) 
{  
    unsigned int length = values.size();
    for (unsigned int i = 0; i < length; i++) {
        if (values[i] == k) {
            idx = i;
            return true;
        }
    }
    return false;
}
```

``` {dropdown} $T(n)\ =\ ?$ <br> $based\ on\ number\ of\ comparisons$

$$T(n)\ =\ n$$

The number of comparisons in this program is equal to the number of elements in the given vector. Therefore, the number of comparisons is dependent on the size of the input vector. The time complexity of this program is `O(n)`, where `n` is the size of the input vector.
```
````
`````
``````````

### Analysis types

`````````` {div} full-width
``````` {card}
`````` {grid}
```` {grid-item}
``` {dropdown} 😕 Worst-case
- **maximum** time of algorithm on **any** input
```
````
```` {grid-item}
``` {dropdown} 🤔 Average-case
- **expected** time of algorithm over **all** inputs
```
````
```` {grid-item}
``` {dropdown} 🦄 Best-case
- **minimum** time of algorithm on **some** (optimal) input
```
````
``````

``` {note}

While <b class="red">asymptotic analysis</b> describes $T(n) \Rightarrow \infty$...

- _asymptotic notation: big-O, big-$\Omega$, $\Theta$_

<b class="red">Case analysis</b> looks into the different input types

- best-case, worst-case, average-case

```

$$Both\ analysis\ types\ are\ orthogonal\ to\ each\ other$$

```````
``````````

### Examples

`````````` {div} full-width
``````` {grid}

```` {grid-item-card} [Factorial of a number (iterative algorithm)](https://www.geeksforgeeks.org/program-for-factorial-of-a-number/)
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

// pseudocode

function factorial(n):
    if n <= 1:
        return 1
    result = 1
    for i in range(1, n+1):
        result *= i
    return result
```

``` {dropdown} ❓Case
**🤔 Best-case**

Without possibility of extra steps, the only analysis can be best-case...
```
````

```` {grid-item-card} [Sequential search (return first occurrence)](https://www.geeksforgeeks.org/linear-search/)
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

// pseudocode

function find_first(items, target):
    index = 0
    while index < len(items):
        if items[index] == target:
            return index
        index += 1
    return -1
```

``` {dropdown} ❓Case
**🤔 Average-case**

Arguably, the first occurrence could be the first or last element/node in the collection. The majority of the time, it will not be either first or last, leading to only one logical result, average-case...
```
````

```` {grid-item-card} [Sequential search (return last occurrence)](https://www.geeksforgeeks.org/linear-search)
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

// pseudocode

function find_last(items, target):
    index = len(items) - 1
    while index >= 0:
        if items[index] == target:
            return index
        index -= 1
    return -1
```

``` {dropdown} ❓Case 
**🤔 Worst-case**

Arguably, the value could be found at anywhere but the last element/node of the collection. However, we must still complete a comparison of the desired value and each element/node in the collection to exhaust all possibilities, therefore, it would fall into worst-case...
```
````
```````
``````````

## Basic Sorting Algorithms

### Sorting

`````````` {div} full-width
``` {card}

Given $n$ elements that can be compared according to a [total order](https://math.libretexts.org/Bookshelves/Combinatorics_and_Discrete_Mathematics/A_Spiral_Workbook_for_Discrete_Mathematics_(Kwong)/07%3A_Relations/7.04%3A_Partial_and_Total_Ordering) relation

- we want to rearrange them in non-increasing/non-decreasing order
- for example (non-decreasing):
  - `input`: sequence of items $\ \ \ \ \ \ \ \ \ \ \ A = [k_0, k_1, \dots, k_{n - 1}]$
  - `output`: permutation of A $\ \ \ \ \ \ \ \ \ \ \ B\ |\ B[0]\ \le\ B[1]\ \le \dots B[n - 1]$

$$\\ \\ \\ Central\ problem\ in\ computer\ science$$

```
``````````

## [Insertion Sort](https://www.geeksforgeeks.org/insertion-sort/)

`````````` {div} full-width
````` {admonition} Defined as...
:class: tip

Array is divided into <b class="orange">sorted</b> and **unsorted** parts

- algorithm scans array from <b class="orange">left to right</b>

Invariants

- elements in <b class="orange">sorted</b> are in ascending order
- elements in **unsorted** have not been seen


```` {dropdown} visualization : linked list
``` {figure} http://jason-chen-1992.weebly.com/uploads/1/0/8/5/108557741/webp-net-gifmaker_1_orig.gif
```
````
```` {dropdown} visualization : interactive

<iframe src="https://visualgo.net/en/sorting" allowfullscreen="true" height="750" width="1000"></iframe>
````


``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

void insertion_sort(int* items, int size) {
    //grows the left part (sorted)
    for (int i = 1; i < size; i++) {
        int j = i;
        //inserts j in sorted part
        while (j > 0 && items[j-1] > items[j]) {
            swap(items[j-1], items[j]);
            j--;
        }
    }
}
```

$$Number\ of\ comparisons?\ |\ Number\ of\ exchanges?$$
`````
``````````

## Analysis — Insertion Sort(comparisons)

`````````` {div} full-width
`````` {card}

**Running time depends on the input**

````` {grid}

```` {grid-item-card}
:columns: 4
``` {glossary} 
Worst-case?
    input is already sorted in descending order
```
$$\begin {align}
\sum_{i = 1}^{N - 1} i &= 1 + 2 + 3 + \dots + (N - 1) \\
&= \frac{N(N - 1)}{2} \\
&= O(N^2) \\
\end {align}$$
````

```` {grid-item-card}
:columns: 4
``` {glossary} 
Average-case?
    each element $\approx$ halfway order 
    
    expect every element to move $O(\frac{n}{2})$ times
```
$$\begin {align}
\sum_{i = 1}^{N - 1} \frac{i}{2} &= \frac{1}{2} (1 + 2 + 3 + \dots + (N - 1)) \\
&= \frac{N(N - 1)}{4} \\
&= O(N^2) \\
\end {align}$$
````

```` {grid-item-card}
:columns: 4
``` {glossary} 
Best-case?
    input is already sorted in ascending order
```
$$\begin {align}
\sum_{i = 1}^{N - 1} 1 &= (N - 1) \\
&= O(N) \\
\end {align}$$
````




```` {grid-item-card}
:columns: 4
:link: https://www.hackerearth.com/practice/algorithms/sorting/insertion-sort/visualize/
``` {figure} img/basic_sorts_worst.png

```
````

```` {grid-item-card}
:columns: 4
:link: https://www.hackerearth.com/practice/algorithms/sorting/insertion-sort/visualize/
``` {figure} img/basic_sorts_average.png

```
````

```` {grid-item-card}
:columns: 4
:link: https://www.hackerearth.com/practice/algorithms/sorting/insertion-sort/visualize/
``` {figure} img/basic_sorts_best.png

```
````

```` {grid-item-card}
:columns: 4
:text-align: center
{90, 80, 70, 60, 50, 40, 30, 20}
````

```` {grid-item-card}
:columns: 4
:text-align: center
{60, 50, 30, 90, 20, 70, 80, 40}
````

```` {grid-item-card}
:columns: 4
:text-align: center
{20, 30, 40, 50, 60, 70, 80, 90}
````

`````
``````
``````````

### Partially sorted arrays

`````````` {div} full-width
``````` {card}

`````` {card} inversion

A pair of keys that are out of order

````` {dropdown} ![image](imgs/06_s16.png)

``` {figure} https://www.erikedrosa.com/imgs/insertionsort.gif
swapping indices
```
`````

``` {epigraph} 
“array is **partially sorted** if the number of pairs that are out-of-order is $O(n)$” 
```

For partially-sorted arrays, insertion sort runs in <b class="orange">linear time</b>.

$$Θ(n)$$

``````

```````
``````````

## [Selection Sort](https://www.geeksforgeeks.org/selection-sort/)

`````````` {div} full-width
`````` {admonition} Defined as
:class: tip


Array is divided into <b class="orange">sorted</b> and **unsorted** parts
- algorithm scans array from left to right


**Invariants**

- elements in <b class="orange">sorted</b> are **fixed** and in ascending order
- no element in **unsorted** is smaller than any element in <b class="orange">sorted</b>

```` {dropdown} ![](imgs/06_s17.png)
``` {figure} https://piratelearner.com/static/media/images/admin/2015/10/13/selection.gif
:align: center
```
````

```` {dropdown} visualization : gif
``` {figure} https://miro.medium.com/max/1400/1*5WXRN62ddiM_Gcf4GDdCZg.gif
```
````

```` {dropdown} visualization : interactive
<iframe src="https://visualgo.net/en/sorting" allowfullscreen="true" height="750" width="1000"></iframe>
````
```` {card}
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

void selectionsort (int *A, unsigned int n) {
    int temp;
    unsigned int i, j, min;
    // grows the left part (sorted) 
    for (i = 0; i < n; i++) {
        min = i;
        // find min in unsorted part
        for (j = i + 1; j < n; j++) {
            if (A[j] < A[min]) {
                min = j;
            }
        }
        // swap A[i] and A[min]
        temp = A[i];  
        A[i] = A[min];
        A[min] = temp;
    }
}
```


``` {dropdown} $Number\ of\ comparisons?\ |\ Number\ of\ exchanges?$

In the above snippet, the selection sort algorithm is implemented. The number of comparisons and exchanges made depend on the size of the input array `n`.

For comparisons, there are two nested `for`-loops that compare all elements of the array. The outer `for`-loop, which runs from $i = 0$ to $n - 1$, runs `n` times. The inner `for`-loop, which runs from $j = i + 1$ to $n - 1$, runs $n - i - 1$ times. Therefore, the total number of comparisons is:

$$(n-1) + (n-2) + (n-3) + ... + 1 = \frac{n(n-1)}{2}$$

For exchanges, each iteration of the outer `for`-loop swaps the element at index i with the element at index min. Since this occurs `n` times, the total number of exchanges is `n`.

<iframe src="https://opendsa-server.cs.vt.edu/embed/ptrSwapCON" allowfullscreen="true" height="350" width="1000"></iframe>
```
````

``` {dropdown} visualization : comparisons & exchanges
<iframe src="https://opendsa-server.cs.vt.edu/embed/SelectionSortAnalysisCON" height="600" width="100%"></iframe>
```

``` {dropdown} Notes

Selection Sort: moves through each element finding the minimum value and replacing the current element value as it goes.

$$A[0] \rightarrow A [1] \rightarrow A[2] \rightarrow A[n - 1]$$

- sorted portion left order, fixed, untouched
- unsorted iterated through to find remaining min value to swap current element value

``````
``````````

## Summary

`````````` {div} full-width
``````` {card}
`````` {tab-set}

````` {tab-item} Incomplete
```` {list-table}
:header-rows: 1

* - 
  - Best-Case
  - Average-Case
  - Worst-Case
* - Selection Sort
  - 
  - 
  - 
* - Insertion Sort
  - 
  - 
  - 

````
`````
````` {tab-item} Complete
```` {list-table}
:header-rows: 1

* - 
  - Best-Case
  - Average-Case
  - Worst-Case
* - Selection Sort
  - $O(n^2)$
  - $O(n^2)$
  - $O(n^2)$
* - Insertion Sort
  - $O(n)$
  - $O(n^2)$
  - $O(n^2)$
````
`````

``````
```````
``````````
