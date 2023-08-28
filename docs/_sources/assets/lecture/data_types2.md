
# [Data Types]()

<style>
    iframe {width:100%;height:600px;}
</style>


<!-- TODO : HERO IMAGE -->
`````````` {div} full-width
``` {figure} https://media.geeksforgeeks.org/wp-content/cdn-uploads/20191113115600/DatatypesInC.png

```
``````````

## [Overview]()

`````````` {div} full-width

``` {admonition} Definition
:class: seealso

> Data types in programming languages represent the type of data that can be stored in variables. They define the size, memory allocation, and operations that can be performed on the data. Common data types include integers, floating-point numbers, characters, strings, booleans, and more complex types like arrays and structures.

```

````` {admonition} Use Cases
:class: tip

Data types are essential for defining variables and data structures to hold different kinds of information in a program. They help enforce constraints on data and enable efficient memory management and manipulation.

`````

````````` {admonition} Pros & Cons
:class: warning

```````` {grid}
```````  {grid-item}
```` {card} 👍
``` {dropdown} Type Safety
Data types help catch type-related errors at compile-time, enhancing code reliability.
```
``` {dropdown} Memory Optimization
Choosing appropriate data types can optimize memory usage.
```
``` {dropdown} Performance
Properly selected data types improve the execution speed of programs.
```
``` {dropdown} Code Clarity
Explicit data types make code more readable and self-documenting.
```
````
```````
```````  {grid-item}
```` {card} 👎
``` {dropdown} Type Constraints
Incorrectly chosen data types can lead to unnecessary restrictions or potential errors.
```
``` {dropdown} Memory Overhead
In certain situations, using larger data types can lead to memory waste.
```
``` {dropdown} Conversion Overhead
Implicit type conversions can lead to performance overhead in some cases.
```
````
```````
````````
`````````
``````````

### Syntax

`````````` {div} full-width
`````````  {card}

```````    {tab-set}

``````     {tab-item} Pseudocode

<iframe src="https://www.youtube.com/embed/p98cayTo1Go" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
input length, width
area = length * width
print area
```

``````

``````     {tab-item} C++

<iframe src="https://www.youtube.com/embed/7zlRqvbuCGU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 5,7,9

#include <iostream>
using namespace std;

int main() {
    double length, width;
    cout << "Enter length: ";
    cin >> length;
    cout << "Enter width: ";
    cin >> width;

    double area = length * width;
    cout << "Area of the rectangle: " << area << endl;

    return 0;
}

```

``````

``````     {tab-item} Python

<iframe src="https://www.youtube.com/embed/gCCVsvgR2KU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} python
:lineno-start: 1
:emphasize-lines: 1-2,6

length = float(input("Enter length: "))
width = float(input("Enter width: "))

area = length * width
print("Area of the rectangle:", area)

```

``````

``````     {tab-item} Java

<iframe src="https://www.youtube.com/embed/Le25I331_yU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} java
:lineno-start: 1
:emphasize-lines: 3-5,9

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double length, width;
        System.out.print("Enter length: ");
        length = scanner.nextDouble();
        System.out.print("Enter width: ");
        width = scanner.nextDouble();

        double area = length * width;
        System.out.println("Area of the rectangle: " + area);
    }
}

```

``````

``````     {tab-item} Rust

<iframe src="https://www.youtube.com/embed/t047Hseyj_k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} rust
:lineno-start: 1
:emphasize-lines: 1-3,8

use std::io;

fn main() {
    let mut input = String::new();
    println!("Enter length: ");
    io::stdin().read_line(&mut input).expect("Failed to read line");
    let length: f64 = input.trim().parse().expect("Please enter a valid number");

    input.clear();
    println!("Enter width: ");
    io::stdin().read_line(&mut input).expect("Failed to read line");
    let width: f64 = input.trim().parse().expect("Please enter a valid number");

    let area = length * width;
    println!("Area of the rectangle: {}", area);
}

```

``````

``````     {tab-item} Golang

<iframe src="https://www.youtube.com/embed/pM0-CMysa_M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} golang
:lineno-start: 1
:emphasize-lines: 5-7,12

package main

import (
    "fmt"
)

func main() {
    var length, width float64

    fmt.Print("Enter length: ")
    fmt.Scan(&length)

    fmt.Print("Enter width: ")
    fmt.Scan(&width)

    area := length * width
    fmt.Println("Area of the rectangle:", area)
}

```

``````
```````

```` {admonition} Output
:class: important, dropdown

> The code samples above calculate the `area` of a rectangle given its length and width. The user enters the `length` and `width`, and the program performs the necessary calculations.
>
> Assume the user enters `length = 5` and `width = 7` for all the examples.


**C++ / Rust / Golang**
``` {code-block} bash
Area of the rectangle: 35
```

**Python / Java**
``` {code-block} bash
Area of the rectangle: 35.0
```

*Note: the difference in each output is due directly to the nature of integer division within each given language.*

````
`````````
``````````

### Data Types of Various Languages

````````` {div} full-width
````````  {card}

Many of the following overlap between languages while others, are unique to a given language. Implementations are in C++.


````` {admonition} Integer Types

`int`  
: Used to represent integers. 
  : `int age = 25;`  

`short`  
: Used to represent short integers. 
  : `short quantity = 10;`

`long`
: Used to represent long integers. 
  : `long population = 1000000;`

`long long`
: Used to represent very long integers.
  : `long long distance = 10000000000LL;`

`unsigned int`
: Used to represent positive integers.
  : `unsigned int count = 100;`

`````

````` {admonition} Floating-Point Types

`float`
: Used to represent floating-point numbers with single precision.
  : `float weight = 65.5f;`

`double`
: Used to represent floating-point numbers with double precision.
  : `double pi = 3.14159;`

`long double`
: Used to represent floating-point numbers with extended precision.
  : `long double value = 1234.56789L;`

`````
````` {admonition} Character Types

`char`
: Used to represent single characters.
  : `char grade = 'A';`

`wchar_t`
: Used to represent wide characters.
  : `wchar_t symbol = L'€';`

`````
````` {admonition} Boolean Type

`bool`
: Used to represent boolean values (true or false).
  : `bool isValid = true;`

`````

```````` 
`````````