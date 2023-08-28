# Analysis of Algorithms

`````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/RctntWQjazw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
The analysis of algorithms and data structures are two fundamental areas of computer science that are closely related. An algorithm is a step-by-step procedure for solving a computational problem, while a data structure is a way of organizing and storing data in a computer program. The choice of algorithm and data structure can significantly impact the performance of a program.

The analysis of algorithms involves the study of the efficiency and performance of algorithms, typically measured in terms of time complexity and space complexity. Time complexity refers to the amount of time it takes for an algorithm to solve a problem as the input size grows larger. Space complexity refers to the amount of memory an algorithm requires to solve a problem.

Data structures are used to store and organize data in a way that allows efficient access and manipulation. The choice of data structure can have a significant impact on the performance of an algorithm. For example, if a program needs to frequently search and retrieve items from a collection, a hash table or a binary search tree might be a more efficient data structure than a linked list.

Together, the analysis of algorithms and data structures are essential for designing and implementing efficient computer programs. By choosing the best algorithms and data structures for a given problem, programmers can significantly improve the performance and scalability of their software.
```

``` {card} Additional Resources
- [Space Complexity of Algorithms - How to Calculate Space Complexity of Algorithms in Data Structures | Simple Snippets](https://www.youtube-nocookie.com/embed/89LxbPzHEaw)
- [What Are Algorithms? - Algorithms & Data Structures #2 | NeuralNine](https://youtu.be/89LxbPzHEaw)
```
`````
`````` {grid}
`````  {grid-item}
``` {admonition} Problem?
:class: dropdown
- a task to be performed
- best thought in terms of (well-defined) inputs and outputs
- problem definition does not impose constraints on how the problem is solved but often includes resource constraints
```
`````
````` {grid-item}
``` {admonition} Algorithm?
:class: dropdown
- a sequence of steps followed to solve a problem
- it must be correct and composed of a finite number of concrete steps
- there can be no ambiguity
- it must terminate
```
````` 
````` {grid-item}
``` {admonition} Program?
:class: dropdown
- a representation of an algorithm in some programming language
```
`````

``````
``````````

<!-- ## Problem, algorithm, and program

`````````` {div} full-width
```````` {card}
``` {image} https://evatronix.com/images/en/offer/product-design/product-development/Evatronix_Algorithm_development_and_analysis_01_800x450.jpg
:align: center
```

````````
`````````` -->

## Analysis of algorithms

`````````` {div} full-width
````` {card}
```` {card}

``` {epigraph} **Algorithms**

“Any well-defined computational procedure that takes some value, or set of values, as input and produces some value, or set of values, as output.”

-- [Cormen et al., Introduction to Algorithms, 3rd.Ed.]

```
````
```` {card} Resources necessary to execute an algorithm?
- Time Complexity (running time)
- Space Complexity (memory)

_Resources typically depend on input size_

````

`````
``````````

## Developing a usable algorithm

`````````` {div} full-width

`````````  {grid} 
````````   {grid-item-card}
:columns: 5

**The building blocks of algorithms**

> An **algorithm** is a step by step process that describes how to solve a problem in a way that always gives a correct answer. When there are multiple algorithms for a particular problem (and there often are!), the best algorithm is typically the one that solves it the fastest.
> 
> As computer programmers, we are constantly using algorithms, whether it's an existing algorithm for a common problem, like sorting an array, or if it's a completely new algorithm unique to our program. By understanding algorithms, we can make better decisions about which existing algorithms to use and learn how to make new algorithms that are correct and efficient.
An algorithm is made up of three basic building blocks: sequencing, selection, and iteration.
> 
> -- [Khan Academy](https://www.khanacademy.org/computing/ap-computer-science-principles/algorithms-101/building-algorithms/a/the-building-blocks-of-algorithms)
````````

```````` {grid-item-card}
:columns: 7

``` {figure} img/w1_algo_design.png
:width: 75%

COS 226 lectures, Princeton University
```

````````
````````   {grid-item-card}
:columns: 4

> **Sequencing**: An algorithm is a step-by-step process, and the order of those steps are crucial to ensuring the correctness of an algorithm.
>
> -- [Khan Academy](https://www.khanacademy.org/computing/ap-computer-science-principles/algorithms-101/building-algorithms/a/the-building-blocks-of-algorithms)
````````
````````   {grid-item-card}
:columns: 4

> **Selection**: Algorithms can use selection to determine a different set of steps to execute based on a Boolean expression.
>
> -- [Khan Academy](https://www.khanacademy.org/computing/ap-computer-science-principles/algorithms-101/building-algorithms/a/the-building-blocks-of-algorithms)
````````
````````   {grid-item-card}
:columns: 4

> **Iteration**: Algorithms often use repetition to execute steps a certain number of times or until a certain condition is met.
>
> -- [Khan Academy](https://www.khanacademy.org/computing/ap-computer-science-principles/algorithms-101/building-algorithms/a/the-building-blocks-of-algorithms)
````````
`````````

```` {admonition} Example from CS50
:class: dropdown tip
<iframe width="560" height="315" src="https://www.youtube.com/embed/okkIyWhN0iQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``````````

## Why analyze algorithms?

`````````` {div} full-width
```` {card}
``` {card}
- Classify algorithms/problems
- Predict performance/resources
- Provide guarantees
- Understand underlying principles of problems
- and...
```

``` {figure} img/w3_01.png
:width: 100%
What do these all have in common?
```

````
``````````

## Analyzing computational cost

`````````` {div} full-width
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
``````````

## Empirical analysis (timing)

`````````` {div} full-width
``` {card}

- Implement algorithm
- Run on different input sizes
- Record actual running times
- Calculate hypothesis
- Predict and validate

```
``````````

## Timing Algorithms

`````````` {div} full-width
```````` {admonition} Example 1
:class: important

``````` {grid}

``````{grid-item-card} [Euler's Number](https://www.mathsisfun.com/numbers/e-eulers-number.html)
:columns: 8
```{card} 
... mathematical constant that is the base of the natural logarithm. It is approximately equal to 2.71828.
```
``` {card} [$e$](https://youtu.be/m2MIpDrF7Es)
$$
\begin {align}
e & = \lim_{x\to \infty} \bigg(1 + \frac{1}{n} \bigg)^n \\
& = \frac{1}{0!} + \frac{1}{1!} + \frac{1}{2!} + \frac{1}{3!} + \frac{1}{4!} + \dotsb \\
& = 1 + \frac{1}{1} + \frac{1}{1 * 2} + \frac{1}{1 * 2 * 3} + \frac{1}{1 * 2 * 3 * 4} + \dots + \frac{1}{n!} \\
\end {align}
$$
```

```` {dropdown} Applications?
``` {epigraph}
Euler used the letter $e$ for exponents, but the letter is now widely associated with his name. It is commonly used in a wide range of applications, including population growth of living organisms and the radioactive decay of heavy elements like uranium by nuclear scientists. It can also be used in trigonometry, probability, and other areas of applied mathematics.

-- [https://www.investopedia.com/terms/e/eulers-constant.asp](https://www.investopedia.com/terms/e/eulers-constant.asp)
```
```` 
``````

``````{grid-item-card} Leonhard Euler (1707–1783)
:columns: 4
````{card} 
``` {figure} https://personajeshistoricos.com/wp-content/uploads/2018/04/Leonhard-Euler-2-785x1024.jpg
:width: 100%
a Swiss  mathematician, physicist, astronomer, geo  grapher, logician and engineer who made  important and influential discoveries in  many branches of mathematics.
```


````
``````
```````
``` {admonition} visualizations
:class: dropdown tip
<iframe src="https://opendsa-server.cs.vt.edu/embed/LinearRecurrencesCON" height="300" width="100%"></iframe>
<iframe src="https://opendsa-server.cs.vt.edu/embed/LinearRecurrencesNCON" height="300" width="100%"></iframe>
```
``````````

### Algorithms

`````````` {div} full-width
``````` {card} Which is more efficient?
````` {grid}

```` {grid-item-card} Algorithm 1
```{code-block} cpp
:lineno-start: 1
:emphasize-lines:

long double euler1 (int n) {
    long double sum = 0;
    long double fact;
    for (int i = 0; i <= n; i++) {
        fact = 1;
        for (int j = 2; j <= i; j++) {
            fact *= j; 
        }
        sum += (1.0/fact);
    }
    return sum;
}
```
````

````{grid-item-card} Algorithm 2
```{code-block} cpp
:lineno-start: 1
:emphasize-lines:

long double euler2 (int n) {
    long double sum = 0;
    long double fact = 1;
    for (int i = 0; i <= n; i++) {
        sum += (1.0/fact);
        fact *= (i + 1); 
    }
    return sum;
}
```
````

`````
```````

`````` {admonition} Example 2
:class: important

``` {figure} https://azcoinnews.com/wp-content/uploads/2019/11/1-8.jpg
:width: 100%
fibonacci
```

``` {card} [recurrence relation](https://byjus.com/maths/recurrence-relation/)
$$
F_0 & = 0 \\
F_1 & = 1 \\
F_n & = F_{n-1} + F_{n-2} \\
& = 0, 1, 1, 2, 3, 5, 8, 13, 21, 34 \dotsb
$$
```

````{card} Iterative
```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 5

uint64_t fibI(uint16_t n){
    uint64_t sum;
    uint64_t prev[] = {0,1};
    if (n < 2) return n;
    for (uint16_t i = 2; i <= n; i++) {
        sum = prev[0] + prev[1];
        prev[0] = prev[1];
        prev[1] = sum;
    }
    return sum;
}
```
````

```` {card} Recursive 
```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 2-3

uint64_t fibR (uint16_t n) {
    if (n < 2) return n;
    else return fibR(n-1) + fibR(n-2);
}
```
````

````{card} Timing...
```{code-block} cpp
:lineno-start: 1

void time_func(uint16_t n, const char *name) {
    uint64_t val;
    Clock::time_point tic,toc;
    if (! strcmp(name,"Iter")) {
        tic = Clock::now();
        val = fib_iter(n);
        toc = Clock::now();
    }
    if (! strcmp(name,"Rec")) {
        tic = Clock::now();
        val = fib_rec(n);
        toc = Clock::now();
    }
    std::cout << name << "fib(" << n << "):\t" 
              << std::fixed << std::setprecision(4) 
              << Seconds(toc-tic).count() << "sec.\tOutput:"
              << val << std::endl; 
}
    
int main (int argc, char** argv) {
    if (argc != 3) {
        std::cout << "Usage:./fib<n><alg>\n";
        std::cout << "\t<n>\tn-th term to be calculated\n";
        std::cout << "\t<alg>\t algorithm to be used(RecorIter)\n";
        return 0;
    }
    uint16_t n = (uint16_t)
    atoi(argv[1]);
    time_func(n,argv[2]);
}
```
````

```` {admonition} Outcomes
:class: dropdown

``` {figure} img/w3_02.png
:width: 100%
Iterative v. Recursive
```

Is this as expected?
````

````{admonition} Hypothesis
:class: dropdown

``` {figure} img/w3_03.png
:width: 100%
graph
```
Complete the graph, what would it look like?
````

``````
``````````

## Limitations of empirical analysis

`````````` {div} full-width
```` {card}
**Requires implementing several algorithms for the same problem**
- may be difficult and time consuming
- implementation details also play a role (one particular algorithm may be “better written”)
  
**Requires extensive testing**
- time consuming
- choice of test cases might favor one of the algorithms

**Variations in hardware, software, and operating system affect analysis**
````
``````````
