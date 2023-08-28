# [Exceptions & Errors]()

<style>
    iframe {width:100%;height:600px;}
</style>

```` {div} full-width
``` {figure} https://static.javatpoint.com/core/images/types-of-exception-handling.png
:width: 450
```
````

## [Overview]()

`````````` {div} full-width

``` {admonition} Definition
:class: seealso

> Exception handling is a mechanism in programming languages that deals with runtime errors and exceptional situations. It allows you to gracefully handle errors and continue execution rather than crashing the program.

```

````` {admonition} Use Cases
:class: tip

```` {card}
Exception handling is used in scenarios where unexpected situations can arise, such as file I/O errors, network communication issues, or arithmetic errors.

````
`````

````````` {admonition} Pros & Cons
:class: warning

```````` {grid}
```````  {grid-item}
```` {card} 👍
``` {dropdown} Readability
Improves code readability by separating error-handling logic from main program flow.
```
``` {dropdown} Structured
Provides a structured way to handle errors and recover gracefully.
```
``` {dropdown} Robust & Reliability
Enhances program robustness and reliability by preventing crashes due to unexpected errors.
```
````
```````
```````  {grid-item}
```` {card} 👎
``` {dropdown} Overhead
Can introduce performance overhead when exceptions are thrown frequently.
```
``` {dropdown} Convoluted Code 
Overuse of exceptions can lead to convoluted code and reduced maintainability.
```
````
```````
````````
`````````
``````````


### Exception & Error Handling Syntax

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

<iframe src="https://www.youtube.com/embed/5MI2N8yLdMI?si=7ykm3jXJojb4kQoy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

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

<iframe src="https://www.youtube.com/embed/6SPDvPK38tw?si=d7HHq3mvOJPGoBXf" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

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

<iframe src="https://www.youtube.com/embed/1XAfapkBQjk?si=VTI1r6yQoGfFDK6h" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

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

<iframe src="https://www.youtube.com/embed/wM6o70NAWUI?si=F2tCfrqQc_Wyqtog" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

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

		
		
		
		
		
		