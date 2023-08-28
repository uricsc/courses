# [Expressions](https://en.cppreference.com/w/cpp/container/array)

<style>
    iframe {width:100%;height:600px;}
</style>

```` {div} full-width
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20190801163131/What-is-an-Expression_-3.jpg
:width: 450
```
````

## [Overview]()

`````````` {div} full-width

``` {admonition} Definition
:class: seealso

> An expression is a combination of variables, constants, operators, and function calls that can be evaluated to produce a value. It can be as simple as a single variable or as complex as a series of nested function calls and operators. Expressions are commonly used in C++ to perform calculations, assign values to variables, and make decisions.

```

````` {admonition} Characteristics
:class: tip

```` {dropdown} Operators
Expressions involve operators, which are symbols that represent specific operations. Examples of operators include addition (+), subtraction (-), multiplication (*), division (/), and comparison operators (==, !=, <, >, etc.).
````
```` {dropdown} Operands
These are the values or variables that the operators act upon. For instance, in the expression 5 + x, the values 5 and x are operands.
````
```` {dropdown} Values
These are constants, literals, or numeric representations that can be used in expressions. In the expression 2 * 3, the values 2 and 3 are used to calculate the product.
````
```` {dropdown} Variables
Variables are placeholders for values that can change during the program's execution. Expressions often involve using variables to create dynamic calculations.
````
```` {dropdown} Function Calls
Functions can also be part of expressions. A function call evaluates to its return value. For example, in the expression sqrt(25), the function sqrt calculates the square root of 25.
````
```` {dropdown} Precedence
Expressions follow operator precedence rules, which determine the order in which operators are evaluated. Parentheses can be used to override the default precedence.
````
```` {dropdown} Evaluation
The process of evaluating an expression involves substituting values for variables, applying operators, and calculating the final result. The result of evaluating an expression is a single value.
````
`````

```` {admonition} Examples of expressions
:class: tip

Arithmetic Expression: 
```
3 * (x + 5) - y
```  
Logical Expression: 
```
age >= 18 && hasID
```  
String Concatenation: 
```
"Hello, " + name
```  
Function Call: 
```
sqrt(x * x + y * y)
```  
```````
``````````


### Expression Syntax

`````````` {div} full-width
`````````  {card}

```````    {tab-set}
``````     {tab-item} Pseudocode

<iframe src="https://www.youtube.com/embed/LV8tCxAxm7E?si=1VNjVwjhMQEz7u_6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
BEGIN
    TRY
        Read userInput
        Convert userInput to integer
        PRINT "You entered:", userInput
    CATCH InvalidInputException
        PRINT "Invalid input! Please enter a valid integer."
    CATCH Exception
        PRINT "An unexpected error occurred."
    END TRY
END

```

``````
``````     {tab-item} C++

<iframe src="https://www.youtube.com/embed/cqi060vJuoI?si=3arMfZBg53XC39_i" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 9,11,13

#include <iostream>
using namespace std;

int main() {
    try {
        int userInput;
        cin >> userInput;
        if (cin.fail()) {
            throw runtime_error("Invalid input! Please enter a valid integer.");
        }
        cout << "You entered: " << userInput << endl;
    }
    catch (const exception &e) {
        cerr << e.what() << endl;
    }
    return 0;
}


```

``````
``````     {tab-item} Python

<iframe src="https://www.youtube.com/embed/LZFpLUKpo1I?si=PKqdIITkrwLN9NWj" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} python
:lineno-start: 1
:emphasize-lines: 1-2,6

def main():
    try:
        user_input = int(input("Enter an integer: "))
        print("You entered:", user_input)
    except ValueError:
        print("Invalid input! Please enter a valid integer.")
    except Exception as e:
        print("An unexpected error occurred.")


if __name__ == "__main__":
    main()

```

``````
``````     {tab-item} Java

<iframe src="https://www.youtube.com/embed/RA7wkTV6z4k?si=RJxuhbqBgLm3R3cC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} java
:lineno-start: 1
:emphasize-lines: 3-5,9

import java.util.Scanner;

public class ErrorHandlingDemo {
    public static void main(String[] args) {
        try {
            Scanner scanner = new Scanner(System.in);
            int userInput = scanner.nextInt();
            System.out.println("You entered: " + userInput);
        } catch (java.util.InputMismatchException e) {
            System.err.println("Invalid input! Please enter a valid integer.");
        } catch (Exception e) {
            System.err.println("An unexpected error occurred.");
        }
    }
}

```

``````
``````     {tab-item} Rust

<iframe src="https://www.youtube.com/embed/LxBgtAIOf4M?si=xNqBapeMW8aea1-Z" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} rust
:lineno-start: 1
:emphasize-lines: 1-3,8

use std::io;

fn main() {
    let mut user_input = String::new();
    io::stdin().read_line(&mut user_input).expect("Failed to read input");
    match user_input.trim().parse::<i32>() {
        Ok(num) => println!("You entered: {}", num),
        Err(_) => println!("Invalid input! Please enter a valid integer."),
    }
}

```

``````
``````     {tab-item} Golang

<!-- TODO : UPDATE IFRAME & CODE -->

<iframe src="https://www.youtube.com/embed/VMveb4GqRck?si=Wvjrn0neNmlX4n3u" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} golang
:lineno-start: 1
:emphasize-lines: 5-7,12

package main

import (
	"fmt"
	"strconv"
)

func main() {
	var userInput string
	fmt.Print("Enter an integer: ")
	fmt.Scan(&userInput)
	num, err := strconv.Atoi(userInput)
	if err == nil {
		fmt.Println("You entered:", num)
	} else {
		fmt.Println("Invalid input! Please enter a valid integer.")
	}
}

```

``````
```````

```` {admonition} Output
:class: important, dropdown

> In each, a user-entered value is validated through error / exception handling. The exception [error] is thrown when the validation fails.
>
> _Note: Various means of evaluation are available per language with a range of validation abilities_

``` {code-block} bash
Outcomes will vary based on the exception throw and or error caught...
```

````

`````````
``````````

### Compare & Contrast

```````` {div} full-width
```````  {card}
``````   {list-table}
:header-rows: 1

* - Language
  - Methodology
  - Comments/Notes
* - C++
  - Exception-based with `try` and `catch` blocks
  - Utilizes standard exceptions for error handling.
* - Python
  - Exception-based using `try` and `except` clauses
  - Python's concise syntax simplifies error handling.
* - Java
  - Exception-based with `try`, `catch`, and `throw`
  - Strongly typed exceptions offer clear error identification.
* - Rust
  - Result-based approach with `Result` and `match`
  - Forces explicit handling of success or error cases.
* - Go
  - Return value-based with error returns and `if` checks
  - Simplicity in error handling with multiple return values.


``````
```````
````````

		
		
		
		
		
		












`````````` {div} full-width

> An expression is a combination of variables, constants, operators, and function calls that can be evaluated to produce a value. It can be as simple as a single variable or as complex as a series of nested function calls and operators. Expressions are commonly used in C++ to perform calculations, assign values to variables, and make decisions.

Now, let's provide an example of a simple C++ expression using pseudocode and C++ code, along with the output and an explanation.


````````  {grid}
<!-- ```````   {grid-item-card}
:columns: 12
``` {figure} https://www.simplilearn.com/ice9/free_resources_article_thumb/Vaibhav-Arrays%20Article/Arrays_in_ds-what-is-array-img1.PNG

expression structure
```
``````` -->
```````   {grid-item-card}
:columns: 6

``` {code-block} cpp
// Pseudocode
// Calculate the sum of two numbers 
//    and store the result in a variable.

1. Declare two variables, 
  num1 and num2, and assign them values.  
2. Calculate the sum of num1 and num2 
  and store it in a variable called sum.

```
``` {code-block} cpp
// Example

#include <iostream>

int main() {
    // Step 1: Declare and assign values to
    //   num1 and num2
    int num1 = 5;
    int num2 = 3;

    // Step 2: Calculate the sum and store it in the 
    //   sum variable
    int sum = num1 + num2;

    // Output the result
    std::cout << "The sum of " << num1 << " and " 
              << num2 << " is: " << sum << std::endl;

    return 0;
}

```
```````
```````   {grid-item-card}
:columns: 6

<!-- TODO: UPDATE EXAMPLE OUTPUT -->
``` {code-block} bash
// Output

The sum of 5 and 3 is: 8
```

``` {card} Explanation

1. We declare two integer variables, `num1` and `num2`, and assign them the values `5` and `3`, respectively. 

2. We calculate the sum of `num1` and `num2` using the addition operator (`+`) and store the result in the `sum` variable. 

3. Finally, we output the result using `std::cout`. The values of `num1` and `num2` are displayed alongside the calculated `sum`, which is `8`.
```

```````
````````


``````````