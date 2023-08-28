# Main


`````````` {div} full-width

```` {dropdown} <iframe width="1000" height="600" src="https://www.youtube.com/embed/imNlJohlLPk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```{contents}
:local:
```
````

``````````

## [main](https://en.cppreference.com/w/cpp/language/main_function)

`````````` {div} full-width

> The main function is crucial because it is the starting point of a C++ program. It allows you to define the program's logic and perform various operations based on your requirements. It also provides an entry point for the program to interact with the operating system and handle command-line arguments, if necessary. Without a main function, the program cannot be executed as a standalone program.


````````  {grid}
<!-- ```````   {grid-item-card}
:columns: 12
``` {figure} https://www.simplilearn.com/ice9/free_resources_article_thumb/Vaibhav-Arrays%20Article/Arrays_in_ds-what-is-array-img1.PNG

expression structure
```
``````` -->

```````   {grid-item-card}
:columns: 6

``` {card} 
`argc` (argument count) 
: is an integer that represents the number of command-line arguments passed to the program. It includes the name of the program itself as the first argument.

`argv` (argument vector) 
: is an array of character pointers (char*) that holds the command-line arguments passed to the program. Each element of the array points to a null-terminated C-style string representing an argument.
```

``` {code-block} cpp
// Example

#include <iostream>

int main(int argc, char* argv[]) {
    std::cout << "Number of arguments: " 
              << argc << std::endl;

    for (int i = 0; i < argc; i++) {
        std::cout << "Argument " << i 
                  << ": " << argv[i] << std::endl;
    }

    return 0;
}

```

``` bash
// Compile, Run, and Output

$ g++ main.cpp -o program
$ ./program 10 20 30
$ Argument 1 : 10
$ Argument 2 : 20
$ Argument 3 : 30
```
```````
```````   {grid-item-card}
:columns: 6

``` {card} Explanation

- The `main` function is declared with the return type `int`, which indicates that it should return an integer value to the operating system upon completion. The value `0` is typically used to indicate successful program execution.

- The `main` function can have two commonly used parameters: `int argc` and `char* argv[]`. These parameters are used to handle command-line arguments passed to the program, but they are not necessary for a basic `main` function.

- The program statements, or the actual code that performs the desired functionality, are written within the curly braces `{}` following the `main` function declaration. These statements can include variable declarations, function calls, control flow structures (e.g., if statements, loops), and any other valid C++ code.

- The `return 0`; statement indicates the end of the `main` function. By convention, a `return 0`; statement is used to indicate successful program execution. Other non-zero values can be returned to indicate different types of errors or abnormal program termination.

```

```````
````````


``````````