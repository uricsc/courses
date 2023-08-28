# [Jump Statements](https://www.geeksforgeeks.org/jump-statements-in-c/?ref=gcse)

```` {div} full-width
``` {figure} https://updatelab.files.wordpress.com/2016/08/jump-and-break-statements.jpeg?w=568
```
````

## [Overview]()

`````````` {div} full-width

``` {admonition} Definition
:class: seealso

> Jump statements are control flow statements used in programming languages to alter the normal sequence of execution. These statements allow programmers to control the flow of their code by transferring control to different parts of the program based on certain conditions

```

````` {admonition} Use Cases
:class: tip

```` {grid}
```  {grid-item} 
:columns: 4

`break`
: Terminates the innermost loop or switch statement and transfers control to the statement immediately following the loop or switch.
```
```  {grid-item} 
:columns: 4

`continue`
: Skips the remaining statements in the current iteration of a loop and proceeds to the next iteration.
```
```  {grid-item} 
:columns: 4

`goto`
: Unconditionally transfers control to a specified label within the current function.

```

````
`````




````````` {admonition} Pros & Cons
:class: warning

```````` {grid}
```````  {grid-item}

```` {card} 👍

``` {dropdown} Concise Controls [All]
`break` and `continue` statements provide a concise way to control loops and switch statements, improving code readability and efficiency.
```
``` {dropdown} Flexible Flow [C++]
The `goto` statement, although controversial, allows for flexible control flow in certain situations.
```
``` {dropdown} Passing Values [Python]
The `return` statement allows functions to pass values back to the caller.
```
``` {dropdown} Exit Flow [Rust & Go]
The `return` statement allows functions to exit early and return values.
```
````
```````
```````  {grid-item}


```` {card} 👎
``` {dropdown} Overuse & Misuse [All]
Overusing `break`, `continue`, or `goto` statements can make code harder to read and understand, leading to potential bugs and maintenance issues, as well as unexpected behavior and infinite loops.


```
``` {dropdown} Spaghetti Code [C++]
The `goto` statement can create spaghetti code and make the program harder to maintain and debug.
```
``` {dropdown} Convoluted Logic [Rust & Go]
Relying too heavily on `return` statements may result in convoluted program logic and reduced maintainability.
```
````

```````


````````


`````````
``````````

### `continue` & `break` statements

`````````` {div} full-width
`````````  {card}
<!-- 
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20230329132110/Java-For-loop-with-Examples-1.png

The for loop is used when the number of iterations is known in advance. It consists of three parts: initialization, condition, and iteration.
``` -->

```````    {tab-set}
``````     {tab-item} Pseudocode

<iframe width="100%" height="600" src="https://www.youtube.com/embed/21l11_9Osd0?start=771" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
start loop
- process statement(s)/task(s) until condition is met
  - continue    // process moves forward within the loop
  - break       // breaks out of the loop and moves to the next instruction
end for loop
```

``````
``````     {tab-item} C++

<iframe width="100%" height="600" src="https://www.youtube.com/embed/yS8DUrQy_ow" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 7, 11

#include <iostream>
using namespace std;

void jumpStatementsExample() {
    for (int i = 0; i < 5; i++) {
        if (i == 2) {
            continue; // Skip the rest of the loop body for i = 2
        }
        cout << i << endl;
        if (i == 3) {
            break; // Terminate the loop when i = 3
        }
    }
}

int main() {
    jumpStatementsExample();
    return 0;
}


```

``````
``````     {tab-item} Python

<iframe width="100%" height="600" src="https://www.youtube.com/embed/KWgYha0clzw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} python
:lineno-start: 1
:emphasize-lines: 4,7

def jump_statements_example():
    for i in range(5):
        if i == 2:
            continue  # Skip the rest of the loop body for i = 2
        print(i)
        if i == 3:
            break  # Terminate the loop when i = 3

jump_statements_example()

```

``````
``````     {tab-item} Java

<iframe width="100%" height="600" src="https://www.youtube.com/embed/VJnSheKQc4U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} java
:lineno-start: 1
:emphasize-lines: 10,14,25

public class JumpStatementsExample {

    public static void main(String[] args) {
        jumpStatementsExample();
    }

    public static void jumpStatementsExample() {
        for (int i = 0; i < 5; i++) {
            if (i == 2) {
                continue; // Skip the rest of the loop body for i = 2
            }
            System.out.println(i);
            if (i == 3) {
                break; // Terminate the loop when i = 3
            }
        }

        int result = performCalculation();
        System.out.println("Result: " + result);
    }

    public static int performCalculation() {
        for (int i = 0; i < 5; i++) {
            if (i == 2) {
                return i * 2; // Exit the function and return a value for i = 2
            }
            System.out.println("Calculation: " + i);
        }
        return 0;
    }
}

```

``````
``````     {tab-item} Rust

<iframe width="100%" height="600" src="https://www.youtube.com/embed/gtoj6vOeb1A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} rust
:lineno-start: 1
:emphasize-lines: 4,8

fn jump_statements_example() {
    for i in 0..5 {
        if i == 2 {
            continue; // Skip the rest of the loop body for i = 2
        }
        println!("{}", i);
        if i == 3 {
            break; // Terminate the loop when i = 3
        }
    }
}

fn main() {
    jump_statements_example();
}

```

``````
``````     {tab-item} Golang

<iframe width="100%" height="600" src="https://www.youtube.com/embed/CL13xV2dHCg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} golang
:lineno-start: 1
:emphasize-lines: 8,12

package main

import "fmt"

func jumpStatementsExample() {
    for i := 0; i < 5; i++ {
        if i == 2 {
            continue // Skip the rest of the loop body for i = 2
        }
        fmt.Println(i)
        if i == 3 {
            break // Terminate the loop when i = 3
        }
    }
}

func main() {
    jumpStatementsExample()
}


```

``````
```````

```` {admonition} Output
:class: important, dropdown

> The loop initializes the variable `i` to `0`, checks the condition `i <= 4`, executes the code block, increments `i` by `1`, and repeats the process until the condition is no longer `true`.

``` {code-block} bash
Value of i: 0
Value of i: 1
Value of i: 2
Value of i: 3
Value of i: 4
```

````


`````````
``````````


### `while` loop

`````````` {div} full-width
`````````  {card}
<!-- 
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20230329132110/Java-For-loop-with-Examples-1.png

The for loop is used when the number of iterations is known in advance. It consists of three parts: initialization, condition, and iteration.
``` -->

```````    {tab-set}
``````     {tab-item} Pseudocode

<iframe width="100%" height="600" src="https://www.youtube.com/embed/U_e7DTZCIM8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
start while loop
- while condition is true
  - continue some task(s) until condition is false
- condition is false
  - break loop
end while loop
```

``````
``````     {tab-item} C++

<iframe width="100%" height="600" src="https://www.youtube.com/embed/iF4i423144E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` cpp
#include <iostream>

int main() {
    int i = 0;
    while (i <= 4) {
        std::cout << "Value of i: " << i << std::endl;
        i++;
    }
    return 0;
}


```

``````
``````     {tab-item} Python

<iframe width="100%" height="600" src="https://www.youtube.com/embed/ECduJk00mUU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` python
i = 0
while i <= 4:
    print("Value of i:", i)
    i += 1

```

``````
``````     {tab-item} Java

<iframe width="100%" height="600" src="https://www.youtube.com/embed/ECduJk00mUU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` java
i = 0
while i <= 4:
    print("Value of i:", i)
    i += 1

```

``````
``````     {tab-item} Rust

<iframe width="100%" height="600" src="https://www.youtube.com/embed/OaEXxpELfvw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` rust

fn main() {
    let mut i = 0;
    while i <= 4 {
        println!("Value of i: {}", i);
        i += 1;
    }
}

```

``````
``````     {tab-item} Golang

<iframe width="100%" height="600" src="https://www.youtube.com/embed/1yGom0Yt1xk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` golang
package main

import "fmt"

func main() {
    i := 0
    for i <= 4 {
        fmt.Println("Value of i:", i)
        i++
    }
}


```

``````
```````

```` {admonition} Output
:class: important, dropdown

> The loop initializes the variable `i` to `0`, checks the condition `i <= 4`, executes the code block, increments `i` by `1`, and repeats the process until the condition is no longer `true`.

``` {code-block} bash
Value of i: 0
Value of i: 1
Value of i: 2
Value of i: 3
Value of i: 4
```

````


`````````
``````````

## Exit Controlled

`````````` {div} full-width

> An exit-controlled loop, also known as a post-test loop, evaluates the loop condition after executing the loop body. This means that the loop body is guaranteed to execute at least once, even if the condition is initially false.
>
> The loop body is executed first, and then the loop condition is checked. If the condition is true, the loop body is executed again for the next iteration. If the condition becomes false, the loop is terminated, and the program continues execution after the loop.

``````````



### `do while` loop

`````````` {div} full-width
`````````  {card}
<!-- 
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20230329132110/Java-For-loop-with-Examples-1.png

The for loop is used when the number of iterations is known in advance. It consists of three parts: initialization, condition, and iteration.
``` -->

```````    {tab-set}
``````     {tab-item} Pseudocode

<iframe width="100%" height="600" src="https://www.youtube.com/embed/v-K-4KuA8mQ?start=220" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
start while loop
- complete task(s) in loop once
- while condition is true
  - continue some task(s) until condition is false
- condition is false
  - break loop
end while loop
```

``````
``````     {tab-item} C++

<iframe width="100%" height="600" src="https://www.youtube.com/embed/TjkJQly2YCw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` cpp
#include <iostream>

int main() {
    int i = 0;
    do {
        std::cout << "Value of i: " << i << std::endl;
        i++;
    } while (i <= 4);
    return 0;
}

```

``````
``````     {tab-item} Python

<iframe width="100%" height="600" src="https://www.youtube.com/embed/6vPHm7z_n0M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` python
i = 0
while True:
    print("Value of i:", i)
    i += 1
    if i > 4:
        break

```

``````
``````     {tab-item} Rust

``` {figure} https://res.cloudinary.com/teepublic/image/private/s--nY05dwdm--/t_Preview/b_rgb:ffffff,c_lpad,f_jpg,h_630,q_90,w_1200/v1536944098/production/designs/3155319_0.jpg
:width: 100%

```

``` rust
// Does not exist in Rust...

```

``````
``````     {tab-item} Golang

<iframe width="100%" height="600" src="https://www.youtube.com/embed/UHE6cMZdF1U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` golang
package main

import "fmt"

func main() {
    i := 0
    for {
        fmt.Println("Value of i:", i)
        i++
        if i > 4 {
            break
        }
    }
}

```

``````
```````

```` {admonition} Output
:class: important, dropdown

> The loop initializes the variable `i` to `0`, checks the condition `i <= 4`, executes the code block, increments `i` by `1`, and repeats the process until the condition is no longer `true`.

``` {code-block} bash
Value of i: 0
Value of i: 1
Value of i: 2
Value of i: 3
Value of i: 4
```

````


`````````
``````````


## Compare & Contrast

````````` {div} full-width
````````  {card}

``````    {list-table}
:header-rows: 1

* - Language
  - `continue` 
  - `break`
  - `return`
  - `labeled break`
* - C++ 
  - Works in loops (for, while, do-while) and skips the current iteration.
  - Terminates the innermost loop or switch statement and transfers control to the statement immediately following the loop or switch.
  - Exits the current function and returns a value (optional).
  - Can use the `goto` statement to transfer control to a labeled statement within the same function (controversial usage).
* - Python
  - Works in loops (for, while) and skips the current iteration.	
  - Terminates the innermost loop (for loop or while loop) and transfers control to the statement immediately following the loop.	
  - Exits the current function and returns a value (optional).	
  - Does not support a direct labeled break statement, but can achieve similar behavior using boolean flags or exception handling.
* - Java
  - Works in loops (for, while, do-while) and skips the current iteration.
  - Terminates the innermost loop or switch statement and transfers control to the statement immediately following the loop or switch.
  - Exits the current function and returns a value (optional).
  - Can be used to break out of nested loops using a labeled identifier.
* - Rust
  - Works in loops (for, while) and skips the current iteration.	
  - Terminates the innermost loop and transfers control to the statement immediately following the loop.	
  - Exits the current function and returns a value (optional).	
  - Does not have a direct `labeled break` statement, but can use the `loop` construct with `break` and a label to achieve similar behavior.
* - Golang
  - Works in loops (for) and skips the current iteration.	
  - Terminates the innermost loop and transfers control to the statement immediately following the loop.	
  - Exits the current function and returns a value (optional).	
  - Supports labeled break statements to break out of nested loops using a labeled identifier.


``````    

```````` 
`````````