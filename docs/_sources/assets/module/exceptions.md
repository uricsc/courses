# Exception Handling

`````````` {div} full-width

``` {dropdown} <iframe width="1000" height="600" src="https://www.youtube.com/embed/kjEhqgmEiWY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```


``````````

## Defined

`````````` {div} full-width
```` {card}
Exception handling is a mechanism in C++ that allows you to handle runtime errors or exceptional conditions in a structured and controlled manner. It enables you to catch and recover from errors that may occur during program execution, preventing the program from terminating abruptly.

``` {figure} https://static.javatpoint.com/core/images/types-of-exception-handling.png
```

Try
: The code that might throw an exception is enclosed within a try block. If an exception occurs within the try block, it is thrown and passed to the corresponding catch block for handling.

Catch
: A catch block follows the try block and specifies the type of exception it can handle. If an exception of the specified type is thrown, the catch block is executed to handle the exception.

Throw
: An exception can be explicitly thrown using the throw statement. It is typically used when an error condition is detected, and you want to transfer control to the nearest catch block.


``` cpp
#include <iostream>

int divide(int a, int b) {
    if (b == 0) {
        throw "Divide by zero error"; // throw an exception
    }
    return a / b;
}

int main() {
    int x = 10, y = 0;
    
    try {
        int result = divide(x, y);
        std::cout << "Result: " << result << std::endl;
    }
    catch (const char* exception) {
        std::cout << "Exception caught: " << exception << std::endl;
    }
    
    return 0;
}

```

``` bash
// Output
Exception caught: Divide by zero error
```

``` {card}
In the above code, the `divide` function attempts to divide `a` by `b`. If `b` is zero, an exception of type `const char*` with the message "Divide by zero error" is thrown.

In the `main` function, the division operation is enclosed within a try block. If an exception is thrown, it is caught by the catch block, which takes a parameter of type `const char*`. In this case, the catch block prints the exception message.

As shown in the output, the catch block is executed because the exception was thrown in the divide function due to dividing by zero. The program doesn't terminate abruptly but gracefully handles the exception.

You can also catch exceptions by their types instead of using `const char*`. C++ allows you to define custom exception classes derived from the standard `std::exception` class to represent specific error conditions. By catching these custom exception types, you can handle different types of exceptions separately.

Exception handling provides a structured approach to deal with exceptional situations and gives you the flexibility to handle errors gracefully without interrupting the normal flow of the program.
```

``````````