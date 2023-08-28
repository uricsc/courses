# OpenDSA

``` {card}
More math resources in the event you need them. The following are excerpts of content from the linked pages to the left.
```

## Logarithms

``` {card}

The logarithm of base $b$ for value $y$ is the power to which $b$ is raised to get $y$. Normally, this is written as $log_b\ y = x$. Thus, if $log_b\ y = x$ then $bx = y$, and $b\ log_b\ y = y$.

In OpenDSA, nearly all logarithms used have a base of two. This is because data structures and algorithms most often divide things in half, or store codes with binary bits. Whenever you see the notation $log\ n$ in OpenDSA, either $log_2\ n$ is meant or else the term is being used asymptotically and so the actual base does not matter. For logarithms using any base other than two, we will show the base explicitly.

Logarithms have the following properties, for any positive values of $m$, $n$, and $r$, and any positive integers $a$ and $b$.

$$  log(nm) = log\ n + log\ m  $$

$$  log(n/m) = log\ n − log\ m  $$

$$  log(n^r) = r\ log\ n  $$

$$  log_a\ n = \frac{log_b\ n}{log_b\ a}$$

```

## Summations

``` {card}

Most programs contain loop constructs. When analyzing running time costs for programs with loops, we need to add up the costs for each time the loop is executed. This is an example of a summation. Summations are simply the sum of costs for some function applied to a range of parameter values. Summations are typically written with the following “Sigma” notation:

$$\sum_{i = 1}^{n} f(i)$$

This notation indicates that we are summing the value of $f(i)$ over some range of (integer) values. The parameter to the expression and its initial value are indicated below the $\sum$ symbol. Here, the notation $i = 1$ indicates that the parameter is $i$ and that it begins with the value $1$. At the top of the $\sum$ symbol is the expression $n$. This indicates the maximum value for the parameter i. Thus, this notation means to sum the values of $f(i)$ as $i$ ranges across the integers from 1 through n. This can also be written $f(1)+f(2)+ \dots +f(n−1)+f(n)$. Within a sentence, Sigma notation is typeset as $\sum_{i = 1}^{n} f(i)$.

Given a summation, you often wish to replace it with an algebraic equation with the same value as the summation. This is known as a closed-form solution, and the process of replacing the summation with its closed-form solution is known as solving the summation. For example, the summation $\sum_{i = 1}^{n} 1$ is simply the expression “1” summed n times (remember that $i$ ranges from $1$ to $n$). Because the sum of $n$ 1s is $n$, the closed-form solution is $n$.

```

## Recurrence Relations

``` {card}
The running time for a recursive algorithm is most easily expressed by a recursive expression because the total time for the recursive algorithm includes the time to run the recursive call(s). A recurrence relation defines a function by means of an expression that includes one or more (smaller) instances of itself. A classic example is the recursive definition for the factorial function:

$$n!=(n−1)!⋅n for n>1;1!=0!=1$$.

Another standard example of a recurrence is the Fibonacci sequence:

$$Fib(n)=Fib(n−1)+Fib(n−2) for n>2;Fib(1)=Fib(2)=1$$

From this definition, the first seven numbers of the Fibonacci sequence are

$$1,1,2,3,5,8,\ and\ 13$$

Notice that this definition contains two parts: the general definition for $Fib(n)$ and the base cases for $Fib(1)$ and $Fib(2)$. Likewise, the definition for factorial contains a recursive part and base cases.

Recurrence relations are often used to model the cost of recursive functions. For example, the number of multiplications required by a recursive version of the factorial function for an input of size $n$ will be zero when $n = 0$ or $n = 1$ (the base cases), and it will be one plus the cost of calling fact on a value of $n − 1$. This can be defined using the following recurrence:

$$ T(n) = T(n−1) + 1\ for\ n > 1; $$
$$ T(0) = T(1) = 0 $$
```

## Mathematical Proof Techniques

``` {card}
Solving any problem has two distinct parts: the investigation and the argument. Students are too used to seeing only the argument in their textbooks and lectures. But to be successful in school (and in life after school), one needs to be good at both, and to understand the differences between these two phases of the process. To solve the problem, you must investigate successfully. That means engaging the problem, and working through until you find a solution. Then, to give the answer to your client (whether that “client” be your instructor when writing answers on a homework assignment or exam, or a written report to your boss), you need to be able to make the argument in a way that gets the solution across clearly and succinctly. The argument phase involves good technical writing skills—the ability to make a clear, logical argument.

Being conversant with standard proof techniques can help you in this process. Knowing how to write a good proof helps in many ways. First, it clarifies your thought process, which in turn clarifies your explanations. Second, if you use one of the standard proof structures such as proof by contradiction or an induction proof, then both you and your reader are working from a shared understanding of that structure. That makes for less complexity to your reader to understand your proof, because the reader need not decode the structure of your argument from scratch.

This section briefly introduces three commonly used proof techniques:

- deduction, or direct proof;

- proof by contradiction and

- proof by mathematical induction.

In general, a direct proof is just a “logical explanation”. A direct proof is sometimes referred to as an argument by deduction. This is simply an argument in terms of logic.
```