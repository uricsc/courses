# Mergesort

`````````` {div} full-width
```` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/4VqmGXwpLqc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR

Merge sort is a popular sorting algorithm that works by recursively dividing an array into two halves until each half contains only one element, and then merging the two halves in a sorted manner. The algorithm divides the array in half, sorts each half recursively, and then merges the two sorted halves.

The key idea behind merge sort is that it's easier to sort two smaller sorted arrays than to sort one large unsorted array. As a result, merge sort can achieve a better time complexity than some other sorting algorithms, such as bubble sort or insertion sort.

The time complexity of merge sort is $O(n\ log\ n)$ in the worst case, where n is the number of elements to be sorted. This makes merge sort one of the most efficient comparison-based sorting algorithms, and it's widely used in practice.
```
``` {card} Other Recordings

- [2.7.2. Merge Sort Algorithm](https://youtu.be/mB5HXBb_HY8) : 20:22
- [2.7.3 MergeSort in-depth Analysis](https://youtu.be/ak-pz7tS5DE) : 13:27

- [Why Is Merge Sort O(n * log(n))? The Really Really Long Answer](https://youtu.be/alJswNJ4P3U) : 36:49
```
````
``````````

## [Divide & Conquer](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/divide-and-conquer-algorithms)

`````````` {div} full-width
``````` {card}
``` {figure} https://codeyz.com/wp-content/uploads/2020/07/image-1-792x512.png
```
``` {card}

<b class="orange">Divide</b> the problem into <u>smaller</u> subproblems

<b class="orange">Conquer</b> recursively
- ... each subproblem

<b class="orange">Combine</b> Solutions

```

````` {card} Example

- sorting with insertion sort is $n^2$   
- we can divide the array into two halves and sort them separately 

```` {dropdown} ![image](https://www.kirupa.com/sorts/images/mergesort_1st_div_300.png)
``` {figure} https://algs4.cs.princeton.edu/22mergesort/images/mergesort-overview.png
:width: 100%
```
````

- each subproblem could be sorted in $≈\frac{n^2}{4}$
- sorting both halves will require $≈2\frac{n^2}{4}$ 🤔
- we need an additional operation to combine both solutions

*_Time “reduced” from $≈n^2$ to $≈\frac{n^2}{2}+n$_*

```````
``````````

## [Merge Sort](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/overview-of-merge-sort)

`````````` {div} full-width
````````` {card}

<span class="orange">Divide</span> the array into two halves

- just need to calculate the midpoint

Conquer <span class="orange">Recursively</span> each half

- call Merge Sort on each half (i.e. solve 2 smaller problems)

<span class="orange">Merge</span> Solutions

- after both calls are finished, proceed to *_merge_* the solutions



``````` {tab-set}
`````` {tab-item} pseudocode
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

MergeSort(arr[], lo,  hi)

if (hi <= lo) return;

  // Find the middle point to divide the array into two halves:
  int mid = lo + (hi - lo) / 2;

  // Call mergeSort for first half:
  mergesort(A, lo, mid);

  // Call mergeSort for second half:
  mergesort(A, mid + 1, hi);

  // Merge the two halves sorted in steps 2 and 3:
  merge(A, lo, mid, hi);
```
[Merge Sort: pseudocode](https://www.geeksforgeeks.org/merge-sort/)
``````
`````` {tab-item} mergesort
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:
void mergesort(int *A, int n) {
  int *aux = new int[n];  
  r_mergesort(A, aux, 0, n - 1);
  delete[] aux;
}
```
``````
`````` {tab-item} r_mergesort

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:
void r_mergesort(int *A, int *aux, int lo,int hi) {
  
    //basecase(single element or empty list)
  if (hi <= lo) return;

  //divide
  int mid = lo + (hi - lo) / 2;

  //recursively sort halves  
  r_mergesort(A, aux, lo, mid);
  r_mergesort(A, aux, mid + 1, hi);

  //merge results 
  merge(A, aux, lo, mid, hi);
}
```

``````
`````` {tab-item} merge
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:
void merge (int *A, int *aux, int lo, int mid,int hi) {

    // copy array
    std::memcpy(aux + lo, A + lo, (hi - lo + 1 * sizeof(A)));
    
    // merge 
    int i = lo, j = mid + 1;

    for (int k = lo; k <= hi; k++) {  

        if (i > mid) A[k]=aux[j++];  

        else if (j > hi) A[k] = aux[i++];

        else if(aux[j] < aux[i]) A[k] = aux[j++];

        else A[k] = aux[i++];
    }
}
```
``````
```````
````` {grid}
````  {grid-item-card}
:columns: 7
``` {figure} https://algs4.cs.princeton.edu/22mergesort/images/merge.png
:width: 100%
```
````
````  {grid-item-card}
:columns: 5
``` {figure} https://algs4.cs.princeton.edu/22mergesort/images/mergesortTD-bars.png
:width: 300
````
`````
`````````

``````````

### [Divide & Conquer](https://www.kirupa.com/sorts/mergesort.htm)

`````````` {div} full-width
````````` {card}
**Consider how this breaks out...**
``````` {tab-set} 
````` {tab-item} Unsorted
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/mergesort_numbers_300.png
:width: 100%
Collection Unsorted
```
````
`````
````` {tab-item} Divide
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/mergesort_1st_div_300.png
:width: 100%
First Division
```
````
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/mergesort_2nd_div_300.png
:width: 100%
Second Division
```
````
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/mergesort_3rd_div_300.png
:width: 100%
Third Division
```
````
`````
````` {tab-item} Conquer Setup
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/merge_setup_300.png
:width: 100%
```
````
`````
````` {tab-item} First Row
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/merge_step_one_300.png
:width: 100%
Step 1
```
````
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/merge_step_two_300.png
:width: 100%
Step 2
```
````
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/merge_step_first_row_300.png
:width: 100%
Completed First Row
```
````
`````
````` {tab-item} Second Row
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/merge_step_2nd_row_3_300.png
:width: 100%
Step 3
```
````
`````
````` {tab-item} Third Row
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/merge_step_3rd_row_1_300.png
:width: 100%
Step 1
```
````
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/merge_step_3rd_row_2.png
:width: 100%
Step 2
```
````
`````
````` {tab-item} Sorted
```` {card}
``` {figure} https://www.kirupa.com/sorts/images/everything_sorted_merge_300.png
:width: 100%
Sort Complete
```
````
`````
````` {tab-item} Try It!
```` {card}
<iframe src="https://opendsa-server.cs.vt.edu/embed/mergesortAV" height="650" width="100%" scrolling="no"></iframe>

- Add the collection values to _Your Values_
  - Collection values : 5, 12, 4, 1, 2, 8, 2, 6, 10
- Change the _List Size_ to _9_
- Press <kbd>run</kbd> and click through the steps...

````
`````
`````````
``````````

### [Merging two sorted arrays](https://www.geeksforgeeks.org/merge-two-sorted-arrays/)

`````````` {div} full-width
```` {card}

``` {figure} https://www.baeldung.com/wp-content/uploads/2019/12/Merge-Sorted-Arrays.png
:width: 100%
```

*_A secondary array is necessary_*

*_to guarantee a_* **[lineartime](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/linear-time-merging)** *_operation_*

``` {admonition} Visualize...
:class: dropdown tip
<iframe src="https://opendsa-server.cs.vt.edu/embed/mergesortCON" height="300" width="100%"></iframe>
```

````
``````````

### [Analysis (recurrence)](https://www.khanacademy.org/computing/computer-science/algorithms/merge-sort/a/analysis-of-merge-sort)

`````````` {div} full-width
```` {list-table}
:header-rows: 1

* - 
  - Worst Case
  - Average Case
  - Best Case
* - Time Complexity
  - $\Theta(n\ log\ n)$
  - $\Theta(n\ log\ n)$
  - $\Theta(n\ log\ n)$
````

```` {card} Breakdown (generalization)
A merge sort consists of several passes over the input.  

$1^{st}$ Pass: merges segments of size 1  
$2^{nd}$ Pass: merges segments of size 2  
$i^{th}$ Pass: merges segments of size $2^{i-1}$.  
Total number of passes: $log\ n$  

As merge showed, we can merge two sorted segments in linear time, which means that each pass takes $O(n)$ time. 
Since there are $log\ n$ passes, the total computing time is $\Theta(n\ log\ n)$, or expressed as:

$$T(n) = 2T(\frac{n}{2}) + \Theta(n)$$

````
``````````

### [Recursion Tree (trace)](https://youtu.be/C4JjXc0htp0)

`````````` {div} full-width
````````` {card}

``` {figure} https://www.kirupa.com/sorts/images/running_complexity_300.png
:width: 100%

```

```` {admonition} Traversal Order
:class: dropdown tip
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20220722205737/MergeSortTutorial.png
:width: 300
```
````
```` {admonition} Try It!
:class: dropdown tip
<iframe src="https://opendsa-server.cs.vt.edu/embed/MergeSortAnalysisCON" height="200" width="100%"></iframe>
````

```` {card}
Total time for $mergeSort$ is: the sum of the merging times for all the levels  
- If there are $l$ levels in the tree, then the total merging time is $l * cn$  
- Where $l$ is the number of subproblem levels until subproblems reach size $n$  
For total time, we end up with:

$$cn(log\ n + 1)$$

- Discard the low-order term (constant) and the coefficient  

$$\Theta(n\ log\ n)$$
````

`````````
``````````

### [Sorting Visualizer](https://clementmihailescu.github.io/Sorting-Visualizer/)

`````````` {div} full-width
````` {card}
<iframe src="https://www.sortvisualizer.com/mergesort/" height="650" width="100%"></iframe>
`````
``````````

### Comments on Merge Sort

`````````` {div} full-width
``````` {grid}
``````  {grid-item-card}
``` {admonition} Advantages
:class: seealso

- relatively efficient for sorting large datasets
- stable sort : the order of elements with equal values is preserved during the sort
- easy to implement
- useful for external sorting
- requires relatively few additional resources (such as memory)
``````
``````  {grid-item-card}
``` {admonition} Disadvantages
:class: danger

- slower compared to the other sort algorithms for smaller tasks
- requires an additional memory space of 0(n) for the temporary array
- regardless of sort status, goes through whole process
- requires more code to implement
```
``````
```````
``````````

### Example

`````````` {div} full-width
```` {card} Think about reversing an array or string
``` {dropdown} solution 1 
**Use an additional array of equal size**

- what is the required extra memory?
```
``` {dropdown} solution 2
**Exchange first and last and work recursively on the inner part**

  - can do it iteratively as well
  - what is the required extra memory?
```
````
``````````

## [In-place sorting](https://www.geeksforgeeks.org/in-place-algorithm/)

`````````` {div} full-width
``````` {card}
``` {card}

> An algorithm does not use extra space for manipulating the input but may require a small though non-constant extra space for its operation. Usually, this space is $O(log\ n)$, though sometimes anything in $O(n)$ (Smaller than linear) is allowed.
>
> -- [Geek for Geeks](https://www.geeksforgeeks.org/in-place-algorithm/)

```

`````` {grid}
`````  {grid-item-card}
:columns: 6
**[selection sort](https://www.geeksforgeeks.org/selection-sort/)**
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:
void selectionSort(int arr[], int n)
{
    int i, j, min_idx;
 
    // One by one move boundary of unsorted subarray
    for (i = 0; i < n-1; i++) {
       
        // Find the minimum element in unsorted 
        // array
        min_idx = i;
        for (j = i+1; j < n; j++)
            
            if (arr[j] < arr[min_idx]) min_idx = j;
 
        // Swap the found minimum element with 
        // the first element
        if(min_idx!=i)
            swap(&arr[min_idx], &arr[i]);
    }
}
```
``` {dropdown} In-place?
Yes, it does not require extra space.
```
`````
````` {grid-item-card}
:columns: 6

**[insertion sort](https://www.geeksforgeeks.org/insertion-sort/)**

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:
void insertionSort(int arr[], int n) 
{ 
    int i, key, j; 
    
    for (i = 1; i < n; i++) 
    { 
        key = arr[i]; 
        j = i - 1; 
  
        // Move elements of arr[0..i-1], 
        // greater than key, to one position 
        // ahead of their current position
        while (j >= 0 && arr[j] > key)
        { 
            arr[j + 1] = arr[j]; 
            j = j - 1; 
        } 
        arr[j + 1] = key; 
    } 
} 
```
``` {dropdown} In-place?
Yes, it does not require extra space.
```
`````
``````

```````
``````````

## Stable Sorting

`````````` {div} full-width
````````` {card}

```` {admonition} Stability
A sorting algorithm is *_stable_* if it preserves the order of equal elements

Consider sorting (in ascending order) a list $A$ into a sorted list $B$. Let $f(i)$ be the index of element $A[i]$ in $B$. The sorting algorithm is stable if:

for any pair $(i,j)$ such that $A[i] = A[j]$ and $i < j$, then $f(i) < f(j)$

``` {figure} https://cdn.emre.me/2019-08-31-stable-unstable.png
:width: 50%
```
````
```````` {tab-set}
```````  {tab-item} Stable?
`````` {admonition} Stable?
:class: tip

````` {grid}
```` {grid-item} 
``` {figure} imgs/mergesort/11_s20_1.png
:width: 375px
```
unsorted
````
```` {grid-item} 
``` {figure} imgs/mergesort/11_s20_2.png
:width: 375px
```
sorted
````
`````
``` {dropdown} Stable?
<b class="red">NOT STABLE</b>
```
``````
```````
``````` {tab-item} Stable?
`````` {admonition} How about now?
:class: tip
````` {grid}
```` {grid-item} 
``` {figure} imgs/mergesort/11_s20_1.png
:width: 400px
```
unsorted
````
```` {grid-item} 
``` {figure} imgs/mergesort/11_s20_3.png
:width: 400px
```
sorted
````
`````
``` {dropdown} Stable?
<b class="green">STABLE</b>
```
``````
```````
````````
`````````
``````````

### Stability

`````````` {div} full-width
````` {card}

``` {dropdown} Is selection sort stable?
Selection sort algorithm picks the minimum and swaps it with the element at current position.

Suppose the array is:

$$[5,\ 2,\ 3,\ 8,\ 4,\ 5,\ 6]$$

$$[5_a,\ 3,\ 4,\ 5_b,\ 2,\ 6,\ 8]$$

- After iteration 1:
  - 2 will be swapped with the element in 1st position:

- So our array becomes:

$$[2,\ 3,\ 4,\ 5_b,\ 5_a,\ 6,\ 8]$$

- Since now our array is in sorted order and we clearly see that $5_a$ comes before $5_b$ in initial array but not in the sorted array.

- Therefore, selection sort is not stable.

<b class="red">NOT</b> STABLE
```
- long distance swaps
- try: 5 2 3 8 4 5 6

``` {dropdown} Is insertion sort stable?
<b class="green">STABLE</b> 
```
- equal items never pass each other (depends on correct implementation)

`````
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
  - $\Theta(n^2)$
  - $\Theta(n^2)$
  - $\Theta(n^2)$
  - No
  - Yes
* - Insertion Sort
  - $\Theta(n)$
  - $\Theta(n^2)$
  - $\Theta(n^2)$
  - Yes
  - Yes
* - Merge Sort
  - $\Theta(n\ log\ n)$
  - $\Theta(n\ log\ n)$
  - $\Theta(n\ log\ n)$
  - Yes
  - No
```
`````
``````
```````
``````````

## Test Yourself...

````` {div} full-width
``` {admonition} Mergesort Merging Proficiency Exercise
:class: dropdown danger
<iframe src="https://opendsa-server.cs.vt.edu/embed/MergesortMergePRO" height="650" width="100%" scrolling="no"></iframe>
```
``` {admonition} Mergesort Proficiency Exercise
:class: dropdown danger
<iframe src="https://opendsa-server.cs.vt.edu/embed/mergesortPRO" height="950" width="100%" scrolling="no"></iframe>
```
`````
