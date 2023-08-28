# Iteration Statements

```` {div} full-width
``` {figure} https://usemynotes.com/wp-content/uploads/2021/01/what-is-loop-statement-in-c-1024x515.jpg
```
````

## [Loops]()

### Entry Controlled

#### `for` loop

````````` {div} full-width

> The for loop is used when the number of iterations is known in advance. It consists of three parts: initialization, condition, and iteration.

````````  {grid}
```````   {grid-item-card}
:columns: 12
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20230329132110/Java-For-loop-with-Examples-1.png

`for` loop
```
```````
```````   {grid-item-card}
:columns: 6
``` {card}
:text-align: center

<iframe width="100%" height="315" src="https://www.youtube.com/embed/yS8DUrQy_ow" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
``` {code-block} bash
// Syntax

for (initialization; condition; iteration) {
    // Code block to be executed repeatedly
}

```
```````
```````   {grid-item-card}
:columns: 6
``` {code-block} cpp
// Example

// C++ program to illustrate If statement
#include <iostream>
using namespace std;

int main()
{

  for (int i = 0; i < 5; i++) {
      cout << i << endl;
  }

}

```
``` {code-block} bash
// Output

0
1
2
3
4
```
``` {card}
The loop initializes the variable `i` to `0`, checks the condition `i < 5`, executes the code block, increments `i` by `1`, and repeats the process until the condition is no longer `true`.
```
```````
````````
`````````
#### `while` loop

````````` {div} full-width

> The while loop is used when the number of iterations is not known in advance. It repeats a block of code as long as a specified condition is true.

````````  {grid}
```````   {grid-item-card}
:columns: 12
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20191118164726/While-Loop-GeeksforGeeks.jpg

`while` loop
```
```````
```````   {grid-item-card}
:columns: 6
``` {card}
:text-align: center

<iframe width="100%" height="315" src="https://www.youtube.com/embed/iF4i423144E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
``` {code-block} bash
// Syntax

while (condition) {
    // Code block to be executed repeatedly
    // Condition should eventually become false to exit the loop
}

```
```````
```````   {grid-item-card}
:columns: 6
``` {code-block} cpp
// Example

// C++ program to illustrate If statement
#include <iostream>
using namespace std;

int main()
{

  int i = 0;
  while (i < 5) {
      cout << i << endl;
      i++;
  }

}

```
``` {code-block} bash
// Output

0
1
2
3
4
```
``` {card}
The loop checks the condition i < 5 before each iteration. If the condition is true, it executes the code block, increments i by 1, and repeats the process until the condition becomes false.
```
```````
````````
`````````
### Exit Controlled

### `do while`

````````` {div} full-width

> The do-while loop is similar to the while loop, but it guarantees that the code block is executed at least once before checking the condition.

````````  {grid}
```````   {grid-item-card}
:columns: 12
``` {figure} https://media.geeksforgeeks.org/wp-content/uploads/20191118154342/do-while-Loop-GeeksforGeeks2.jpg

`do-while` loop
```
```````
```````   {grid-item-card}
:columns: 6
``` {card}
:text-align: center

<iframe width="100%" height="315" src="https://www.youtube.com/embed/TjkJQly2YCw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```
``` {code-block} bash
// Syntax

do {
    // Code block to be executed repeatedly
    // Condition should eventually become false to exit the loop
} while (condition);

```
```````
```````   {grid-item-card}
:columns: 6
``` {code-block} cpp
// Example

// C++ program to illustrate If statement
#include <iostream>
using namespace std;

int main()
{

  int i = 0;
  do {
      cout << i << endl;
      i++;
  } while (i < 5);

}

```
``` {code-block} bash
// Output

0
1
2
3
4
```
The loop executes the code block at least once because the condition i < 5 is checked after the first iteration. If the condition is true, it repeats the process until the condition becomes false.
```
```````
````````
`````````
