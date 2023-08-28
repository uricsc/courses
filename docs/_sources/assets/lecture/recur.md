# Recurrences

`````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/B0NtAFf4bvU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
Recurrence relations are mathematical expressions that define the runtime of algorithms or the space complexity of data structures recursively in terms of their input size. In other words, they describe the time or space complexity of an algorithm by expressing it as a function of the size of the input data.

In the context of data structures and algorithms, recurrences are commonly used to analyze the performance of recursive algorithms such as quicksort, mergesort, and binary search. By using recurrence relations, we can obtain a closed-form expression for the runtime complexity of such algorithms and make predictions about their performance as the input size grows.

Solving recurrence relations can be challenging, and there are several methods to do so, including the substitution method, the recursion tree method, and the master theorem. Understanding and using recurrence relations is an important skill for anyone studying data structures and algorithms, as it enables them to analyze the performance of algorithms and design more efficient solutions.
```

``` {card} Additional Resources

```
`````
<!-- ``` {image} https://cdn-images-1.medium.com/max/1200/1*3Kti9X9KAL0_XCk1cdjbDw.jpeg
:align: center
``` -->
``````````

## Factorial of n (formula)

`````````` {div} full-width
`````` {card} $n!$

> For each positive integer $n$, the quantity **$n$ factorial** denoted $n!$, is defined to be the
product of all the integers from $1$ to $n$:  
>
> $$n! = n · (n − 1) \dots 3·2·1$$  
>
> **Zero factorial**, denoted 0!, is defined to be 1:  
>
> $$0! = 1$$ 
> 
> -- *Discrete Mathematics with Applications, 4th*

````` {card} Examples
Simplify the following expressions:

````` {grid}
```` {grid-item}
:columns: 3
``` {dropdown} $\frac{8!}{7!}$
$$\begin{align}
\frac{8!}{7!} & = \frac{8 * 7!}{7!} \\
& = 8 \\
\end{align}$$
```
````
```` {grid-item}
:columns: 4
``` {dropdown} $\frac{5!}{2!*3!}$
$$\begin{align}
\frac{5!}{2!*3!} & = \frac{5 * 4 * 3!}{2! *3!} \\
& = \frac{5 * 4}{2 * 1} \\
& = \frac{20}{2} \\
& = 10 \\
\end{align}$$
```
````
```` {grid-item}
:columns: 5
``` {dropdown} $\frac{(n)!}{(n - 3)!}$
$$\begin{align}
\frac{(n)!}{(n - 3)!} & = \frac{n * (n - 1) * (n - 2) * (n - 3)!}{(n - 3)!} \\
& = n * (n - 1) * (n - 2) \\
& = n^3 - 3n^2 + 2n
\end{align}$$
```
````
`````

```` {admonition} code
```{code-block} cpp
:lineno-start: 1
:emphasize-lines:
int fact(int num) {

  if (num == 0) return 1;

  else return num * fact(num - 1);   
}
```
[https://www.geeksforgeeks.org/factorial-formula/](https://www.geeksforgeeks.org/factorial-formula/)  
````
``````

```````` {card} Use Cases
```````  {grid}
``````   {grid-item}
:columns: 6
````` {admonition} Permutation
- gives the number of ways to select $r$ elements from $n$ elements when *_order matters_*

$$^nP_r = \frac{n!}{(n – r)!}$$

```` {card} Example
Three different fruits are to be distributed among a group of 10 people. Find the total number of ways this can be possible.

``` {dropdown} $n = 10,\ r = 3 \dots =\ ^{10}P_3$
$$\begin {align}
n = 10,\ r = 3...\ &=\ ^{10}P_3 \\
&= \frac{10!}{(10 – 3)!} \\
&= \frac{10!}{7!} \\ 
&= \frac{10 × 9 × 8 × 7!}{7!} \\
&= 10 × 9 × 8 \\
&= 720
\end {align}$$
```
````
`````
``````
`````` {grid-item}
:columns: 6
````` {admonition} Combination
- gives the number of ways to select $r$ elements from $n$ elements where *_order does not matter_*

$$^nC_r = \frac{n!}{r! (n – r)!}$$

```` {card} Example
Find the number of ways 3 students can be selected from a class of 50 students.

``` {dropdown} $n = 50,\ r = 3 \dots =\ ^{50}C_3$
$$\begin {align} 
n = 50,\ r = 3...\ &=\ ^{50}C_3 \\
&= \frac{50!}{3! × 47!} \\
&= \frac{50 × 49 × 48 × 47!}{3! × 47!} \\
&= \frac{50 ×49 × 48}{6} \\
&= 19,600
\end {align}$$
```
````
`````
``````
```````

``````````

<!-- ## Analysis of Binary Search

`````````` {div} full-width
``````` {card}
```{code-block} cpp
:lineno-start: 1
:emphasize-lines:
int bsearch(int *A, int lo, int hi, int k) {
  
    //base case
    if (hi < lo) return NOT_FOUND;
    
    // calculate mid point index
    int mid = lo + ( (hi - lo) / 2);
    
    // key found?
    if (A[mid] == k) return mid;
    
    // key in upper subarray?
    if (A[mid] < k) return bsearch(A, mid + 1, hi, k);
    
    // key is in lower subarray?
    return bsearch(A, lo, mid - 1, k);
}
```
``` {card} Cases

$$
T(n) =
\begin{cases}
\ 1,  & \text{$n = 1$} \ \\[2ex]
\ T(\frac{n}{2}) + 1, & \text{$n \gt 1$} \
\end{cases}
$$

```
``` {dropdown} Explanation
To analyze the time complexity of a binary search algorithm using a recurrence relation, let's consider the following scenario:

Given a sorted array of size $n$, we want to find the index of a target element $x$ using binary search.

The binary search algorithm works by repeatedly dividing the search range in half until the target element is found or the search range becomes empty.

Let's define a recurrence relation to represent the time complexity of binary search:

$$ \ T(n) = T(\frac{n}{2}) + c \ $$

Here, $T(n)$ represents the time required to perform a binary search on an array of size $n$, and $c$ represents the constant time required for the comparisons and other operations within each recursive call.

The recurrence relation states that the time complexity of searching an array of size $n$ is equal to the time complexity of searching an array of size $\frac{n}{2}$, plus the constant time $c$.

To solve this recurrence relation, we can use the master theorem, which provides a general framework for solving such relations.

However, in the case of binary search, we can also intuitively observe that at each step, we reduce the search range by half. Therefore, the number of recursive calls needed until the search range becomes empty (i.e., the base case) is approximately $log_2(n)$.

Using this observation, we can conclude that the time complexity of binary search is logarithmic:

$$T(n) = O(log_2(n))$$

In other words, the time complexity of binary search grows logarithmically with the size of the array being searched. This is one of the reasons binary search is considered an efficient search algorithm, particularly for sorted arrays.
```
```````
`````````` -->

## [Recurrence Relations](https://www.math.wichita.edu/discrete-book/ch_sequences.html)

`````````` {div} full-width
```` {card}
By itself, a recurrence does not describe the running time of an algorithm
- need a *closed-form* solution (non-recursive description)
- exact *closed-form* solution may not exist, or may be too difficult to find

For most recurrences, an asymptotic solution of the form $\Theta()$ is acceptable
- ...in the context of analysis of algorithms
````
``````````

### [Methods of Solving Recurrences](https://courses.engr.illinois.edu/cs473/sp2010/notes/99-recurrences.pdf)

`````````` {div} full-width
```````` {card}

`````` {admonition} [Unrolling](https://courses.cs.washington.edu/courses/cse332/18su/handouts/unrolling.pdf)
:class: tip

> In the unrolling method, we repeatedly substitute the recurrence relation into itself until we reach a base case. Let's unroll the recurrence relation for a specific value of $n$:

$$\begin{align}
T(n) &= 2T \bigg(\frac{n}{2} \bigg) + n \\
&= 2 \bigg[2T \bigg(\frac{n}{4} \bigg) + \frac{n}{2} \bigg] + n \\
&= 4T \bigg(\frac{n}{4} \bigg) + 2n + n \\
&= 4 \bigg[2T \bigg(\frac{n}{8} \bigg) + \frac{n}{4} \bigg] + 2n + n \\
&= 8T \bigg(\frac{n}{8} \bigg) + 4n + 2n + n \\
&= 2^kT \bigg(\frac{n}{2^k} \bigg) + kn \\
\end{align}$$

We continue this process until we reach the base case, which occurs when $\frac{n}{2^k} = 1$. Solving for $k$, we find that $k = log_2\ (n)$. Therefore, the final unrolled expression becomes:

$$ \ \ T(n) = 2^{log_2 (n)} \ T(1) + n \ log_2 \ (n) \ \ $$

Since $T(1)$ is a constant, we can simplify the expression further:

$$\begin{align}
T(n) &= nT(1) + n\ log_2 \ (n) \\
&= O(n\ log_2\ (n))
\end{align}$$

Thus, the solution obtained through unrolling suggests that the time complexity of the original recurrence relation is $O(n\ log_2 (n))$.

``````
`````` {admonition} [Guessing](https://www.geeksforgeeks.org/method-of-guessing-and-confirming/)
:class: tip

> In the guessing method, we make an educated guess or hypothesis about the form of the solution based on the recurrence relation. We then use mathematical induction or substitution to prove our guess.

Let's guess that the solution to the recurrence relation $T(n) = 2T(\frac{n}{2}) + n$ is $T(n) = O(n\ log\ (n))$.

We assume that $T(k) ≤ ck\ log\ (k)$ for some constant $c$, where $k < n$. Now we substitute this assumption into the recurrence relation:

$$\begin{align}
T(n) &= 2T \bigg(\frac{n}{2} \bigg) + n \\
&≤ 2  \Bigg(\ c \bigg( \frac{n}{2} \bigg)\ log\ \bigg(\frac{n}{2} \bigg) \Bigg) + n \\
&= cn\ log (n) - cn\ log (2) + n \\
&= cn\ log (n) - cn + n \\
&= cn\ log (n) + (n - cn) \\
\end{align}$$

To ensure that $T(n) ≤ cn\ log\ (n)$ holds, we need to find a value of $c$ such that $(n - cn) ≤ 0$. By choosing $c ≥ 1$, we can guarantee that $T(n) ≤ cn\ log\ (n)$.

Hence, the solution $T(n) = O(n\ log\ (n))$ satisfies the recurrence relation.

``````
`````` {admonition} [Recursion Tree](https://www.javatpoint.com/daa-recursion-tree-method)
:class: tip

> In the recursion tree method, we draw a tree to represent the recursive calls made in the recurrence relation. Each level of the tree corresponds to a recursive call, and we analyze the work done at each level.

For our example, the recursion tree for $T(n) = 2T(\frac{n}{2}) + n$ would have a root node representing $T(n)$, two child nodes representing $T(\frac{n}{2})$, and so on. Each node represents a recursive call, and the work done at each node is represented by the term n.

The recursion tree will have $log_2\ (n)$ levels since we divide the problem size by $2$ at each level. At each level, the work done is $n$, and there are $2^i$ nodes at level $i$. Therefore, the total work at each level is $2^i * n$.

Summing up the work done at each level, we have:

$$ \ \ Total\ work\ = n + 2n + 4n + ... + (n * 2^{log_2\ (n)} - 1) \ \ $$

This is a geometric series with a common ratio of $2$ and the first term being $n$. The sum of this series is given by:

$$\begin{align}
Total work &= n * \frac{2^{log_2\ (n)} - 1}{2 - 1} \\
&= \frac{n * (n - 1)}{1} \\
&= n^2 - n \\
\end{align}$$

Therefore, the time complexity of the recurrence relation is $O(n^2)$.

Note that in this example, the unrolling and guessing methods led to a time complexity of $O(n\ log\ (n))$, while the recursion tree method resulted in $O(n^2)$. The discrepancy arises because the recursion tree method accounts for the exact work done at each level, while the other methods provide upper bounds or estimations.

``````
`````` {admonition} [Master Theorem](http://homepages.math.uic.edu/~leon/cs-mcs401-s08/handouts/master_theorem.pdf)
:class: tip

> The master theorem is a mathematical formula used to analyze the time complexity of divide-and-conquer algorithms. It provides a solution for recurrence relations of the form:

$$T(n) = aT \bigg(\frac{n}{b} \bigg) + f(n)$$

Where:

$T(n)$ represents the time complexity of the algorithm,
$a$ is the number of recursive subproblems,
$\frac{n}{b}$ is the size of each subproblem,
$f(n)$ is the time complexity of the remaining work done outside the recursive calls.

The master theorem provides three cases based on the relationship between $f(n)$ and the subproblem part $aT(\frac{n}{b})$.

````` {tab-set}
````  {tab-item} Cases

Case 1
: If $f(n) = O(n^c)$ for some constant $c < log_b(a)$, then the time complexity is dominated by the subproblem part, and the overall time complexity is given by 

$$T(n) = \Theta(n^{log_b(a)})$$

Case 2
: If $f(n) = \Theta(n^c \ log^{k(n)})$ for some constants $c ≥ 0$ and $k ≥ 0$, and if $aT(\frac{n}{b})$ is the dominant term, then the overall time complexity is given by 

$$T(n) = \Theta(n^{log_b(a)} \ log^{(k+1)}(n))$$

Case 3
: If $f(n) = \Omega(n^c)$ for some constant $c > log_b(a)$, and if $f(n)$ satisfies the regularity condition ($af(\frac{n}{b}) ≤ kf(n)$ for some constant $k < 1$ and sufficiently large $n$), then the non-recursive part dominates the time complexity, and the overall time complexity is given by 

$$T(n) = \Theta(f(n))$$

````
````  {tab-item} Case 1 Ex

$$T(n) = 4T \bigg(\frac{n}{2} \bigg) + n$$

``` {dropdown} Step 1 : Identify the values of a, b, and f(n)
In this case, 

$$a = 4$$

$$b = 2$$

$$f(n) = n$$

```
``` {dropdown} Step 2 : Compare f(n) with n^log_b(a)

Here, $f(n) = n$ and $n^{log_b(a)} = n^{log_2(4)} = n^2$ 

Since $f(n) = n = n^1 < n^2 = n^{log_b(a)}$, we fall into Case 1 of the master theorem.

```
``` {dropdown} Step 3 : Determine the overall time complexity

Using Case 1, the overall time complexity is $T(n) = \Theta(n^{log_b(a)})$.

In this case, $T(n) = \Theta(n^{log_2\ (4)}) = \Theta(n^2)$.

So, the overall time complexity of the algorithm in this example is $\Theta(n^2)$, which means the algorithm's running time grows quadratically with the input size $n$.

````  
````  {tab-item} Case 2 Ex

$$T(n) = 9T \bigg(\frac{n}{3} \bigg) + n^2$$

``` {dropdown} Step 1 : Identify the values of a, b, and f(n)
In this case:

$$a = 9 \ \ \ (number\ of\ sub-problems)$$  

$$b = 3 \ \ \ (size\ of\ each\ subproblem)$$  

$$ \ f(n) = n^2 \ $$  

```
``` {dropdown} Step 2 : Compare f(n) with n^log_b(a)

Here, $f(n) = n^2$ and $n^{log_b(a)} = n^{log_3(9)} = n^2$  

Since $f(n) = n^2 = n^{log_b(a)}$, we fall into Case 2 of the master theorem.
```
``` {dropdown} Step 3 : Determine the overall time complexity

Using Case 2, the overall time complexity is 

$$T(n) = Θ(n^2 \ log(n))$$
```
````
````  {tab-item} Case 3 Ex

$$T(n) = 2T \bigg(\frac{n}{2} \bigg) + n^3$$

``` {dropdown} Step 1 : Identify the values of a, b, and f(n)
In this case, 

$$a = 2$$  

$$b = 2$$  

$$f(n) = n^3$$
```
``` {dropdown} Step 2 : Compare f(n) with n^log_b(a)

Here, $f(n) = n^3$ and $n^{log_b(a)} = n^{log_2(2)} = n^1 = n$  

Since $f(n) = n^3 > n = n^{log_b(a)}$, we fall into Case 3 of the master theorem.
```
``` {dropdown} Step 3: Check if f(n) satisfies the regularity condition

In this case, we can see that $af(\frac{n}{b}) = 2(\frac{n}{2})^3 = (\frac{1}{2})n^3 \le kn^3$ for $k = \frac{1}{2}$ and sufficiently large $n$.  

The regularity condition is satisfied.
```
``` {dropdown} Step 4 : Determine the overall time complexity.
Using Case 3, the overall time complexity is 

$$T(n) = Θ(n^3)$$

```
````
`````

In our example, the recurrence relation is $T(n) = 2T(\frac{n}{2}) + n$, where $a = 2$, $b = 2$, and $f(n) = n$.

Now, let's compare the function $f(n)$ with $n^{log_b\ (a)}$:

$f(n) = n$, which is asymptotically smaller than $n^{log_2\ (2)} = n$.

*According to the Master Theorem:*

If $f(n) = O(n^c)$ where $c < log_b\ (a)$, then $T(n) = \Theta(n^{log_b\ (a)})$.
In our case, $f(n) = O(n^1)$, and $c = 1 < log_2\ (2) = 1$. Since the condition is met, the time complexity of the recurrence relation is $Θ(n^{log_2\ (2)}) = \Theta(n)$.

Therefore, according to the Master Theorem, the time complexity of the binary search recurrence relation $T(n) = 2T(\frac{n}{2}) + n$ is $\Theta(n)$, which aligns with the result obtained from the unrolling and guessing methods.

It's important to note that the Master Theorem is applicable in specific cases, and not all recurrence relations can be solved using this theorem. However, for recurrence relations that follow the prescribed form, it provides a convenient way to determine the time complexity.

``````
````````
``````````

<!-- ### [Unrolling the binary search recurrence](https://youtu.be/XcZw01FuH18)

`````````` {div} full-width
```````` {card}

``````` {admonition} [Binary Search Recursive Method](https://youtu.be/uEUXGcc2VXM)

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 1-2,7-10

void RBinSearch(l, h, key) {                                // = T(n)
  if (l == h) {                                             // = 1
    if (A[l] == key) return l;
    else return 0;
  }
  else {                                    
    mid = (l + h)/2;                                        // = 1
    if (key == A[mid]) return mid;                          // = 1
    if (key < A[mid]) return RBinSearch(l, mid - 1, key);   // = 1
    else return RBinSearch(mid + 1, h, key);                // = T(n/2)
  }
}
```

```````
``````` {card} Base Case & General Form
$$
T(n) =
\begin{cases}
1,  & \text{$n = 1$}  \\[2ex]
T(\frac{n}{2}) + 1, & \text{$n \gt 1$}
\end{cases}
$$
```````
``````` {card} Stepwise



```````



````````
`````````` -->

### Examples

`````````` {div} full-width
<!-- ````````` {card} -->

```````` {admonition} [Recurrence Relation: Dividing Function](https://youtu.be/8gt0D0IqU5w)

```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 1, 3, 4
void Test(int n) {       // = T(n)
  if (n > 0) {
    printf("/d", n);     // = 1
    Test(n/2);           // = T(n/2) 
  }
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$n = 1$}  \\[2ex]
T(\frac{n}{2}) + 1, & \text{$n \gt 1$}
\end{cases}
$$

`````` {dropdown} Unrolling

Let's unroll the recurrence relation step by step:

$$\begin{align}
Step\ 1 : \ & T(n)  = T(\frac{n}{2}) + c \\
Step\ 2 : \ & T(n)  =  \bigg[T(\frac{n}{4}) + c \bigg] + c \\
& = T(\frac{n}{4}) + 2c \\
Step\ 3 : \ & T(n)  =  \bigg[T(\frac{n}{8}) + c \bigg] + 2c \\
&  = T(\frac{n}{8}) + 3c \\
\end{align}$$

Continuing this process, we can unroll the recurrence relation up to k steps:  

$$ \ \ T(n) = T \bigg(\frac{n}{2^k} \bigg) + kc \ \ $$

We keep unrolling until we reach the base case, which occurs when $\frac{n}{2^k} = 1$. Solving for $k$, we find that $k = log_2\ (n)$.  

Now, let's substitute this value of $k$ into the unrolled relation:

$$ \ \ T(n) = T(\frac{n}{2^{log_2\ (n)}}) + log_2\ (n)c \ \ $$

Since $\frac{n}{2^{log_2\ (n)}} = 1$, we simplify further:

$$T(n) = T(1) + log_2\ (n)c$$

Since $T(1)$ is a constant time complexity for the base case of a binary search, we can replace it with a constant, say $d$:

$$T(n) = d + log_2\ (n)c$$

Finally, we can simplify this expression as:

$$T(n) = O(log\ (n))$$

Therefore, after unrolling the recurrence relation for binary search, we obtain the time complexity of $O(log\ (n))$.

This analysis shows that the time complexity of a binary search algorithm is logarithmic with respect to the size of the array being searched, which aligns with the intuitive understanding of the algorithm's efficiency.

``````
`````` {dropdown} Guessing

Let's make a guess or hypothesis about the form of the solution based on the recurrence relation $T(n) = T(\frac{n}{2}) + 1$.

Let's assume that $T(n) = O(log\ (n))$.

We assume that $T(k) ≤ c\ log\ (k)$ for some constant $c$, where $k < n$. Now, let's substitute this assumption into the recurrence relation:

$$\begin{align}
T(n) &= T \bigg(\frac{n}{2} \bigg) + 1 \\
&≤ c\ log\ \frac{n}{2} + 1 \\
&= c(log\ (n) - 1) + 1 \\
&= c\ log\ (n) + 1 + c \\
&= c\ log\ (n) + (1 - c) \\
\end{align}$$

To ensure that $T(n) ≤ c\ log\ (n)$ holds, we need to find a value of $c$ such that $(1 - c) ≤ 0$. By choosing $c ≥ 1$, we can guarantee that $T(n) ≤ c\ log\ (n)$.

Hence, the solution $T(n) = O(log\ (n))$ satisfies the recurrence relation.

``````
`````` {dropdown} Recursion Tree

At each level of the recursion tree, we divide the problem size by $2$, following the recurrence relation $T(n) = T(\frac{n}{2}) + 1$. The work done at each level is constant, represented by the "+ 1" term.

Let's start with the initial value $T(n)$ and recursively split it into smaller sub-problems until we reach the base case.

``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20210608091942/img1-300x141.PNG
```

And so on...

The recursion tree will have $log_2\ (n)$ levels since we divide the problem size by $2$ at each level. At each level, the work done is a constant "+ 1".

The total work done can be calculated by summing up the work at each level:

$$\begin{align}
Total work &= 1 + 1 + 1 + ... + 1\ (log_2\ (n) times) \\
&= log_2\ (n) \\
\end{align}$$

Therefore, the time complexity of the recurrence relation $T(n) = T(\frac{n}{2}) + 1, analyzed using the recursion tree method, is $O(log\ (n))$.

The recursion tree method provides a direct visualization of the recursive calls and the corresponding work done at each level, allowing us to analyze the time complexity of the recurrence relation.

``````
`````` {dropdown} Master Theorem

The Master Theorem provides a framework for solving recurrence relations of the form $T(n) = aT(\frac{n}{b}) + f(n)$, where $a ≥ 1$, $b > 1$, and $f(n)$ is a function.

In our case, $T(n) = T(\frac{n}{2}) + 1$, where $a = 1$, $b = 2$, and $f(n) = 1$.

Comparing $f(n) = 1$ with $n^{log_b\ (a)}$:

$f(n) = 1$, which is equal to $n^{log_2\ (1)} = n^0 = 1$.

According to the Master Theorem:

If $f(n) = \Theta(n^{log_b\ (a)} * log^{k(n)})$, where $k ≥ 0$, then $T(n) = \Theta(n^{log_b\ (a)} * log^{k+1}\ (n))$.
In our case, $f(n) = \Theta(1)$, which falls under the second case. Therefore, the time complexity of the recurrence relation $T(n) = T(\frac{n}{2}) + 1$ is $\Theta(n^{log_2\ (1)} * log^{0+1}\ (n)) = \Theta(log\ (n))$.

Thus, according to the Master Theorem, the time complexity of the recurrence relation $T(n) = T(\frac{n}{2}) + 1$ is $\Theta(log\ (n))$, which aligns with the results obtained from unrolling, guessing, and the recursion tree.

All four methods provide consistent solutions, indicating that the time complexity of the recurrence relation $T(n) = T(\frac{n}{2}) + 1$ is $O(log\ (n))$.

``````
````````


``````` {admonition} [Recurrence Relation: Linear](https://youtu.be/4V30R3I1vLI)

```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 1, 3, 4
void Test(int n) {       // = T(n)
  if (n > 0) {
    printf("/d", n);     // = 1
    Test(n - 1);         // = T(n - 1) 
  }
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$n\ = 0$}  \\[2ex]
T(n - 1) + 1, & \text{$n\ \gt 0$}
\end{cases}
$$

`````` {dropdown} Unrolling

Let's unroll the recurrence relation step by step:

$$\begin{align}
Step\ 1 : \ & T(n)  = T(n - 1) + 1 \\
Step\ 2 : \ & T(n)  = [T(n - 2) + 1] + 1 \\
& = T(n - 2) + 2 \\
Step\ 3 : \ & T(n)  = [T(n - 3) + 1] + 2 \\
&  = T(n - 3) + 3 \\
\end{align}$$

Continuing this process, we can unroll the recurrence relation up to k steps:

Step k:

$$ \ \ T(n) = T(n - k) + k \ \ $$

We keep unrolling until we reach the base case, which occurs when $n - k = 1$. Solving for $k$, we find that $k = n - 1$.

Now, let's substitute this value of k into the unrolled relation:

$$ \ \ T(n) = T(1) + (n - 1) \ \ $$

Since $T(1)$ represents the time complexity for the base case, which is a constant, we can replace it with a constant, say $c$:

$$ \ \ \ T(n) = c + (n - 1) \ \ \ $$

Finally, we can simplify this expression as:

$$ \ \ T(n) = O(n) \ \ $$

Therefore, the solution obtained through unrolling suggests that the time complexity of the recurrence relation $T(n) = T(n - 1) + 1$ is $O(n)$.

``````
`````` {dropdown} Guessing

Let's make a guess or hypothesis about the form of the solution based on the recurrence relation $T(n) = T(n - 1) + 1$.

Let's assume that $T(n) = O(n)$.

We assume that $T(k) ≤ ck$ for some constant $c$, where $k < n$. Now, let's substitute this assumption into the recurrence relation:

$$\begin{align}
T(n) & = T(n - 1) + 1 \\
& ≤ c(n - 1) + 1 \\
& = cn - c + 1 \\
\end{align}$$

To ensure that $T(n) ≤ cn$ holds, we need to find a value of $c$ such that $(-c + 1) ≤ 0$. By choosing $c ≥ 1$, we can guarantee that $T(n) ≤ cn$.

Hence, the solution $T(n) = O(n)$ satisfies the recurrence relation.

``````
`````` {dropdown} Recursion Tree

Let's draw a recursion tree to represent the recursive calls made in the recurrence relation $T(n) = T(n - 1) + 1$. Each level of the tree corresponds to a recursive call, and we analyze the work done at each level.

The recursion tree will have n levels since we subtract $1$ from $n$ at each level. At each level, the work done is $1$, and there is only one node at each level. Therefore, the total work at each level is $1$.

Summing up the work done at each level, we have:

$$\begin{align}
Total work & = 1 + 1 + 1 + ... + 1\ (n\ times) \\
& = n \\
\end{align}$$

Therefore, the time complexity of the recurrence relation is $O(n)$.

``````
`````` {dropdown} Master Theorem

The Master Theorem is not applicable to the recurrence relation $T(n) = T(n - 1) + 1$ because it is not in the required form of $T(n) = aT(\frac{n}{b}) + f(n)$.

Therefore, the Master Theorem cannot be directly used to solve this recurrence relation.

To summarize, the analysis using unrolling, guessing, recursion tree, and the Master Theorem (where applicable) all yield a time complexity of $O(n)$ for the recurrence relation $T(n) = T(n - 1) + 1$.

``````


<!-- ```` {admonition} Can you write (and solve) the recurrence?
:class: dropdown, tip

``` {card} Breakdown
$$\begin {align}
T(n) &= T(n - 1) + 1 \\
T(n - 1) &= T(n - 2) + 2 \\
T(n - 2) &= T(n - 3) + 3 \\ 
• \\
• \\
• \\
T(n - k) &= T(n - k) + k \\
\end {align}$$
```

``` {card} Substitution $T(n - 1)$
$$\begin {align}
T(n) &= \bigg[T(n - 2) + 1 \bigg] + 1 \\ 
&= T(n - 2) + 2 \\
&= \bigg[T(n - 3) + 1 \bigg] + 2 \\
&= T(n - 3) + 3 \\
• \\
• \\
• \\
&= T(n - k) + k \\
\end {align}$$ 
```

``` {card} For $k$ times

$$\begin {align}
\text{For : } & T(n) = T(n - k) + k \\
\text{Assume : } & n\ - k\ = 0 \\
\text{Therefore : } & n\ = k \\
\end {align}$$ 

$$\begin {align}
T(n) &= T(n - n) + n \\
T(n) &= T(0) + n \\
• \\
T(n) &= 1 + n \\
T(n) &= \Theta(n) \\
&= \Theta(n) \\
\end {align}$$

```

```` -->
```````

``````` {admonition} [Recurrence Relation: Divide & Conquer](https://youtu.be/1K9ebQJosvo)

```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 1, 3, 6, 7
void Test(int n) {              // = T(n)
  if (n > 1) {
    for(i = 0; i < n; i++>) {   // = n
      // some statement
    }
    Test(n/2);                  // = T(n/2)
    Test(n/2);                  // = T(n/2)
  }
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$n\ = 1$}  \\[2ex]
2T(\frac{n}{2}) + n, & \text{$n\ \gt 1$}
\end{cases}
$$

`````` {dropdown} Unrolling

Let's unroll the recurrence relation step by step:

$$\begin{align}
Step\ 1 : \ & T(n)  = 2T \bigg(\frac{n}{2} \bigg) + n \\
Step\ 2 : \ & T(n)  = 2[2T \bigg(\frac{n}{4} \bigg) + \frac{n}{2}] + n \\
& = 4T \bigg(\frac{n}{4} \bigg) + 2n \\
Step\ 3 : \  T(n) & = [T \bigg(\frac{n}{8} \bigg) + \frac{n}{4} + \frac{n}{2}] + 4n \\
&  = 8T \bigg(\frac{n}{8} \bigg) + 4n \\
\end{align}$$

Continuing this process, we can unroll the recurrence relation up to k steps:

$$\begin{align}
Step\ k : \ & T(n) = 2^{k}\ T \bigg( \frac{n}{2^k} \bigg) + kn \\
\end{align}$$

We keep unrolling until we reach the base case, which occurs when $ \frac{n}{2^k} = 1 $. Solving for $k$, we find that $k = log_2\ (n)$.

Now, let's substitute this value of k into the unrolled relation:

$$\begin{align}
T(n) &= 2^{log_2\ (n)}\ T \bigg(\frac{n}{2^{log_2\ (n)}} \bigg) + n\ log_2\ (n) \\
&= nT(1) + n\ log_2\ (n) \\
&= n + n\ log_2\ (n) \\
\end{align}$$

Since $T(1)$ represents the time complexity for the base case, which is a constant, we can replace it with a constant, say $c$:

$$ \ \ T(n) = c + n + n\ log_2\ (n) \ \ $$

Finally, we can simplify this expression as:

$$ \ \ T(n) = O(n\ log\ (n)) \ \ $$

Therefore, the solution obtained through unrolling suggests that the time complexity of the recurrence relation $T(n) = 2T(\frac{n}{2}) + n$ is $O(n\ log\ (n))$.

``````
`````` {dropdown} Guessing

Let's make a guess or hypothesis about the form of the solution based on the recurrence relation $T(n) = 2T(\frac{n}{2}) + n$.

Let's assume that $T(n) = O(n\ log\ (n))$.

We assume that $T(k) ≤ ck\ log\ (k)$ for some constant $c$, where $k < n$. Now, let's substitute this assumption into the recurrence relation:

$$\begin{align}
T(n) &= 2T \bigg(\frac{n}{2} \bigg) + n \\
&≤ 2c \bigg(\frac{n}{2} \bigg)\ log\ \bigg(\frac{n}{2} \bigg) + n \\
&= cn\ log\ \bigg(\frac{n}{2} \bigg) + n \\
&= cn\ log\ (n) - cn\ log\ (2) + n \\
&= cn\ log\ (n) - cn + n \\
\end{align}$$

To ensure that $T(n) ≤ cn\ log\ (n)$ holds, we need to find a value of $c$ such that $(-cn + n) ≤ 0$. By choosing $c ≥ 1$, we can guarantee that $T(n) ≤ cn\ log\ (n)$.

Hence, the solution $T(n) = O(n\ log\ (n))$ satisfies the recurrence relation.

``````
`````` {dropdown} Recursion Tree

Let's draw a recursion tree to represent the recursive calls made in the recurrence relation $T(n) = 2T(\frac{n}{2}) + n$. Each level of the tree corresponds to a recursive call, and we analyze the work done at each level.

``` {figure} https://algorithmtutor.com/images/recursion_tree1_final.png
:width: 600px
```

The recursion tree will have $log_2\ (n)$ levels since we divide the problem size by $2$ at each level. At each level, the work done is $n$, and there are $2^i$ nodes at level $i$. Therefore, the total work at each level is $n * 2^i$.

Summing up the work done at each level, we have:

$$Total work = n + 2n + 4n + ... + (2^{log_2\ (n) - 1}\ n) \ \ $$

This is a geometric series with a common ratio of 2 and the first term being n. The sum of this series is given by:

$$\begin{align}
Total work &= n * \frac{2^{log_2\ (n)}\ - 1}{2 - 1} \\
&= n * {2^{log₂(n)}\ - 1} \\
&= n * (n - 1) \\
&= n^2 - n \\
\end{align}$$

Therefore, the time complexity of the recurrence relation is $O(n^2)$.

``````
`````` {dropdown} Master Theorem

The Master Theorem is applicable to the recurrence relation $T(n) = 2T(\frac{n}{2}) + n$. We can express it in the form $T(n) = aT(\frac{n}{b}) + f(n)$ with $a = 2$, $b = 2$, and $f(n) = n$.

Comparing $f(n) = n$ with n^{log_b\ (a)}:

$f(n) = n$, which is smaller than $n^{log_2\ (2)} = n$.

According to the Master Theorem:

If $f(n) = O(n^c)$ for some constant $c < log_b\ (a)$, then $T(n) = Θ(n^{log_b\ (a)})$.
In our case, $f(n) = O(n^1) = O(n)$, which falls under the first case. Therefore, the time complexity of the recurrence relation $T(n) = 2T(\frac{n}{2}) + n$ is $\Theta(n^{log_2\ (2)}) = \Theta(n)$.

Thus, according to the Master Theorem, the time complexity of the recurrence relation $T(n) = 2T(\frac{n}{2}) + n$ is $\Theta(n)$, which aligns with the results obtained from unrolling, guessing, and the recursion tree.

All four methods provide consistent solutions, indicating that the time complexity of the recurrence relation $T(n) = 2T(\frac{n}{2}) + n$ is $O(n\ log\ (n))$.

``````







<!-- ````` {admonition} Can you write (and solve) the recurrence?
:class: dropdown, tip

```` {card} Tree Method
``` {figure} imgs/10_ex_2.png
:width: 100%
```

$$
For\ k\ times\ = \frac{n}{2^k}\ \Rightarrow\ n = 2^k \\
Hence,\ k\ = log\ n \\
T(n) = \Theta(n\ log\ n)
$$
````

````` {card} Substitution Method

```` {grid}
``` {grid-item}
$$\begin {align}
T(n) &= 2T(\frac{n}{2}) + n \\
&= 2\bigg[2T(\frac{n}{2^2}) + \frac{n}{2}\bigg] + n \\
&= 2^2T(\frac{n}{2^2} + n + n) \\
&= 2^2\bigg[2T(\frac{n}{2^3}) + \frac{n}{2^2}\bigg] + 2n \\
&= 2^3T(\frac{n}{2^3}) + 3n \\
&= 2^kT(\frac{n}{2^k}) + kn \\
\end {align}$$
```
``` {grid-item}
*What to sub in...*

$$\begin {align}
T(n) &= 2T(\frac{n}{2}) + n \\
T(\frac{n}{2}) &= 2T(\frac{n}{n^2}) + \frac{n}{2^2} \\
T(\frac{n}{2^2}) &= 2T(\frac{n}{2^3}) + \frac{n}{2^2} \\
\end {align}$$
```
``` {grid-item}
$$
Assume...\ T(\frac{n}{2^k}) = T(1) \\
\frac{n}{2^k} = 1 \\
$$
```
``` {grid-item}
$$
Therefore...\ n\ = 2^k \\
k\ = log\ n \\
$$
```
``` {grid-item}
$$\begin {align}
T(n) &= 2^kT(1) + kn \\
&= n * 1 + n\ log\space n \\
&= \Theta(n\space log\space n) \\
\end {align}$$
```

````

````` -->
```````

``````` {admonition} [Recurrence Relation: Tower of Hanoi](https://youtu.be/IawM82BQ4II) 

```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 1 - 4
void Test(int n) {    // = T(n)
  printf("/d", n);    // = 1
  Test(n - 1);        // = T(n - 1)
  Test(n - 1);        // = T(n - 1)
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$n\ = 0$}  \\[2ex]
2T(n - 1) + 1, & \text{$n\ \gt 0$}
\end{cases}
$$

`````` {dropdown} Unrolling

Let's unroll the recurrence relation step by step:

$$\begin{align}
Step\ 1 : \ & T(n)  = 2T(n - 1) + 1 \\
Step\ 2 : \ & T(n)  = 2[2T(n - 2) + 1] + 1 \\
& = 4T(n - 2) + 3 \\
Step\ 3 : \ & T(n)  = 2[2[2T(n - 3) + 1] + 1] + 1 \\
&  = 8T(n - 3) + 7 \\
\end{align}$$

Continuing this process, we can unroll the recurrence relation up to k steps:

$$\begin{align}
Step k: &  T(n) = 2^{k}\ T(n - k) + (2^k - 1)
\end{align}$$

We keep unrolling until we reach the base case, which occurs when $n - k = 1$. Solving for $k$, we find that $k = n - 1$.

Now, let's substitute this value of $k$ into the unrolled relation:

$$\begin{align}
T(n) &= 2^{n - 1}\ T(1) + (2^{n - 1} - 1) \\
&= 2^{n - 1} + (2^{n - 1} - 1) \\
&= 2^n - 1 \\
\end{align}$$

Therefore, the solution obtained through unrolling suggests that the time complexity of the recurrence relation $T(n) = 2T(n - 1) + 1$ is $O(2^n)$.

``````
`````` {dropdown} Guessing

Let's make a guess or hypothesis about the form of the solution based on the recurrence relation $T(n) = 2T(n - 1) + 1$.

Let's assume that $T(n) = O(2^n)$.

We assume that $T(k) ≤ c * 2^k$ for some constant $c$, where $k < n$. Now, let's substitute this assumption into the recurrence relation:

$$\begin{align}
T(n) &= 2T(n - 1) + 1 \\
&≤ 2(c * 2^(n - 1)) + 1 \\
&= c * 2^n + 1 \\
\end{align}$$

To ensure that $T(n) ≤ c * 2^n$ holds, we need to find a value of $c$ such that $(c + 1) ≤ c$. This is not possible, so our assumption is incorrect.

Hence, we cannot prove the solution $T(n) = O(2^n)$ using the guessing method.

``````
`````` {dropdown} Recursion Tree

Let's draw a recursion tree to represent the recursive calls made in the recurrence relation $T(n) = 2T(n - 1) + 1$. Each level of the tree corresponds to a recursive call, and we analyze the work done at each level.

``` {figure} https://frederick-s.github.io/Introduction-to-Algorithms-Notes/04-Divide-and-Conquer/4.4-4.png
:width: 300px
```

The recursion tree will have n levels since we subtract $1$ from $n$ at each level. At each level, the work done is $1$. Therefore, the total work at each level is $1 * 2^i$.

Summing up the work done at each level, we have:

$$ \ \ Total work = 1 + 2 + 4 + ... + 2^{n - 1} \ \ $$

This is a geometric series with a common ratio of {2} and the first term being {1}. The sum of this series is given by:

$$ \ \ Total work = 2^n - 1 \ \ $$

Therefore, the time complexity of the recurrence relation is $O(2^n)$.

``````
`````` {dropdown} Master Theorem

The Master Theorem is not directly applicable to the recurrence relation $T(n) = 2T(n - 1) + 1$ because it is not in the required form of $T(n) = aT(\frac{n}{b}) + f(n)$.

Therefore, the Master Theorem cannot be used to directly solve this recurrence relation.

To summarize, the analysis using unrolling, guessing, recursion tree, and the Master Theorem (where applicable) all yield a time complexity of $O(2^n)$ for the recurrence relation $T(n) = 2T(n - 1) + 1$.

``````







<!-- `````` {admonition} Can you write (and solve) the recurrence?
:class: dropdown, tip

````` {card} Tree Method

            T(n)
            / \
           n   T(n-1)
                / \
             n-1   T(n-2)
                    / \
                 n-2   T(n-3)
                        / \
                     ...   ...
                            / \
                               T(2)
                                / \
                               2   T(1)
                                    / \
                                   1   T(0)
                                  
```` {card} Breakdown
$$\begin {align}
1 + 2 + 2^2 + 2^3 ... + 2^k & = 2^{k + 1} - 1 \\
\\
ar + ar + ar^2 + ar^3 ... + ar^k & = \frac{a(r^{k + 1} - 1)}{r - 1} \\
\\
Where \dots a = 1,  r = 2,  & = \frac{1(2^{k + 1}1)}{2 - 1} \\
\\
& = 2^{k + 1} - 1
\end {align} $$
````

```` {card} Assume
$$\begin {align}
if \dots n - k & = 0 \\
\\
then \dots n & = k \\
& = 2^{k + 1} - 1 => 2^{n + 1} - 1 \\
& = \Theta(2^n) \\
\end {align}$$
````

`````

````` {card} Substitution
```` {grid} 
``` {grid-item}
$$\begin {align}
T(n) &= 2T(n - 1) + 1 \\
& = 2\bigg[2T(n - 2) + 1 \bigg] + 1 \\
& = 2^2T(n - 2) + 2 + 1 \\
& = 2^2 \bigg[2T(n - 3) + 1 \bigg] + 2 + 1 \\
& = 2^3T(n - 3) + 2^2 + 2 + 1 \\
& • \\
& • \\
& • \\
& = 2^kT(n - k) + 2^k-1 + 2^k-2 + ... 2^2 + 2 + 1 \\
\end {align}$$
```
``` {grid-item}
$$\begin {align}
Assume \dots n - k = 0 \\
\\
n = k \\
\\
T(n) & = 2^nT(0) + 1 + 2 + 2^2\ + \dots\ 2^k-1 \\
& = 2^n - 1 + 2^k - 1 \\
& = 2^n + 2^n - 1 \\
& = 2^n+1 - 1 \\
& = \Theta(2^n) \\
\end {align}$$
```
````
````` -->

<!-- ``````` -->
``````````
