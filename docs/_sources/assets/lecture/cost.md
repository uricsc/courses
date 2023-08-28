# Computational Cost

## Analyzing running time

`````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/YoZPTyGL2IQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
In computer science, data structures and algorithms are fundamental concepts used to efficiently store and manipulate data. Data structures are ways of organizing and storing data in a computer's memory, while algorithms are step-by-step procedures for performing specific tasks. The computational cost of data structures and algorithms refers to the amount of time and resources required to execute a particular operation or task.

When designing or choosing data structures and algorithms, it's important to consider their computational cost. Some operations may require a lot of time and resources, which can impact the overall performance of a system. The computational cost can be analyzed using various measures such as time complexity, space complexity, and big-O notation.

Time complexity measures the number of operations required to perform a task as a function of the input size. Space complexity measures the amount of memory required to store data structures and algorithms. Big-O notation is used to express the upper bound of the computational cost in terms of the input size.

By understanding the computational cost of data structures and algorithms, developers can make informed decisions about which ones to use in a particular context. For example, if the system needs to perform a lot of searches, a data structure with fast search time complexity like a hash table may be a better choice than a binary search tree. Similarly, if memory usage is a concern, a data structure with low space complexity like an array may be a better choice than a linked list.
```
``` {card} Additional Resources
- [Algorithms Explained: Computational Complexity | DataDaft](https://youtu.be/47GRtdHOKMg) : 21:22
```
`````


````` {card}
```` {grid}

``` {grid-item-card} Empirical Model
- **Run** algorithm
- Measure actual time
```

```{grid-item-card} Mathematical Model
- **Analyze** algorithm
- Develop Model
```

````
`````
``````

## Theoretical Models

`````` {div} full-width
````` {card}
```` {grid}
```{grid-item-card} Mathematical Model
- High-level analysis
  - <b class="brown">no need to implement</b>
- Independent of hardware / software
- Based on **counts** of basic <b class="brown">instructions</b>
  - additions, multiplications, comparisons,etc
  - exact definition <u>not important</u> but <b class="brown">must be relevant</b> to the problem
```

```{grid-item-card} Basic assumptions
- In order to use a **formal framework**, we will make  certain assumptions
  - count basic instructions: additions, multiplications, comparisons, assignments
  - each instruction takes one time unit
  - instructions are executed sequentially
  - infinite memory
- Focus on <span class="green">analyzing <b>running time</b></u>
```
````
`````
``````

### Examples

`````````` {div} full-width
`````````  {card}
````````   {tab-set}
```````    {tab-item} Model
What to count?
- only relevant instructions? 
- all instructions?

```{code-block} cpp
:lineno-start: 1
:emphasize-lines:

for (int i = 0; i < n; i++) {
    std::cout << (2 * i);
}
```

````` {admonition} Time Complexity & Why...
The time complexity of this code is $O(n)$, because the operation within the loop is done `n` times.

```` {card} Application
``` {code-block} cpp
#include <iostream>
using namespace std;

int main()
{
  int i, n = 8;
  for (i = 1; i <= n; i++) {
    cout << "Hello World !!!\n";
  }
  return 0;
}
```
**Output**
``` {code-block} bash
Hello World !!!
Hello World !!!
Hello World !!!
Hello World !!!
Hello World !!!
Hello World !!!
Hello World !!!
Hello World !!!
```
**Time Complexity**
: In the above code “Hello World !!!” is printed only `n` times on the screen, as the value of `n` can change.  So, the time complexity is linear: $O(n)$ i.e. every time, a linear amount of time is required to execute code.

**Auxiliary Space**
: $O(1)$
````

`````
```````
```````    {tab-item} Example 1
````` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        std::cout << (i * j);
    }
}
`````

````` {admonition} Time Complexity & Why...
:class: dropdown, tip
This code has a time complexity of $O(n^2)$. This is because it has nested loops that are both iterating over `n` elements, so the total number of operations increases quadratically with the size of the input.

`````
```````
```````    {tab-item} Example 2
````` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

for (int i = 0; i < n; i++) {
    for (int j = 0; j < n * n; j++) {
        std::cout << (i * j);
    }
}
`````
````` {admonition} Time Complexity & Why...
:class: dropdown, tip
The time complexity of this code is $O(n^3)$. This is because there are two nested for loops, each of which has a time complexity of $O(n)$, resulting in a time complexity of $O(n^2)$. The total time complexity is $O(n^3)$ because the inner loop is iterating $n * n$ times.
`````
```````
```````    {tab-item} Example 3
````` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

for (int i = 0; i < n; i++) {
    for (int j = 0; j < i; j++) {
        sum = sum * j;
    }
}
`````
````` {admonition} Time Complexity & Why...
:class: dropdown, tip
This code has a time complexity of $O(n^2)$. This is because there is an outer loop that runs `n` times and an inner loop that runs i times, where `i` is the value of the outer loop's iterator. Since `i` starts at `0` and increases each iteration of the loop, the inner loop will run `0` times on the first iteration, `1` time on the second iteration, `2` times on the third iteration, and so on, up to `n` times on the last iteration. This results in a total of $n(n+1)/2$ iterations of the inner loop, which is equivalent to $O(n^2)$. 

$$\begin {align}
n + n-1 + n-2 + ... + 1 & = n(n+1)/2 \\
& = O(n^2) \\
\end {align}$$
`````
```````
```````    {tab-item} Example 4
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        for (int k = 0; k < n; k++) {
            //count 1 instruction
        }
    }
}
```
````` {admonition} Time Complexity & Why...
:class: dropdown, tip
The time complexity of this code is $O(n^3)$ because there are three nested loops, each of which runs `n` times. This results in $n^3$ total iterations of the innermost loop.
`````
```````
```````    {tab-item} Example 5
``` {code-block} cpp
:lineno-start: 1
:emphasize-lines:

for (int i = 0; i < n; i++) {
    for (int j = 0; j < i * i; j++) {
        for (int k = 0; k < j; k++) {
            // count 1 instruction
        }
    }
}
```
````` {admonition} Time Complexity & Why...
:class: dropdown, tip
This code has a time complexity of $O(n^4)$. This is because the first loop runs in $O(n)$ time, the second loop runs in $O(n^2)$ time, and the third loop runs in $O(n^3)$ time. Therefore, the total time complexity is the product of all of these which is $O(n^4)$.
`````
```````
````````
`````````
``````````

## Some rules...

`````````` {div} full-width
```` {card}
``` {card} Single loops
- essentially, $total\ iterations\ \times total\ instructions\ performed\ per\ iteration$
```
``` {card} Nested loops
- count instructions inside out
- careful with the range of the loop
- when possible, multiplications can be used for counts from each loop
```
``` {card} Consecutive statements
- just add the counts
```
``` {card} Conditionals
- consider the branch with the highest count
```
````
``````````

## [Computational cost](https://www.youtube.com/watch?v=YoZPTyGL2IQ)

`````````` {div} full-width
```` {card}

Number of <b class="brown">basic instructions</b> required by the algorithm to process an input of a certain <b class="brown">size $n$</b>

$$\begin{align}
T(n) \\
\end{align}$$

- basic instructions are always  <b class="brown">relevant</b> to the problem
  - ex: find max in an array
    - \# of comparisons
  - ex: sum elements in an array
    - \# of additions

````
``````````

## Comparing computational cost

`````````` {div} full-width
```` {card} $Cost$

``` {list-table} 
:header-rows: 2

* - 
  - $find (x,y,z)s.t.x+y+z = k$
  - $find (x,y)s.t.x+y = k$
  - $find\ x = k$
* - Size of input
  - $n^3$
  - $n^2$
  - $n$
* - $n = 1$
  - 1
  - 1
  - 1
* - $n = 10$
  - 1000
  - 100
  - 10
* - $n = 100$
  - 1000000
  - 10000
  - 100
* - $n = 1000$
  - 1000000000
  - 1000000
  - 1000
* - $n = 10000$
  - 1000000000000
  - 100000000
  - 10000
* - $n = 100000$
  - 1000000000000000
  - 10000000000
  - 100000
* - $n = 1000000$
  - 1000000000000000000
  - 1000000000000
  - 1000000
* - $n = 10000000$
  - 1000000000000000000000
  - 100000000000000
  - 10000000

```
````
``````````

## [Growth Rate](https://en.wikipedia.org/wiki/Time_complexity#Logarithmic_time)

`````````` {div} full-width
```` {card}

``` {list-table} $Growth\ of\ T(n)\ as\ n\to\infty$
:header-rows: 2

* - $Constant$
  - $Log-Logarithmic$
  - $Logarithmic$
  - $Linear$
  - $Linearithmic$
  - $Quadratic$<br>$(Polynomial)$
  - $Cubic$<br>$(Polynomial)$
  - $Exponential$
* - $n$
  - $log\ log\ n$
  - $log\ n$
  - $n$
  - $n\ log\ n$
  - $n^2$
  - $n^3$
  - $2^n$
* - $16$
  - $2$
  - $4$
  - $2^4$
  - $4 \times 2^4 = 2^6$
  - $2^8$
  - $2^{12}$
  - $2^{16}$
* - $256$
  - $3$
  - $8$
  - $2^8$
  - $8 \times 2^8 = 2^{11}$
  - $2^{16}$
  - $2^{24}$
  - $2^{256}$
* - $1024$
  - $\approx 3.3$
  - $10$
  - $2^{10}$
  - $10 \times 2^{10} = 2^{13}$
  - $2^{20}$
  - $2^{32}$
  - $2^{1024}$
* - $64K$
  - $4$
  - $16$
  - $2^{16}$
  - $16 \times 2^{16} = 2^{20}$
  - $2^{32}$
  - $2^{48}$
  - $2^{64K}$
* - $1M$
  - $\approx 4.3$
  - $20$
  - $2^{20}$
  - $20 \times 2^{20} = 2^{24}$
  - $2^{40}$
  - $2^{60}$
  - $2^{1M}$
* - $1G$
  - $\approx 4.9$
  - $30$
  - $2^{30}$
  - $30 \times 2^{30} = 2^{35}$
  - $2^{60}$
  - $2^{90}$
  - $2^{1G}$

```

````
``````````
