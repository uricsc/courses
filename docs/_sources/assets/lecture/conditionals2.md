
# [Conditionals]()

<style>
    iframe {width:100%;height:600px;}
</style>

```` {div} full-width
``` {figure} https://files.realpython.com/media/t.78f3bacaa261.png
:width: 450
```
````

## [Overview]()

`````````` {div} full-width

``` {admonition} Definition
:class: seealso

> Conditional statements are essential programming constructs that allow us to make decisions based on certain conditions. These statements evaluate an expression and execute specific code blocks based on whether the condition is true or false. The most common conditional statements are `if`, `else if`, `else`, nested `if`, and `switch`.

```

````` {admonition} Use Cases
:class: tip

```` {grid}
```  {grid-item} 
:columns: 4
Decision-making
: Executing different code based on specific conditions.
```
```  {grid-item} 
:columns: 4
Input Validation
: Checking user input for validity before processing it.
```
```  {grid-item} 
:columns: 4
Flow Control
: Controlling program flow based on conditions.
```
```  {grid-item} 
:columns: 4
Error Handling
: Handling specific error conditions.
```
```  {grid-item} 
:columns: 4
Menu Selection
: Implementing menu-driven applications.
```

````
`````

````````` {admonition} Pros & Cons
:class: warning

```````` {grid}
```````  {grid-item}
```` {card} 👍
``` {dropdown} Improved Control
Allows the program to make dynamic decisions during runtime.
```
``` {dropdown} Readable Code
Conditional statements enhance code readability by expressing intent clearly.
```
``` {dropdown} Saves Resources
Prevents unnecessary execution of code, optimizing resource utilization.
```
````
```````
```````  {grid-item}
```` {card} 👎
``` {dropdown} Complexity
Multiple nested conditions can make code harder to maintain and understand.
```
``` {dropdown} Code Duplication
Repeating code blocks for similar conditions can lead to code duplication.
```
``` {dropdown} Potential Bugs
Incorrect conditions or missing cases can introduce bugs.
```
````
```````
````````
`````````
``````````

### `if`, `else if`, `else` Syntax

`````````` {div} full-width
`````````  {card}

```````    {tab-set}
``````     {tab-item} Pseudocode

<iframe src="https://www.youtube.com/embed/osuzDDlBmRI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext

```

``````
``````     {tab-item} C++

<iframe src="https://www.youtube.com/embed/TOx3tPJircc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 9,11,13

#include <iostream>
using namespace std;

int main() {
    int exam_score;
    int passing_threshold = 60;

    cout << "Enter your exam score: ";
    cin >> exam_score;

    if (exam_score >= passing_threshold) {
        cout << "Congratulations! You passed the exam." << endl;
    } else {
        cout << "Unfortunately, you did not pass the exam. Please try again." << endl;
    }

    return 0;
}

```

``````
``````     {tab-item} Python

<iframe src="https://www.youtube.com/embed/NkVSSMt-h3Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} python
:lineno-start: 1
:emphasize-lines: 1-2,6

passing_threshold = 60

exam_score = int(input("Enter your exam score: "))

if exam_score >= passing_threshold:
    print("Congratulations! You passed the exam.")
else:
    print("Unfortunately, you did not pass the exam. Please try again.")

```

``````
``````     {tab-item} Java

<iframe src="https://www.youtube.com/embed/P6ivQ3QRq0I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} java
:lineno-start: 1
:emphasize-lines: 3-5,9

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int passing_threshold = 60;

        System.out.print("Enter your exam score: ");
        int exam_score = scanner.nextInt();

        if (exam_score >= passing_threshold) {
            System.out.println("Congratulations! You passed the exam.");
        } else {
            System.out.println("Unfortunately, you did not pass the exam. Please try again.");
        }
    }
}

```

``````
``````     {tab-item} Rust

<iframe src="https://www.youtube.com/embed/MOa7ulhNYc0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} rust
:lineno-start: 1
:emphasize-lines: 1-3,8

use std::io;

fn main() {
    let passing_threshold = 60;

    println!("Enter your exam score: ");
    let mut input = String::new();
    io::stdin().read_line(&mut input).expect("Failed to read line");
    let exam_score: i32 = input.trim().parse().expect("Please enter a valid number");

    if exam_score >= passing_threshold {
        println!("Congratulations! You passed the exam.");
    } else {
        println!("Unfortunately, you did not pass the exam. Please try again.");
    }
}

```

``````
``````     {tab-item} Golang

<iframe src="https://www.youtube.com/embed/Hjqjff490B8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} golang
:lineno-start: 1
:emphasize-lines: 5-7,12

package main

import (
    "fmt"
)

func main() {
    var passing_threshold int = 60
    var exam_score int

    fmt.Print("Enter your exam score: ")
    fmt.Scan(&exam_score)

    if exam_score >= passing_threshold {
        fmt.Println("Congratulations! You passed the exam.")
    } else {
        fmt.Println("Unfortunately, you did not pass the exam. Please try again.")
    }
}

```

``````
```````

<!-- TODO : UPDATE OUTPUT FOR CONSISTENCY WITH THE SAMPLES -->

```` {admonition} Output
:class: important, dropdown

> We prompt the user to enter their exam score and compare it with the `passing_threshold` value of `60`. If the `exam_score` is greater than or equal to `60`, the program outputs a success message indicating that the student passed the exam. Otherwise, it prints a message stating that the student did not pass and should try again.
>
> Assume the user enters `75` as input for all the examples.
>
> Since the input `75` is greater than the passing threshold of `60`, the output is: `Congratulations! You passed the exam.``.

``` {code-block} bash
Congratulations! You passed the exam.
```

````


`````````
``````````

### `switch` / `match` Syntax

`````````` {div} full-width
`````````  {card}
<!-- 
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20230329132110/Java-For-loop-with-Examples-1.png

The for loop is used when the number of iterations is known in advance. It consists of three parts: initialization, condition, and iteration.
``` -->

```````    {tab-set}
``````     {tab-item} Pseudocode

<iframe src="https://www.youtube.com/embed/A30EM-ARYTA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
FUNCTION name_of_function (parameter1, parameter2, ...):
    // Function implementation here
    RETURN result
```

``````
``````     {tab-item} C++

<iframe src="https://www.youtube.com/embed/r2pWRvxhTqk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Rules of Use
: 

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 9,11,13

#include <iostream>
using namespace std;

int main() {
    int day_number;

    cout << "Enter a day number (1 to 7): ";
    cin >> day_number;

    switch (day_number) {
        case 1:
            cout << "Sunday" << endl;
            break;
        case 2:
            cout << "Monday" << endl;
            break;
        case 3:
            cout << "Tuesday" << endl;
            break;
        case 4:
            cout << "Wednesday" << endl;
            break;
        case 5:
            cout << "Thursday" << endl;
            break;
        case 6:
            cout << "Friday" << endl;
            break;
        case 7:
            cout << "Saturday" << endl;
            break;
        default:
            cout << "Invalid day number. Please enter a number between 1 and 7." << endl;
            break;
    }

    return 0;
}

```

``````
``````     {tab-item} Python

<iframe src="https://www.youtube.com/embed/RvW1zJcd6oA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Rules of Use
: 

``` {code-block} python
:lineno-start: 1
:emphasize-lines: 1-2,6

day_number = int(input("Enter a day number (1 to 7): "))

if day_number == 1:
    print("Sunday")
elif day_number == 2:
    print("Monday")
elif day_number == 3:
    print("Tuesday")
elif day_number == 4:
    print("Wednesday")
elif day_number == 5:
    print("Thursday")
elif day_number == 6:
    print("Friday")
elif day_number == 7:
    print("Saturday")
else:
    print("Invalid day number. Please enter a number between 1 and 7.")

```

``````
``````     {tab-item} Java

<iframe src="https://www.youtube.com/embed/xL0O22dTTW8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Rules of Use
: 

``` {code-block} java
:lineno-start: 1
:emphasize-lines: 3-5,9

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int day_number;

        System.out.print("Enter a day number (1 to 7): ");
        day_number = scanner.nextInt();

        switch (day_number) {
            case 1:
                System.out.println("Sunday");
                break;
            case 2:
                System.out.println("Monday");
                break;
            case 3:
                System.out.println("Tuesday");
                break;
            case 4:
                System.out.println("Wednesday");
                break;
            case 5:
                System.out.println("Thursday");
                break;
            case 6:
                System.out.println("Friday");
                break;
            case 7:
                System.out.println("Saturday");
                break;
            default:
                System.out.println("Invalid day number. Please enter a number between 1 and 7.");
                break;
        }
    }
}

```

``````
``````     {tab-item} Rust

<iframe src="https://www.youtube.com/embed/OkR__wxWrG0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Rules of Use
: 

``` {code-block} rust
:lineno-start: 1
:emphasize-lines: 1-3,8

use std::io;

fn main() {
    let mut day_number = String::new();

    println!("Enter a day number (1 to 7): ");
    io::stdin().read_line(&mut day_number).expect("Failed to read line");
    let day_number: i32 = day_number.trim().parse().expect("Please enter a valid number");

    match day_number {
        1 => println!("Sunday"),
        2 => println!("Monday"),
        3 => println!("Tuesday"),
        4 => println!("Wednesday"),
        5 => println!("Thursday"),
        6 => println!("Friday"),
        7 => println!("Saturday"),
        _ => println!("Invalid day number. Please enter a number between 1 and 7."),
    }
}

```

``````
``````     {tab-item} Golang

<iframe src="https://www.youtube.com/embed/l6zlJFJst8o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Rules of Use
: 

``` {code-block} golang
:lineno-start: 1
:emphasize-lines: 5-7,12

package main

import (
    "fmt"
)

func main() {
    var day_number int

    fmt.Print("Enter a day number (1 to 7): ")
    fmt.Scan(&day_number)

    switch day_number {
    case 1:
        fmt.Println("Sunday")
    case 2:
        fmt.Println("Monday")
    case 3:
        fmt.Println("Tuesday")
    case 4:
        fmt.Println("Wednesday")
    case 5:
        fmt.Println("Thursday")
    case 6:
        fmt.Println("Friday")
    case 7:
        fmt.Println("Saturday")
    default:
        fmt.Println("Invalid day number. Please enter a number between 1 and 7.")
    }
}

```

``````
```````

<!-- TODO : UPDATE OUTPUT FOR CONSISTENCY WITH THE SAMPLES -->

```` {admonition} Output
:class: important, dropdown

> We take a user input for the day_number and use a switch statement (or if-elif statements in Python) to display the corresponding day of the week. Assuming the user input is `3`, the output for each program is `Tuesday`.

``` {code-block} bash
Tuesday
```

````


`````````
``````````
<!-- 
## Compare & Contrast

````````` {div} full-width
````````  {card}

``````    {list-table}
:header-rows: 1

* - Language
  - Similarities
  - Differences
  - Limitations
* - C++ 
  - \- Supports return type and parameter declaration.<br>- Functions can have default arguments.<br>- Allows function overloading (same name, different parameters).<br>- Can be used in object-oriented programming paradigm.
  - \- Requires explicit data types for parameters and return values.<br>- Uses the `return` keyword to return values.<br>- Supports function pointers and function overloading.
  - \- Limited support for built-in error handling mechanisms.<br>- No native support for closures and anonymous functions.<br>- Lack of strict memory safety, prone to memory-related bugs.
* - Python
  - \- Supports return type and parameter declaration.<br>- Functions can have default arguments and keyword arguments.<br>- Allows function overloading (using default arguments).<br>- Supports lambda functions and closures.
  - \- Uses indentation to define function blocks.<br>- Uses the `def` keyword to define functions.<br>- No requirement for explicit data type declaration.<br>- Uses `return` statement to return values.
  -	\- Dynamic typing may lead to run-time errors.<br>- Lack of strict typing may affect code maintainability.<br>- Global interpreter lock (GIL) may limit multi-threading performance.
* - Java
  - \- Supports return type and parameter declaration.<br>- Supports method overloading (same name, different parameters).<br>- Strongly typed language, requiring explicit data types.<br>- Follows object-oriented programming paradigm.
  - \- Functions must be defined within classes (except static methods).<br>- Uses the return keyword to return values.<br>- Requires objects to call non-static methods.
  - \- Verbosity in syntax compared to other languages.<br>- Lack of support for first-class functions and closures.<br>- Boilerplate code for even simple tasks.
* - Rust
  - \- Supports return type and parameter declaration.<br>- Supports functions with explicit data types.<br>- Functions can have default and variable arguments.<br>- Allows function overloading using traits.
  - \- Uses the `fn` keyword to define functions.<br>- Utilizes `->` to specify return type.<br>- Ownership and borrowing system for memory safety.<br>- Allows closure types and function pointers.
  - \- Learning curve due to strict borrow checker and lifetimes.<br>- Lack of garbage collector may require manual memory management.<br>- Limited standard library compared to mature languages.
* - Golang
  - \- Supports return type and parameter declaration.<br>- Functions can have multiple return values.<br>- Functions are first-class citizens (can be passed as arguments).<br>- Supports closures and anonymous functions.
  - \- Uses the `func` keyword to define functions.<br>- Requires explicit data types for parameters and return values.<br>No requirement for `return` keyword.
  - \- Lack of support for traditional object-oriented programming.<br>- Lack of generics until Go 2 is released.<br>- Less expressive syntax compared to other languages.

``````    

*Notes*
: *Similarities* refer to common features or functionalities shared among the languages.  
: *Differences* highlight distinct aspects of functions in each respective language.  
: *Limitations* mention potential drawbacks or restrictions that developers might face when working with functions in these languages.

```````` 
````````` -->