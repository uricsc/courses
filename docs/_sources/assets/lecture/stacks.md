## Stacks

````````` {div} full-width
```````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/KcT3aVgrrpU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
A stack is a linear data structure in computer science that follows the Last-In-First-Out (LIFO) principle. In simpler terms, the element that is added last to the stack is the first element to be removed from it.

A stack is similar to a stack of books, where the book that is placed on top is the first book to be removed. The stack data structure has two primary operations: push and pop. The push operation adds an element to the top of the stack, while the pop operation removes the topmost element from the stack.

Stacks are commonly used in programming for various purposes, such as function calls, expression evaluation, and memory allocation. In function calls, a stack is used to keep track of the sequence of function calls that are made during the execution of a program. In expression evaluation, a stack is used to evaluate arithmetic expressions, such as infix, postfix, and prefix expressions. In memory allocation, a stack is used to allocate and deallocate memory for variables and data structures.
```

``` {card} Additional Resources
- [Data Structures: Stacks and Queues | HackerRank](https://youtu.be/wjI1WNcIntg)
```

````````


`````````

`````````` {div} full-width
``````` {card} LIFO: Last In, First Out


<iframe src="https://joaogabrielferr.github.io/data-structures-visualizer"></iframe>

```````
``````````

### Documentation

`````````` {div} full-width
```` {card}
<iframe src="https://en.cppreference.com/w/cpp/container/stack" frameborder="0"></iframe>
````
```` {card} Example

%``` {figure} imgs/08_s04_01.png
%```

```cpp
#include <stack>
#include <iostream>

int main() {
  std::stack<int> s;
  s.push(1);
  s.push(2);
  s.push(3);
  std::cout << s.size() << " elements on stack\n";  
  std::cout << "Top element: " << s.top() << "\n";
  std::cout << s.size() << " elements on stack\n";
  s.pop();
  std::cout << s.size() << " elements on stack\n";
  std::cout << "Top element: " << s.top() << "\n";
  return 0;
}
```

%[https://en.cppreference.com/w/cpp/container/stack](https://en.cppreference.com/w/cpp/container/stack)

%``` {figure} imgs/08_s04_02.png
%```

````
``````````

### Basic Operations

`````````` {div} full-width
`````` {card}

````` {grid}
````  {grid-item}
:columns: 6

``` {figure} https://storage.googleapis.com/course-panel-site-media/images/stacks.width-1500.jpg
:align: center
```

````
````  {grid-item}
:columns: 6

``` {figure} https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/stack1.PNG
:align: center
```
````
`````

<!-- ```` {figure} https://miro.medium.com/max/814/0*pdhOeAK6wSh8ipTW.png
```` -->

````` {dropdown} push
```` {admonition} Built-in Function
- inserts one element onto the stack

``` {figure} https://algorithmtutor.com/images/stack_push.png
```

> A new item can be pushed into a stack using the following steps  
> - Check if the stack is full. If it is, then you can not insert the item. Raise “Stack Overflow” error.  
> - If the stack is not full, insert the item at the top of the stack.  
> - Make this item a new top of the stack.  
> 
> -- https://algorithmtutor.com/Data-Structures/Basic/Stacks/
````
`````

````` {dropdown} pop
```` {admonition} Built-in Function
- returns the element at the top of the stack (and removes it)

``` {figure} https://algorithmtutor.com/images/stack_pop.png
```

> An item on the top of the stack can be removed (popped) using following steps.
> : Check if the stack is empty. If it is, then you can not remove the item. Raise “Stack Underflow” error.
> : If the stack is not empty, remove the item at the top of the stack.
> : Update the top of the stack.
>
> -- https://algorithmtutor.com/Data-Structures/Basic/Stacks/
````
`````

```` {dropdown} push-pop
``` {figure} https://i5.walmartimages.com/asr/086c29e7-6a57-4e3b-866e-5acb0a55a20f.ce63df4e7d8951e80eef82640705f104.jpeg?odnWidth=400&odnHeight=400&odnBg=ffffff
:width: 400

For levity...
```
````

```` {dropdown} isEmpty
``` {admonition} Built-in Function
- not necessary, but sometimes useful

> The `top` operation returns the item at the top of the stack. Don’t be confused this operation with the `pop` operation. The `pop` operation removes the top item whereas the `top` operation only reads the value of the top item. As in the `pop` operation, we need to check if the stack is empty before reading the value.
```
````

``````
``````````

### Implementation

`````````` {div} full-width
``````` {card}

```` {admonition} Arrays

- **push** and **pop** at the end of the array (easier and efficient)
- can be <span class="blue">fixed-length</span>
- can also use a <span class="blue">dynamic array</span> (grows overtime)   
  - additional cost for dynamic arrays

``` {figure} imgs/08_s05.png
:width: 92%
```

````

```` {admonition} Stack
```cpp
class Stack {
    private:
        int *array;
        int length;
        int top_idx;

    public:
        Stack();
        ~Stack();
          
        void push(int);
        int peek();        // returns top
        void pop();        // removes top
}
```
````

```` {admonition} Stack: Array Sample

```cpp
// CPP program to illustrate
// Implementation of push() function      

#include <iostream>
#include <stack>
using namespace std;

int main()
{
    // Empty stack
    stack<int> mystack;
    mystack.push(0);
    mystack.push(1);
    mystack.push(2);
    // Printing content of stack
    while (!mystack.empty()) {
        cout << ' ' << mystack.top(); 
        mystack.pop();
    }
}
```

[https://www.geeksforgeeks.org/stack-push-and-pop-in-c-stl/?ref=rp](https://www.geeksforgeeks.org/stack-push-and-pop-in-c-stl/?ref=rp)

````

```` {admonition} Visualize: Stack Array (general premise)
:class: tip

[https://www.cs.usfca.edu/~galles/visualization/StackArray.html](https://www.cs.usfca.edu/~galles/visualization/StackArray.html)
````

````` {admonition} Visualize: Stack Array (in Memory)
:class: tip

```` {card}
:link: https://pythontutor.com/visualize.html#code=/*%20C%2B%2B%20program%20to%20implement%20basic%20stack%0Aoperations%20*/%0A%23include%20%3Cbits/stdc%2B%2B.h%3E%0A%0Ausing%20namespace%20std%3B%0A%0A%23define%20MAX%203%0A%0Aclass%20Stack%20%7B%0A%20%20%20%20int%20top%3B%0A%0Apublic%3A%0A%20%20%20%20int%20a%5BMAX%5D%3B%20//%20Maximum%20size%20of%20Stack%0A%0A%20%20%20%20Stack%28%29%20%7B%20top%20%3D%20-1%3B%20%7D%0A%20%20%20%20bool%20push%28int%20x%29%3B%0A%20%20%20%20int%20pop%28%29%3B%0A%20%20%20%20int%20peek%28%29%3B%0A%20%20%20%20bool%20isEmpty%28%29%3B%0A%7D%3B%0A%0Abool%20Stack%3A%3Apush%28int%20x%29%0A%7B%0A%20%20%20%20if%20%28top%20%3E%3D%20%28MAX%20-%201%29%29%20%7B%0A%20%20%20%20%20%20%20%20cout%20%3C%3C%20%22Stack%20Overflow%22%3B%0A%20%20%20%20%20%20%20%20return%20false%3B%0A%20%20%20%20%7D%0A%20%20%20%20else%20%7B%0A%20%20%20%20%20%20%20%20a%5B%2B%2Btop%5D%20%3D%20x%3B%0A%20%20%20%20%20%20%20%20cout%20%3C%3C%20x%20%3C%3C%20%22%20pushed%20into%20stack%5Cn%22%3B%0A%20%20%20%20%20%20%20%20return%20true%3B%0A%20%20%20%20%7D%0A%7D%0A%0Aint%20Stack%3A%3Apop%28%29%0A%7B%0A%20%20%20%20if%20%28top%20%3C%200%29%20%7B%0A%20%20%20%20%20%20%20%20cout%20%3C%3C%20%22Stack%20Underflow%22%3B%0A%20%20%20%20%20%20%20%20return%200%3B%0A%20%20%20%20%7D%0A%20%20%20%20else%20%7B%0A%20%20%20%20%20%20%20%20int%20x%20%3D%20a%5Btop--%5D%3B%0A%20%20%20%20%20%20%20%20return%20x%3B%0A%20%20%20%20%7D%0A%7D%0Aint%20Stack%3A%3Apeek%28%29%0A%7B%0A%20%20%20%20if%20%28top%20%3C%200%29%20%7B%0A%20%20%20%20%20%20%20%20cout%20%3C%3C%20%22Stack%20is%20Empty%22%3B%0A%20%20%20%20%20%20%20%20return%200%3B%0A%20%20%20%20%7D%0A%20%20%20%20else%20%7B%0A%20%20%20%20%20%20%20%20int%20x%20%3D%20a%5Btop%5D%3B%0A%20%20%20%20%20%20%20%20return%20x%3B%0A%20%20%20%20%7D%0A%7D%0A%0Abool%20Stack%3A%3AisEmpty%28%29%0A%7B%0A%20%20%20%20return%20%28top%20%3C%200%29%3B%0A%7D%0A%0A//%20Driver%20program%20to%20test%20above%20functions%0Aint%20main%28%29%0A%7B%0A%20%20%20%20class%20Stack%20s%3B%0A%20%20%20%20s.push%2810%29%3B%0A%20%20%20%20s.push%2820%29%3B%0A%20%20%20%20s.push%2830%29%3B%0A%20%20%20%20cout%20%3C%3C%20s.pop%28%29%20%3C%3C%20%22%20Popped%20from%20stack%5Cn%22%3B%0A%0A%20%20%20%20//%20//print%20top%20element%20of%20stack%20after%20popping%0A%20%20%20%20//%20cout%20%3C%3C%20%22Top%20element%20is%20%3A%20%22%20%3C%3C%20s.peek%28%29%20%3C%3C%20endl%3B%0A%0A%20%20%20%20//%20//print%20all%20elements%20in%20stack%20%3A%0A%20%20%20%20//%20cout%20%3C%3C%22Elements%20present%20in%20stack%20%3A%20%22%3B%0A%20%20%20%20//%20while%28!s.isEmpty%28%29%29%0A%20%20%20%20//%20%7B%0A%20%20%20%20//%20%20%20%20%20//%20print%20top%20element%20in%20stack%0A%20%20%20%20//%20%20%20%20%20cout%20%3C%3C%20s.peek%28%29%20%3C%3C%22%20%22%3B%0A%20%20%20%20//%20%20%20%20%20//%20remove%20top%20element%20in%20stack%0A%20%20%20%20//%20%20%20%20%20s.pop%28%29%3B%0A%20%20%20%20//%20%7D%0A%0A%20%20%20%20return%200%3B%0A%7D&cumulative=false&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false

Click to interact...

``` {figure} img/w5_stack_array.png
:align: center
```

_Note: may need a few seconds to execute code..._

````
`````

```` {admonition} Linked Lists

- **push** and **pop** at front (could use the other end as well)

``` {figure} https://i1.faceprep.in/Companies-1/stack%20linked%20list.png
```

````

`````` {admonition} Stack: LL Sample

````` {tab-set}
```` {tab-item} Altogether
``` {code-block} cpp
class Node {
public:
    int data;
    Node* next;
    Node(int data) {
        this->data = data;
        next = NULL;
    }
};

class Stack {
private:
    Node* top;

public:
    Stack() {
        top = NULL;
    }

    void push(int data) {
        Node* newNode = new Node(data);
        newNode->next = top;
        top = newNode;
    }

    int pop() {
        if (top == NULL) {
            return -1; // stack is empty
        }
        int popped = top->data;
        Node* temp = top;
        top = top->next;
        delete temp;
        return popped;
    }

    int peek() {
        if (top == NULL) {
            return -1; // stack is empty
        }
        return top->data;
    }

    bool isEmpty() {
        return top == NULL;
    }
};
```
````
```` {tab-item} Node
``` {code-block} cpp
class Node {
public:
    int data;
    Node* next;
    Node(int data) {
        this->data = data;
        next = NULL;
    }
};
```

````
```` {tab-item} Stack
``` {code-block} cpp
class Stack {
private:
    Node* top;

public:
    Stack() {
        top = NULL;
    }
};
```
````
```` {tab-item} push()
``` {code-block} cpp
void push(int data) {
    Node* newNode = new Node(data);
    newNode->next = top;
    top = newNode;
}
```

````
```` {tab-item} pop()
``` {code-block} cpp
int pop() {
    if (top == NULL) {
        return -1; // stack is empty
    }
    int popped = top->data;
    Node* temp = top;
    top = top->next;
    delete temp;
    return popped;
}
```
````
```` {tab-item} peek()
``` {code-block} cpp
int peek() {
    if (top == NULL) {
        return -1; // stack is empty
    }
    return top->data;
}
```
````
```` {tab-item} isEmpty()
``` {code-block} cpp 
bool isEmpty() {
    return top == NULL;
}
```
````
`````

[https://www.geeksforgeeks.org/implement-a-stack-using-singly-linked-list/](https://www.geeksforgeeks.org/implement-a-stack-using-singly-linked-list/)

``````

```` {admonition} Visualize: Stack Array (general premise)
:class: tip

<!-- <iframe src="https://www.cs.usfca.edu/~galles/visualization/StackLL.html" width="1000" height="600" frameborder="0"> -->

[https://www.cs.usfca.edu/~galles/visualization/StackLL.html](https://www.cs.usfca.edu/~galles/visualization/StackLL.html)
````

````` {admonition} Visualize: Stack LL (in Memory)
:class: tip

```` {card}
:link: https://pythontutor.com/iframe-embed.html#code=//%20C%2B%2B%20program%20for%20linked%20list%20implementation%20of%20stack%0A%23include%20%3Cbits/stdc%2B%2B.h%3E%0Ausing%20namespace%20std%3B%0A%0A//%20A%20structure%20to%20represent%20a%20stack%0Aclass%20StackNode%20%7B%0Apublic%3A%0A%20%20%20%20int%20data%3B%0A%20%20%20%20StackNode*%20next%3B%0A%7D%3B%0A%0AStackNode*%20newNode%28int%20data%29%0A%7B%0A%20%20%20%20StackNode*%20stackNode%20%3D%20new%20StackNode%28%29%3B%0A%20%20%20%20stackNode-%3Edata%20%3D%20data%3B%0A%20%20%20%20stackNode-%3Enext%20%3D%20NULL%3B%0A%20%20%20%20return%20stackNode%3B%0A%7D%0A%0Aint%20isEmpty%28StackNode*%20root%29%0A%7B%0A%20%20%20%20return%20!root%3B%0A%7D%0A%0Avoid%20push%28StackNode**%20root,%20int%20data%29%0A%7B%0A%20%20%20%20StackNode*%20stackNode%20%3D%20newNode%28data%29%3B%0A%20%20%20%20stackNode-%3Enext%20%3D%20*root%3B%0A%20%20%20%20*root%20%3D%20stackNode%3B%0A%20%20%20%20cout%20%3C%3C%20data%20%3C%3C%20%22%20pushed%20to%20stack%5Cn%22%3B%0A%7D%0A%0Aint%20pop%28StackNode**%20root%29%0A%7B%0A%20%20%20%20if%20%28isEmpty%28*root%29%29%0A%20%20%20%20%20%20%20%20return%20INT_MIN%3B%0A%20%20%20%20StackNode*%20temp%20%3D%20*root%3B%0A%20%20%20%20*root%20%3D%20%28*root%29-%3Enext%3B%0A%20%20%20%20int%20popped%20%3D%20temp-%3Edata%3B%0A%20%20%20%20delete%20temp%3B%0A%0A%20%20%20%20return%20popped%3B%0A%7D%0A%0A//%20Driver%20code%0Aint%20main%28%29%0A%7B%0A%20%20%20%20StackNode*%20root%20%3D%20NULL%3B%0A%0A%20%20%20%20push%28%26root,%2010%29%3B%0A%20%20%20%20push%28%26root,%2020%29%3B%0A%20%20%20%20push%28%26root,%2030%29%3B%0A%0A%20%20%20%20cout%20%3C%3C%20pop%28%26root%29%20%3C%3C%20%22%20popped%20from%20stack%5Cn%22%3B%0A%0A%20%20%20%20return%200%3B%0A%7D&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false

Click to interact...

``` {figure} img/w5_stack_ll.png
:align: center
```

_Note: may need a few seconds to execute code..._

````
`````

```````
``````````

### Considerations

`````````` {div} full-width
````` {card}

``` {figure} https://static.platzi.com/media/user_upload/Captura%20de%20pantalla%20(55)-27856afe-5df2-45ee-afdb-59af2e1629c1.jpg
```

``` {dropdown} Underflow
error can be thrown when calling `pop` on an empty stack
```

```` {dropdown} Overflow
error can be thrown when calling `push` on a full stack  (especially in fixed-length implementations)

``` {image} https://thecodinglove.com/content/036/glass_stackoverflow_tw.png
:align: center
```

````

`````
``````````

### Applications

`````````` {div} full-width
```` {card}
``` {card}

**Undo in software applications...**

**Stack in compilers/programming languages...**

**Parsing expressions...**

**etc...**

```
````
``````````
