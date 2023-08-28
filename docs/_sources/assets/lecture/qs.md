# Quicksort

`````````` {div} full-width
```` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/Hoixgm4-P4M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
``` {image} https://gifimage.net/wp-content/uploads/2018/04/quick-sort-gif-5.gif
:align: center
```
````
``````````

## [Quick Sort](https://www.geeksforgeeks.org/quick-sort/)

`````````` {div} full-width
````` {card}

<b class="orange">Divide</b> the array into **two** partitions (subarrays)

- need to pick a _pivot_ and rearrange the elements into two  partitions

Conquer <b class="orange">Recursively</b> each half

- call Quick Sort on each partition (i.e. solve 2 smaller problems)

<b class="orange">Combine</b> Solutions

- there is no need to combine the solutions

``````````

### Partition

`````````` {div} full-width

``` {figure} https://www.baeldung.com/wp-content/uploads/sites/4/2021/06/Quicksort-891x1024-1.png
```

#### [Partition: algorithm](https://medium.com/@vladitech/partition-algorithm-basics-of-quick-sort-pivoting-286f97f251f1)

`````````` {div} full-width
````` {dropdown} ![image](https://blogger.googleusercontent.com/img/a/AVvXsEj_5g_ulJTm7AnqNrfjUt3zYDUi0qf6eepoRqnDvvUhBKIf_vdqP-982F2zX_xV3k1148k8oozojzlBGhKUPrbUshDZs9VMCT0F-iQC8NmV68gDceOu1AIEkl520KEmXgaPXb_R3PdtHNAHhfXHfHDWjQSIpFoKPqC2MIz1Mv50u1XVXI8Gpe2AXu9_3g=s16000)

<iframe width="100%" height="300" src="https://opendsa-server.cs.vt.edu/embed/quicksortCON"></iframe>

`````
``````````

### Implementation

`````````` {div} full-width
````````` {card}

``````` {tab-set}
`````` {tab-item} quicksort
```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 

void quicksort(int *A, int n, int m)              
{
    // shuffle the array  
    std::random_shuffle(A, A + n);
    
    // call recursive quicksort  
    r_quicksort(A, 0, n - 1);
}
```
``````
`````` {tab-item} r_quicksort
```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 

void r_quicksort(int *A,int lo, int  hi)                                           
{
    if (hi <= lo) return;
    
    int p = partition(A, lo, hi);  
    
    r_quicksort(A, lo, p - 1);  
    
    r_quicksort(A, p + 1, hi);
}
```
``````
`````` {tab-item} partition
```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 

int partition (int *A, int lo, int hi)                      
{
    int i = lo;
    int j = hi + 1;  
    while (1) {
      
        // while A[i] < pivot, increase i 
        while (A[++i] < A[lo])
            if (i == hi) break;

        // while A[i] > pivot, decrease j 
        while (A[lo] < A[--j])
            
            if (j == lo) break;
          
            // if i and j cross exit theloop
            if(i >= j) break;
            
            // swap A[i] and A[j]
            std::swap(A[i], A[j]);
    }
    // swap the pivot with A[j]  
    std::swap(A[lo], A[j]);

    //return pivot's position
    return j;
}

```
``````
```````
``` {admonition} Visualize
:class: dropdown tip
<iframe width="100%" height="500" src="https://opendsa-server.cs.vt.edu/embed/quicksortAV"></iframe>
```
`````````
``````````

### [Analysis of Quick Sort](https://www.khanacademy.org/computing/computer-science/algorithms/quick-sort/a/analysis-of-quicksort)

`````````` {div} full-width
`````` {admonition} [Worst-Case](https://youtu.be/4nVbJV5pZa8?t=80)

````` {card}

```` {dropdown} ![image](https://cdn.kastatic.org/ka-perseus-images/7da2ac32779bef669a6f05decb62f219a9132158.png)
````

$$
c \{ n + (n-1) + (n-2) + (n-3) + ... 1 \} \\
c * \frac{n(n+1)}{2} \\
= \Theta(n^2)
$$

`````

**input sorted, reverse order, equal elements**

$$\begin {align}
T(n) &= T(n - 1) + T(0) + \Theta(n) \\
&= T(n - 1) + \Theta(1) + \Theta(n) \\
&= T(n - 1) + \Theta(n) \\
&= \dots \\
&= \Theta(n^2) \\
\end {align}$$

can shuffle or [randomize](https://youtu.be/HY64dw_Af94) the array (to avoid the worst-case)

``````

````` {admonition} [Best-Case](https://youtu.be/4nVbJV5pZa8?t=374)

```` {dropdown} ![image](https://cdn.kastatic.org/ka-perseus-images/21cd0d70813845d67fbb11496458214f90ad7cb8.png)
````

- pivot partitions array evenly (almost never happens)

$$ \begin {align}
T(n) &= 2T(\frac{n}{2}) + \Theta(n) \\
&= \dots \\
&=\ \Theta(n\ log\ n)
\end {align}$$

`````

````````` {admonition} [Average-Case](https://youtu.be/4nVbJV5pZa8?t=482)

- analysis is more complex

``` {card}
- Consider a 9-to-1 proportional split
- Even a 99-to-1 split yields same running time
- Faster than merge sort in practice (less data movement)
```

$$\begin {align}
T(n) &= T(\frac{n}{10}) + T(\frac{9n}{10}) + \Theta(n) \\
&= \dots \\
&= \Theta(n\ log\ n) \\
\end {align}$$

```` {dropdown} ![image](https://cdn-images-1.medium.com/max/600/1*h6C8WodiZvZ04CwgOKOgBA.png)

````

Add all $cn$ from side of tree with greatest depth (right subtree):

$$
= cn * log_{\frac{10}{9}}\ n \\
= \Theta(n\ log\ n) \\
$$
`````````

``````````

### Comments on Quick Sort

`````````` {div} full-width
`````` {card}

``` {card} Properties
- it is **in-place** but not **stable**
- benefits substantially from code tuning
```

``` {card} Improvements
use insertion sort for small arrays
- avoid overhead on small instances (~10 elements)
median of 3 elements
- estimate true median by inspecting 3 random elements
[three-way partitioning](https://www.toptal.com/developers/sorting-algorithms/quick-sort-3-way)
- create three partitions $ \le pivot$, $== pivot$, $ \ge pivot$
```

``````
``````````

## Sorting Algorithms

`````````` {div} full-width
``````` {card}
`````` {tab-set}
````` {tab-item} incomplete
``` {list-table}
:header-rows: 1

* - 
  - Best-Case
  - Average-Case
  - Worst-Case
  - Stable
  - In-place
* - Selection Sort
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
* - Insertion Sort
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
* - Merge Sort
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
* - Quick Sort
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
  - <b contenteditable></b>
```
`````
````` {tab-item} complete
``` {list-table}
:header-rows: 1

* - 
  - Best-Case
  - Average-Case
  - Worst-Case
  - Stable
  - In-place
* - Selection Sort
  - $n^2$
  - $n^2$
  - $n^2$
  - No
  - Yes
* - Insertion Sort
  - $n$
  - $n^2$
  - $n^2$
  - Yes
  - Yes
* - Merge Sort
  - $n\ log\ n$
  - $n\ log\ n$
  - $n\ log\ n$
  - Yes
  - No
* - Quick Sort
  - $n\ log\ n$
  - $n\ log\ n$
  - $n^2$
  - No
  - Yes
```
`````
``````
```````
``````````

## Empirical Analysis

`````````` {div} full-width
```` {card}

``` {figure} imgs/12_s16.png
```

[https://www.cs.princeton.edu/courses/archive/spring18/cos226/lectures/23Quicksort.pdf](https://www.cs.princeton.edu/courses/archive/spring18/cos226/lectures/23Quicksort.pdf)

````
``````````
