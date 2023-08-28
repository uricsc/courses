# Big-O

`````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/__vX2sjlpXU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
Asymptotic analysis is a mathematical method used to describe the behavior of data structures and algorithms as the input size approaches infinity. It is a way of analyzing the computational cost of algorithms in terms of their efficiency and scalability.

In asymptotic analysis, we typically focus on the worst-case scenario of an algorithm, which is the scenario in which the algorithm takes the longest time to execute. We use big-O notation to express the upper bound of the computational cost in terms of the input size.

For example, if we have an algorithm that takes $2n^2 + 3n + 1$ operations to complete a task, we can express its time complexity as $O(n^2)$. This means that as the input size grows, the computational cost of the algorithm will grow no faster than the quadratic function of n.

Asymptotic analysis is important in data structures and algorithms because it helps us understand how efficient and scalable they are. By analyzing the time and space complexity of an algorithm, we can make informed decisions about which algorithms and data structures to use in different scenarios.

For example, if we have a large dataset, we may want to choose an algorithm with a lower time complexity even if it has a higher space complexity. Conversely, if we have limited memory resources, we may choose a data structure with lower space complexity even if it has a higher time complexity.

Overall, asymptotic analysis is a powerful tool for analyzing the efficiency and scalability of data structures and algorithms, and is essential for developing high-performance software systems.
```

``` {card} Additional Resources
- [Big Oh(O) vs Big Omega(Ω) vs Big Theta(θ) notations | Asymptotic Analysis of Algorithms with Example | Simple Snippets](https://youtu.be/1tfdr1Iv6JA) : 28:49

```
`````

```` {card}
``` {image} https://big-o.io/assets/graph_animated.svg
```

``` {image} https://era86.github.io/assets/images/posts/big-o-chart.png
```
````
``````````

## The story so far...

`````````` {div} full-width
`````` {grid}

``` {grid-item-card}
:columns: 6
Can measure actual runtime to compare algorithms  
- however, runtime is noisy (highly sensitive to hardware/software and implementation details)
```

``` {grid-item-card}
:columns: 6
Can count instructions to compare algorithms  
- can define $T(n)$, which depends on the input size  
- for large inputs, our focus should be on the dominant terms of $T(n)$
```
``````
``````````

## Inline Math

``````````` {div} full-width
`````````` {card}

````````` {tab-set}
````````  {tab-item} Sequence & Series
`````` {grid}
````` {grid-item-card}
:columns: 6
[**Sequence**](https://www.khanacademy.org/math/algebra/x2f8bb11595b61c86:sequences)  

> also known as a progression, is a successive arrangement of numbers in an order according to some specific rules
> 
> -- [gfg](https://www.geeksforgeeks.org/sequences-and-series-formulas/)

- Depending upon the number of terms in a sequence, it is classified into two types, namely a finite sequence and an infinite sequence.

examples
- finite arithmetic sequence: $3, 5, 7, 9, 11$  
- infinite geometric sequence: $2, 4, 8, 16, …… $

`````
````` {grid-item-card}
:columns: 6
[**Series**](https://www.khanacademy.org/math/precalculus/x9e81a4f98389efdf:series)

> formed by adding the elements of a sequence
> 
> -- [gfg](https://www.geeksforgeeks.org/sequences-and-series-formulas/)

- Depending on whether the sequence is finite or infinite, the series can be either finite or infinite.

examples  
- finite arithmetic series: $3 + 5 + 7 + 9 + 11$
- infinite geometric series: $2 + 4 + 8 + 16 + …… $ 
`````
``````
````````

````````  {tab-item} Arithmetic
`````` {admonition} [Arithmetic Sequence and Series](https://www.khanacademy.org/math/precalculus/x9e81a4f98389efdf:series/x9e81a4f98389efdf:arith-series/v/sum-of-arithmetic-sequence-arithmetic-series)
:class: tip
- where each term of the sequence is formed either by adding or subtracting a common term from the preceding number

$2, 5, 8, 11, 14,…$

``` {dropdown} common difference?
$3$
```
``````
````````
````````  {tab-item} Geometric
`````` {admonition} [Geometric Sequence and Series](https://www.khanacademy.org/math/precalculus/x9e81a4f98389efdf:series/x9e81a4f98389efdf:geo-series-notation/v/sigma-notation-sum)
:class: tip
- where each term of the sequence is formed either by multiplying or dividing a common term with the preceding number

$1, 5, 25, 125, 625,…$

``` {dropdown} common ratio?
$5$
```
``````
````````
````````  {tab-item} Harmonic
`````` {admonition} [Harmonic Sequence and Series](https://www.khanacademy.org/math/ap-calculus-bc/bc-series-new/bc-10-5/v/harmonic-and-p-series)
:class: tip
- where each term of the sequence is the reciprocal of the element of an arithmetic sequence

$2, 5, 8, 11, 14,…$

``` {dropdown} harmonic sequence?
$1/2, 1/5, 1/8, 1/11, 1/14,…$
```
``````
````````
````````  {tab-item} Fibonacci
`````` {admonition} Fibonacci Numbers
:class: tip
- a sequence of numbers where each term of the sequence is formed by adding its preceding two numbers, and the first two terms of the sequence are 0 and 1

$$ 
\begin {align}
F_0 & = 0 \\
F_1 & = 1 \\\
F_2 & = F_1 - F_0 \\\
& = 1 + 0 \\\
& = 1 \\\
F_3 & = F_2 + F_1 \\\
& = 1 + 1 \\\
& = 2 \\
\end {align}
$$

``` {dropdown} $F_n$ ?
$F_n = F_{n - 1} + F_{n - 2}$
```
``````
````````
````````  {tab-item} Sigma Notation
```` {card} 
:link: https://www.khanacademy.org/math/precalculus/x9e81a4f98389efdf:series/x9e81a4f98389efdf:geo-series-notation/v/sigma-notation-sum
``` {figure} https://i.pinimg.com/736x/df/35/19/df351990b77146392f2c8b3b0ab9681c--algebra--math-resources.jpg
sigma notation
```
````
````````
````````  {tab-item} Sigma Ex 1
[Summation of the first N Integers : $\sum_{i = 1}^n i$](https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3/html/Summations.html)

<iframe src="https://opendsa-server.cs.vt.edu/embed/SummationOneToNCON" height="450" width="100%"></iframe>

````````
````````  {tab-item} Sigma Ex 2
[Summation Two Power : $\sum_{i = 0}^{n} 2^i$](https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3/html/Summations.html)

<iframe src="https://opendsa-server.cs.vt.edu/embed/SummationTwoPowerICON" height="450" width="100%"></iframe>

````````
`````````
``````````
``````````

```{margin} Desmos
[Desmos : Graphing Calculator](https://www.desmos.com/calculator/7vmsklh8o9)  
Used to create the images below...
```
``````````
```````````

## Comparing Algorithms

`````````` {div} full-width
`````````  {card}
````````   {tab-set}
```````    {tab-item} Compare two...
`````` {card} $Are\ these\ the\ same?$

$$\color{green}{T(n) = 2n} \ \ \ \ \ \ \ \ \color{orange}{T(n) = 25n}$$

````` {grid}

```` {grid-item-card}
:columns: 6
:text-align: center

<iframe src="https://www.desmos.com/calculator/61er8lxhiy?embed" width="450" height="400" style="border: 1px solid #ccc" frameborder=0></iframe>
Smaller datasets...
````

````{grid-item-card}
:columns: 6
:text-align: center

<iframe src="https://www.desmos.com/calculator/amlwrfh9sd?embed" width="450" height="400" style="border: 1px solid #ccc" frameborder=0></iframe>
Larger datasets...
````

`````

$$Why\ / Why\ Not?$$

````` {admonition} Explantion
:class: dropdown, important
Looking closely at the graphs, the left graph has low input ($n$) values...when we look to the right and reveal the graph for high input ($n$) values, the behavior of the lines on the graph remains the same. Therefore the algorithms themselves are the same...
`````

``````
```````
```````    {tab-item} Compare three...
`````` {card} $Are\ these\ the\ same?$

$$\color{green}{T(n) = 2n} \ \ \ \ \ \ \ \ \color{orange}{T(n) = 25n} \ \ \ \ \ \ \ \ \color{blue}{T(n) = n^2}$$

````` {grid}

```` {grid-item-card}
:columns: 12 12 4 4
:text-align: center

<iframe src="https://www.desmos.com/calculator/z8ay5kpdtl?embed" width="250" height="400" style="border: 1px solid #ccc" frameborder=0></iframe>
Smaller datasets...
````

````{grid-item-card}
:columns: 12 12 4 4
:text-align: center

<iframe src="https://www.desmos.com/calculator/8zgxexrima?embed" width="250" height="400" style="border: 1px solid #ccc" frameborder=0></iframe>
Larger datasets...
````

````{grid-item-card}
:columns: 12 12 4 4
:text-align: center

<iframe src="https://www.desmos.com/calculator/eq5m3nq2zq?embed" width="250" height="400" style="border: 1px solid #ccc" frameborder=0></iframe>
Largest datasets...
````

`````

$$Why\ / Why\ Not?$$

````` {admonition} Explantion
:class: dropdown, important
Looking closely at the graphs, the left graph has low input ($n$) values...when we look to the right and reveal the graph for high input ($n$) values, the behavior of the lines on the graph remains the same. Therefore the algorithms themselves are the same...
`````
``````
```````
```````    {tab-item} Compare two more...
`````` {card} $Are\ these\ the\ same?$

$$\color{green}{T(n) = 1000n + 500} \ \ \ \ \ \ \ \ \color{orange}{T(n) = n^2}$$

````` {grid}

```` {grid-item-card}
:columns: 12 12 6 6
:text-align: center

<iframe src="https://www.desmos.com/calculator/rcyaujqwho?embed" width="450" height="200" style="border: 1px solid #ccc" frameborder=0></iframe>
Smaller datasets...
````

````{grid-item-card}
:columns: 12 12 6 6
:text-align: center

<iframe src="https://www.desmos.com/calculator/c1bcn6r7wx?embed" width="450" height="200" style="border: 1px solid #ccc" frameborder=0></iframe>
Larger datasets...
````

`````

````` {grid}

```` {grid-item-card}
:columns: 12 12 6 6
:text-align: center

<iframe src="https://www.desmos.com/calculator/ifozextlng?embed" width="450" height="200" style="border: 1px solid #ccc" frameborder=0></iframe>
Larger datasets...
````

````{grid-item-card}
:columns: 12 12 6 6
:text-align: center

<iframe src="https://www.desmos.com/calculator/4ii7sbfoom?embed" width="450" height="200" style="border: 1px solid #ccc" frameborder=0></iframe>
"Big Data"...
````

`````

$$Why\ / Why\ Not?$$

``````

```````
``````` {tab-item} Bottom line...
``` {card}
We are trying to compare $T(n)$ functions, but...
- we also care about large values of $n$  
```

``` {card}
Can we properly define $\le$ for functions?
- we can group functions into $sets$ and make our lives easier
```
``````` 
````````
`````````
``````````

## [Asymptotic Analysis](https://www.geeksforgeeks.org/types-of-asymptotic-notations-in-complexity-analysis-of-algorithms/?ref=rp)

`````````` {div} full-width
``` {card}
- refers to the study of an algorithm as the input size “gets big” or reaches a limit (in the calculus sense)
```
``````````

### Growth rate

`````````` {div} full-width
````` {card}

``` {card}
- rate at which the cost of an algorithm grows as the size of its input grows
```

```` {grid}
``` {grid-item-card}
$$c_1n$$
```
``` {grid-item-card}
$$c_2n^2$$
```
````
`````
``````````

### Common sets of functions

`````````` {div} full-width
````` {grid}
```` {grid-item-card}
``` {image} imgs/04_s11.png
```
````
```` {grid-item-card}
Algorithm $A$ is better than Algorithm $B$ if... 

- for large values of $n$, $TA(n)$ grows slower than $TB(n)$

_Note: Faster growth rate...slower algorithm..._

````

`````
``````````

#### Examples

````` {div} full-width
``` {list-table}
:header-rows: 1

* - order of growth
  - name
  - typical code framework
  - description
  - example
* - $$1$$
  - **constant**
  - $$a = b + c;$$
  - statement
  - add two numbers
* - $$log\ n$$
  - **logarithmic**
  - $$while\ (n > 1)\\ \{ \ \ \ \ \ \ \ \dots \ \ \ \ \ \ \ \}$$
  - divide in half
  - binary search
* - $$n$$
  - **linear**
  - $$for\ (int\ i\ = 0; i \lt n; i++)\\ \{ \ \ \ \ \ \ \ \dots \ \ \ \ \ \ \ \}$$
  - single loop
  - find the maximum
* - $$n\ log\ n$$
  - **linearithmic**
  - $$see\ mergesort$$
  - divide & conquer
  - mergesort
* - $$n^2$$
  - **quadratic**
  - $$for\ (int\ i\ = 0; i \lt n; i++)\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \\ for\ (int\ j\ = 0; j \lt n; j++)\ \ \ \ \ \ \ \ \ \\ \ \ \ \ \ \ \ \ \{ \ \ \ \ \ \ \ \dots \ \ \ \ \ \ \ \}$$
  - double loop
  - check all pairs
* - $$n^3$$
  - **cubic**
  - $$for\ (int\ i\ = 0; i \lt n; i++)\ \ \ \ \ \ \ \ \ \ \ \ \ \ \\ for\ (int\ j\ = 0; j \lt n; j++)\ \ \ \ \ \ \ \ \ \\ \ \ \ \  for\ (int\ k\ = 0; k \lt n; k++)\\ \{ \ \ \ \ \ \ \ \dots \ \ \ \ \ \ \ \}$$
  - double loop
  - check all pairs
* - $$2^n$$
  - **exponential**
  - $$see\ combinatorial\ search$$
  - exhaustive search
  - check all subsets
```
`````

### Asymptotic Bounds

`````````` {div} full-width
`````````  {card}
````````   {tab-set}
```````    {tab-item} Defined
Asymptotic bounds are a way of describing the behavior of an algorithm as the input size approaches infinity. They are used to analyze the time and space complexity of algorithms, and are expressed in terms of upper and lower bounds.

The most commonly used asymptotic bounds are Big-O notation, Omega notation, and Theta notation.

- **Big-O** notation is an upper bound on the growth rate of an algorithm. It describes the worst-case scenario of an algorithm's time complexity.
  - Ex : if an algorithm has a time complexity of $O(n^2)$, it means that the running time of the algorithm grows no faster than $n^2$.

- **Big-Omega** notation is a lower bound on the growth rate of an algorithm. It describes the best-case scenario of an algorithm's time complexity.
  - Ex. if an algorithm has a time complexity of $\Omega(n)$, it means that the running time of the algorithm grows at least as fast as $n$.

- **Theta** notation provides both an upper and lower bound on the growth rate of an algorithm. It describes the tight bound on the growth rate of an algorithm.
  - Ex. if an algorithm has a time complexity of $\Theta(n^2)$, it means that the running time of the algorithm grows exactly as fast as $n^2$.

Asymptotic bounds are useful because they allow us to compare the efficiency of different algorithms and to choose the most appropriate one for a given task.
```````
```````    {tab-item} Big-O
```` {admonition} Definition

``` {figure} imgs/04_s13.png
:width: 90%
```

``` {card} Translation
$T$ of $n$ is upper bounded by $F$ of $n$ if and only if $T$ of $n$ is less than or equal to some constant $C$ times $F$ of $n$ the function we chose to bound with for all $N$ greater than the initial $n$ or and not
```

``` {card} Examples
$$\begin{align}
7n - 2 & = O(n) \\
20n^3 + 10n\ log\ n + 5 & = O(n^3) \\
3\ log\ n + log\ log\ n & = O(log\ n) \\
2^{100} & = O(1)
\end{align}$$
```

````

[Miscellaneous Notations](https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3/html/MiscMath.html)

```````
```````    {tab-item} Big-Omega
```` {admonition} Definition
``` {figure} imgs/04_s15.png
:width: 90%
```
``` {card} Examples
$$\begin{align}
n^2 + n & = \Omega(n^2) \\
2n^2 & = \Omega(n^2) \\
n^2 + log(n) & = \Omega(n^2) \\
n/4 & = \Omega(n) \\
2n+3 & = \Omega(n) \\
n/100 + log(n) & = \Omega(n) \\
100 & = \Omega(1) \\
log 2000 & = \Omega(1) \\
10^4 & = \Omega(1) \\
\end{align}$$

```
````
[Miscellaneous Notations](https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3/html/MiscMath.html)
```````
```````    {tab-item} Theta
```` {admonition} Definition
``` {figure} imgs/04_s16.png
:width: 90%
```
````
[Miscellaneous Notations](https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3/html/MiscMath.html)
```````

```````    {tab-item} Prove It
```` {card}

$$3\ log\ n\ + log\ log\ n\ = Ω(log\ n)$$
$$3\ log\ n\ + log\ log\ n\ = Θ(log\ n)$$

<br>
<br>
<br>
<br>


``` {admonition} $???$
:class: dropdown danger
The graph of $log\ n$ is a monotonically increasing curve that grows very slowly at first, but then accelerates rapidly as n gets larger. The curve becomes steeper and steeper as n increases, but it never becomes vertical. The curve approaches infinity as $n$ approaches infinity.

The graph of $log\ log\ n$ is also a monotonically increasing curve, but it grows even more slowly than $log\ n$. At first, the curve is almost flat, but it gradually becomes steeper as $n$ increases. The curve approaches infinity as $n$ approaches infinity, but it grows much more slowly than $log\ n$.

Both $log\ n$ and $log\ log\ n$ are commonly used in asymptotic analysis of algorithms to describe their time complexity. For example, an algorithm with time complexity $O(log\ n)$ would be considered more efficient than an algorithm with time complexity $O(log\ log\ n)$ for large values of $n$.
```

<br>
<br>
<br>
<br>

$$T(n)\ is\ O( f(n))\ ⟺\ ∃\  positive\  c, n_0\ ∣\ 0 ≤ T(n)\ ≤ cf(n), ∀n ≥ n_0$$
$$T(n)\ is\ Ω( f(n))\ ⟺\ ∃\  positive\  c, n_0\ ∣\ 0 ≤ cf(n)\ ≤ T(n), ∀n ≥ n_0$$



````

[Miscellaneous Notations](https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3/html/MiscMath.html)

```````


````````
`````````
``````````

### In practice...

```` {div} full-width
``` {card}
“ignore constants and drop lower order terms”
```
````

### Advantages & Disadvantages

``````` {div} full-width
``````  {grid}
`````   {grid-item-card} 

**Advantages**

> - Asymptotic analysis provides a high-level understanding of how an algorithm performs with respect to input size.
>
> - It is a useful tool for comparing the efficiency of different algorithms and selecting the best one for a specific problem.
>
> - It helps in predicting how an algorithm will perform on larger input sizes, which is essential for real-world applications.
>
> - Asymptotic analysis is relatively easy to perform and requires only basic mathematical skills.
>
> -- [gfg](https://www.geeksforgeeks.org/asymptotic-notation-and-analysis-based-on-input-size-of-algorithms/)

`````
`````   {grid-item-card} 

**Disadvantages**

> - Asymptotic analysis does not provide an accurate running time or space usage of an algorithm.
>
> - It assumes that the input size is the only factor that affects an algorithm’s performance, which is not always the case in practice.
> 
> - Asymptotic analysis can sometimes be misleading, as two algorithms with the same asymptotic complexity may have different actual running times or space usage.
>
> - It is not always straightforward to determine the best asymptotic complexity for an algorithm, as there may be trade-offs between time and space complexity.
>
> -- [gfg](https://www.geeksforgeeks.org/asymptotic-notation-and-analysis-based-on-input-size-of-algorithms/)

`````
`````` 
```````


### True or False?

```````` {div} full-width

$$Time\ Complexities:\ {1, log\ n, n, n\ log\ n, n^2, 2^n, n!}$$

``````` {card}

`````` {tab-set}

````` {tab-item} Test yourself

_Click near the center of a cell in each respective column to type your response..._

```` {card}

``` {list-table}
:header-rows: 1

* - 
  - $$Big\ O$$
  - $$Big\ \Omega$$
  - $$\Theta$$
* - $$10^2 + 3000n + 10$$
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
* - $$21\ log\ n$$
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
* - $$500\ log\ n + n^4$$
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
* - $$\sqrt{n} + log\ n^{50}$$
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
* - $$4^n + n^{5000}$$
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
* - $$3000n^3 + n^{3.5}$$
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>
* - $$2^5 +n!$$
  - <span contenteditable></span>
  - <span contenteditable></span>
  - <span contenteditable></span>

```

````

`````

````` {tab-item} Outcomes

```` {card}

``` {list-table}
:header-rows: 1

* - 
  - $$Big\ O$$
  - $$Big\ \Omega$$
  - $$\Theta$$
* - $$10^2 + 3000n + 10$$
  - $$\ge n$$
  - $$\le n$$
  - $$true$$
* - $$21\ log\ n$$
  - $$\ge log\ n$$
  - $$\le log\ n$$
  - $$true$$
* - $$500\ log\ n + n^4$$
  - $$\ge n^2$$
  - $$\le log\ n$$
  - $$false$$
* - $$\sqrt{n} + log\ n^{50}$$
  - $$\ge log\ n$$
  - $$\le log\ n$$
  - $$true$$
* - $$4^n + n^{5000}$$
  - $$\ge 2^n$$
  - $$\le n^2$$
  - $$false$$
* - $$3000n^3 + n^{3.5}$$
  - $$\ge n^2$$
  - $$\le n^2$$
  - $$true$$
* - $$2^5 +n!$$
  - $$\ge n!$$
  - $$\le n!$$
  - $$true$$

```

````

`````

``````

```````

````````

### Asymptotic Performance

`````````` {div} full-width
``` {card}
For $large$ values of $n$, a $Θ(n^2)$ algorithm always beats a $Θ(n^3)$ algorithm

_However, we shouldn’t completely ignore asymptotically slower algorithms_
```
``````````
