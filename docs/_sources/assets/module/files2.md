# [File Handling]()

<style>
    iframe {width:100%;height:600px;}
</style>

```` {div} full-width
``` {figure} https://intellipaat.com/mediaFiles/2015/11/mj1.png
:width: 600
```
````

## [Overview]()

`````````` {div} full-width

``` {admonition} Definition
:class: seealso

> File Input/Output (I/O) refers to the process of reading data from files or writing data to files in a computer program. This functionality allows programs to store and retrieve information persistently, making it useful for various tasks like saving configurations, storing user data, or processing large datasets.

```

````` {admonition} Use Cases
:class: tip

```` {grid}
```  {grid-item-card} 
:columns: 4
Reading configuration files to set program parameters.
```
```  {grid-item-card} 
:columns: 4
Saving and loading game progress or user data in games or applications.
```
```  {grid-item-card} 
:columns: 4
Processing large datasets, such as reading from CSV files.
```
```  {grid-item-card} 
:columns: 4
Logging information, debugging, and error handling.
```
```  {grid-item-card} 
:columns: 4
Creating and managing databases.
```

````
`````

````````` {admonition} Pros & Cons
:class: warning

```````` {grid}
```````  {grid-item}
```` {card} 👍
``` {dropdown} Data Persistence
Files allow data to be stored beyond the program's runtime, making it available for future use.

```
``` {dropdown} Data Sharing
Files enable data exchange between different programs and systems.

```
``` {dropdown} Scalability
FIle I/O can handle large volumes of data efficiently.
```
``` {dropdown} Portability
Files can be easily transformed between different platforms
```
````
```````
```````  {grid-item}
```` {card} 👎
``` {dropdown} Slower Access
Reading from and writing to files is generally slower compared to in-memory operations.
```
``` {dropdown} Error Handling
File operations can lead to potential errors, such as file not found or permissions issues.
```
``` {dropdown} Security Risks
Improper handling of files can lead to security vulnerabilities.
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

<iframe src="https://www.youtube.com/embed/snFPNd13XyA?si=jWw74mgvW1JW4gjO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
Open "data.txt" for reading
if the file is opened successfully:
    Read data from the file
    Close the file
else:
    Display an error message
```
``````

``````     {tab-item} C++
<iframe src="https://www.youtube.com/embed/EaHFhms_Shw?si=rjnFg7pZvpTkKGRd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 4-6,10

// In this C++ code, we use the ifstream class to open the file in input mode. 
// We then use a while loop to read the integers one by one until the end of the file.

#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ifstream inputFile("data.txt");
    if (inputFile.is_open()) {
        int num;
        while (inputFile >> num) {
            cout << num << " ";
        }
        inputFile.close();
    } else {
        cout << "Error opening file.";
    }
    return 0;
}

```

``````

``````     {tab-item} Python
<iframe src="https://www.youtube.com/embed/DmHSwTiD5Tk?si=qVaNfEXuigP8ekmQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} python
:lineno-start: 1
:emphasize-lines: 1-2,6

# In Python, we use a with statement to open the file, which automatically closes
# the file after reading. We read the file contents, split the data into numbers, 
# and then print each number.

try:
  with open("data.txt", "r") as inputFile:
    numbers = inputFile.read().split()       
    for num in numbers:  
      print(num, end=" ") 
except FileNotFoundError:
  print("Error opening file.")
```
``````

``````     {tab-item} Java
<iframe src="https://www.youtube.com/embed/hgF21imQ_Is?si=6ftxkapbUo3hJFiP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} java
:lineno-start: 1
:emphasize-lines: 3-5,9

// Java uses Scanner to read data from the file. The hasNextInt() method checks 
// if the file has more integers, and nextInt() reads the next integer.

import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class FileIOJava {
    public static void main(String[] args) {
        try {
            File file = new File("data.txt");
            Scanner inputFile = new Scanner(file);
            while (inputFile.hasNextInt()) {
                int num = inputFile.nextInt();
                System.out.print(num + " ");
            }
            inputFile.close();
        } catch (FileNotFoundException e) {
            System.out.println("Error opening file.");
        }
    }
}

```
``````

``````     {tab-item} Rust
<iframe src="https://www.youtube.com/embed/mkFFtO6WA8I?si=eeYQxWNiaiWCvDDH" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} rust
:lineno-start: 1
:emphasize-lines: 1-3,8

// Rust provides File and BufReader for file handling. We read the file's contents
// into a string and then split it by whitespace to extract the numbers.

use std::fs::File;
use std::io::{BufReader, Read};

fn main() {
    match File::open("data.txt") {
        Ok(file) => {
            let mut buf_reader = BufReader::new(file);
            let mut contents = String::new();
            buf_reader.read_to_string(&mut contents).unwrap();
            for num in contents.trim().split_whitespace() {
                print!("{} ", num);
            }
        }
        Err(_) => println!("Error opening file."),
    }
}

```

``````

``````     {tab-item} Golang
<iframe src="https://www.youtube.com/embed/N1wSFA6VNuM?si=MbYJri9gIAVammLc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} golang
:lineno-start: 1
:emphasize-lines: 5-7,12

// In Go, we open the file using os.Open and handle the error. Then, we use a 
// Scanner to read the file line by line and print each line.

package main

import (
    "fmt"
    "os"
    "bufio"
)

func main() {
    file, err := os.Open("data.txt")
    if err != nil {
        fmt.Println("Error opening file.")
        return
    }
    scanner := bufio.NewScanner(file)
    for scanner.Scan() {
        fmt.Print(scanner.Text(), " ")
    }
    file.Close()
}

```

``````
```````

```` {admonition} Output
:class: important, dropdown

> *Descriptions included in the comments for each sample code*
>
> If "data.txt" contains the numbers "1 2 3 4 5", the output will be:

``` {code-block} bash
1 2 3 4 5
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
  - File I/O Implementation
  - Exception Handling
  - Ease of Use
  - Performance
* - C++
  - `<fstream>` library
  - Manual
  - Moderate
  - Efficient
* - Python
  - `open()` built-in function with `with`
  - Automatic
  - Easy
  - Moderate
* - Java
  - `Scanner` class
  - Try-Catch
  - Easy
  - Moderate
* - Rust
  - `std::fs::File` and `BufReader`
  - Result
  - Moderate
  - Efficient
* - Golang
  - `os.Open` and `bufio.Scanner`
  - Error Handling
  - Easy
  - Efficient

``````     

```````` 
`````````

				
				
				