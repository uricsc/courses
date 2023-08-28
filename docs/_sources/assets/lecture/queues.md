## Queues

````````` {div} full-width
```````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/D6gu-_tmEpQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
``` {card} TL;DR
A queue is another linear data structure in computer science that follows the First-In-First-Out (FIFO) principle. This means that the element that is added first to the queue is the first element to be removed from it.

A queue is similar to a queue of people waiting in line, where the person who enters the queue first is the first person to leave. The queue data structure has two primary operations: enqueue and dequeue. The enqueue operation adds an element to the end of the queue, while the dequeue operation removes the front-most element from the queue.

Queues are commonly used in programming for various purposes, such as job scheduling, breadth-first search, and buffer management. In job scheduling, a queue is used to schedule tasks or processes for execution based on their priority or arrival time. In breadth-first search, a queue is used to traverse a graph or tree in a level-by-level manner. In buffer management, a queue is used to manage the flow of data between two processes or devices.
```

``` {card} Additional Resources
- [Data Structures: Stacks and Queues | HackerRank](https://youtu.be/wjI1WNcIntg)
```

````````
`````````


<!-- 
````````` {div} full-width
``````` {grid}
``````  {grid-item}
:columns: 6

``` {figure} https://media-exp1.licdn.com/dms/image/C4D12AQGxoj-X5uaibQ/article-cover_image-shrink_720_1280/0/1526784056697?e=2147483647&v=beta&t=6Z11_PpUPowdeHcUHERvFunxIZUqA7mUWfV4SPALQnI
:align: center
```

``````
``````  {grid-item}
:columns: 6

``` {figure} https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/images/Queue.PNG
:align: center
```
``````
```````
````````` -->
<!-- 
`````````` {div} full-width
````` {card}
```` {admonition} FIFO: First In First Out
``` {figure} https://airpix.io/assets/images/queue-management/airport-queue.png
```
``` {figure} https://assets.interviewbit.com/assets/skill_interview_questions/data-structure/queue-2c61774234ac435fa7c5edb2867d269f7b22159a72c5e871a2d7c94b5f945831.png.gz
```
````
`````
`````````` -->

### Basic Operations

`````````` {div} full-width
`````` {card}

``` {figure} https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fprepinsta.com%2Fwp-content%2Fuploads%2F2020%2F06%2FHow-Queue-in-C-Programming-works-1024x646.png&f=1&nofb=1&ipt=8cf09d53e7476f452a2830dd8ffa4b288d2acf75bda0780f1c01bfa005e1d4f1&ipo=images
```

``` {figure} https://algorithmtutor.com/images/queue_operations.png
```

````` {card}

```` {dropdown} enqueue
- inserts one element onto the queue

``` {image} https://algorithmtutor.com/images/enqueue.png
:align: center
```

> The `enqueue` operation inserts a new item at the rear end of the `queue`. After the `enqueue` operation, the value of rear is increased by 1.
> 
> -- https://algorithmtutor.com/Data-Structures/Basic/Queues/
````


```` {dropdown} dequeue
- returns the element at the top of the queue (and removes it)

``` {image} https://algorithmtutor.com/images/dequeue.png
:align: center
```

> The dequeue operation removes the item at the front of the queue. When we remove the item at the front, we increase the value of front.
>
> -- https://algorithmtutor.com/Data-Structures/Basic/Queues/

````

``` {dropdown} isEmpty
not necessary, but sometimes useful
```

``````
``````````

### Documentation

`````````` {div} full-width

``` {card}
:text-align: center
<iframe src="https://en.cppreference.com/w/cpp/container/queue" frameborder="0"></iframe>
```

```` {card}

%``` {figure} imgs/08_s12_01.png
%```

```cpp
#include <stack>
#include <iostream>

int main() {
    std::queue<int> q1;
    q1.push(5);
    std::cout << q1.size() << "\n";
    
    std::queue<int> q2(q1);
    std::cout << s.size() << "\n";
    
    std::deque<int> deq { 3, 1, 4, 1, 5 };
    std::queue<int> q3(deq);
    std::cout << q3.size() << "\n";
    return 0;
}
```

[https://en.cppreference.com/w/cpp/container/queue](https://en.cppreference.com/w/cpp/container/queue)

%``` {figure} imgs/08_s12_02.png
%```

````
``````````

### Implementation

`````````` {div} full-width
``````` {card}

```` {admonition} Arrays

- **enqueue** and **dequeue** at <u>different</u> ends of the array (easier and efficient)
- can be <span class="blue">fixed-length</span>
- can also use a <span class="blue">dynamic array</span> (grows over time)   
  - additional cost for dynamic arrays

``` {figure} imgs/08_s05.png
:width: 92%
```

````

```` {admonition} Visualize: Queue Array (general premise)
:class: tip

[https://www.cs.usfca.edu/~galles/visualization/QueueArray.html](https://www.cs.usfca.edu/~galles/visualization/QueueArray.html)
````

```` {admonition} Queue: Array Sample

```cpp
void enqueue(Queue* queue, int item)
{
  if (isFull(queue))
    return;
  queue->rear = (queue->rear + 1)
                % queue->capacity;
  queue->array[queue->rear] = item;
  queue->size = queue->size + 1;
  cout << item << " enqueued to queue\n"; 
}
```

```cpp
int dequeue(Queue* queue)
{
  if (isEmpty(queue))
    return INT_MIN;
  int item = queue->array[queue->front];  
  queue->front = (queue->front + 1)
                  % queue->capacity;
  queue->size = queue->size - 1;
  return item;
}
```

``` {figure} https://examradar.com/wp-content/uploads/2016/10/Figure-4.6.-Basic-operations-on-deque.png
```

[https://www.geeksforgeeks.org/queue-set-1introduction-and-array-implementation/](https://www.geeksforgeeks.org/queue-set-1introduction-and-array-implementation/)

````

````` {admonition} Visualize: Queue Array (in Memory)
:class: tip

```` {card} 
:link: https://pythontutor.com/iframe-embed.html#code=//%20CPP%20program%20for%20array%0A//%20implementation%20of%20queue%0A%23include%20%3Cbits/stdc%2B%2B.h%3E%0Ausing%20namespace%20std%3B%0A%0A//%20A%20structure%20to%20represent%20a%20queue%0Aclass%20Queue%20%7B%0Apublic%3A%0A%20%20%20%20int%20front,%20rear,%20size%3B%0A%20%20%20%20unsigned%20capacity%3B%0A%20%20%20%20int*%20array%3B%0A%7D%3B%0A%0A//%20function%20to%20create%20a%20queue%0A//%20of%20given%20capacity.%0A//%20It%20initializes%20size%20of%20queue%20as%200%0AQueue*%20createQueue%28unsigned%20capacity%29%0A%7B%0A%20%20%20%20Queue*%20queue%20%3D%20new%20Queue%28%29%3B%0A%20%20%20%20queue-%3Ecapacity%20%3D%20capacity%3B%0A%20%20%20%20queue-%3Efront%20%3D%20queue-%3Esize%20%3D%200%3B%0A%0A%20%20%20%20//%20This%20is%20important,%20see%20the%20enqueue%0A%20%20%20%20queue-%3Erear%20%3D%20capacity%20-%201%3B%0A%20%20%20%20queue-%3Earray%20%3D%20new%20int%5Bqueue-%3Ecapacity%5D%3B%0A%20%20%20%20return%20queue%3B%0A%7D%0A%0A//%20Queue%20is%20full%20when%20size%0A//%20becomes%20equal%20to%20the%20capacity%0Aint%20isFull%28Queue*%20queue%29%0A%7B%0A%20%20%20%20return%20%28queue-%3Esize%20%3D%3D%20queue-%3Ecapacity%29%3B%0A%7D%0A%0A//%20Queue%20is%20empty%20when%20size%20is%200%0Aint%20isEmpty%28Queue*%20queue%29%0A%7B%0A%20%20%20%20return%20%28queue-%3Esize%20%3D%3D%200%29%3B%0A%7D%0A%0A//%20Function%20to%20add%20an%20item%20to%20the%20queue.%0A//%20It%20changes%20rear%20and%20size%0Avoid%20enqueue%28Queue*%20queue,%20int%20item%29%0A%7B%0A%20%20%20%20if%20%28isFull%28queue%29%29%0A%20%20%20%20%20%20%20%20return%3B%0A%20%20%20%20queue-%3Erear%20%3D%20%28queue-%3Erear%20%2B%201%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%25%20queue-%3Ecapacity%3B%0A%20%20%20%20queue-%3Earray%5Bqueue-%3Erear%5D%20%3D%20item%3B%0A%20%20%20%20queue-%3Esize%20%3D%20queue-%3Esize%20%2B%201%3B%0A%20%20%20%20cout%20%3C%3C%20item%20%3C%3C%20%22%20enqueued%20to%20queue%5Cn%22%3B%0A%7D%0A%0A//%20Function%20to%20remove%20an%20item%20from%20queue.%0A//%20It%20changes%20front%20and%20size%0Aint%20dequeue%28Queue*%20queue%29%0A%7B%0A%20%20%20%20if%20%28isEmpty%28queue%29%29%0A%20%20%20%20%20%20%20%20return%20INT_MIN%3B%0A%20%20%20%20int%20item%20%3D%20queue-%3Earray%5Bqueue-%3Efront%5D%3B%0A%20%20%20%20queue-%3Efront%20%3D%20%28queue-%3Efront%20%2B%201%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%25%20queue-%3Ecapacity%3B%0A%20%20%20%20queue-%3Esize%20%3D%20queue-%3Esize%20-%201%3B%0A%20%20%20%20return%20item%3B%0A%7D%0A%0A//%20Function%20to%20get%20front%20of%20queue%0Aint%20front%28Queue*%20queue%29%0A%7B%0A%20%20%20%20if%20%28isEmpty%28queue%29%29%0A%20%20%20%20%20%20%20%20return%20INT_MIN%3B%0A%20%20%20%20return%20queue-%3Earray%5Bqueue-%3Efront%5D%3B%0A%7D%0A%0A//%20Function%20to%20get%20rear%20of%20queue%0Aint%20rear%28Queue*%20queue%29%0A%7B%0A%20%20%20%20if%20%28isEmpty%28queue%29%29%0A%20%20%20%20%20%20%20%20return%20INT_MIN%3B%0A%20%20%20%20return%20queue-%3Earray%5Bqueue-%3Erear%5D%3B%0A%7D%0A%0A//%20Driver%20code%0Aint%20main%28%29%0A%7B%0A%20%20%20%20Queue*%20queue%20%3D%20createQueue%285%29%3B%0A%0A%20%20%20%20enqueue%28queue,%2010%29%3B%0A%20%20%20%20enqueue%28queue,%2020%29%3B%0A%20%20%20%20enqueue%28queue,%2030%29%3B%0A%20%20%20%20enqueue%28queue,%2040%29%3B%0A%0A%20%20%20%20cout%20%3C%3C%20dequeue%28queue%29%0A%20%20%20%20%20%20%20%20%3C%3C%20%22%20dequeued%20from%20queue%5Cn%22%3B%0A%0A%20%20%20%20cout%20%3C%3C%20%22Front%20item%20is%20%22%0A%20%20%20%20%20%20%20%20%3C%3C%20front%28queue%29%20%3C%3C%20endl%3B%0A%20%20%20%20cout%20%3C%3C%20%22Rear%20item%20is%20%22%0A%20%20%20%20%20%20%20%20%3C%3C%20rear%28queue%29%20%3C%3C%20endl%3B%0A%0A%20%20%20%20return%200%3B%0A%7D%0A%0A//%20This%20code%20is%20contributed%20by%20rathbhupendra&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false

Click to interact...

``` {figure} img/w5_queue_array.png
:align: center
```

_Note: may need a few seconds to execute code..._

````
`````

```` {admonition} Queues : Linked Lists

- **enqueue** and **dequeue** at <u>different</u> ends

``` {figure} imgs/08_s15.png
```

[https://www.cs.usfca.edu/~galles/visualization/QueueArray.html](https://www.cs.usfca.edu/~galles/visualization/QueueLL.html)

````

```` {admonition} Queue: LL Sample

```cpp
void enQueue(int x)
{
  QNode* temp = new QNode(x);     

  if (rear == NULL) {
    front = rear = temp;
    return;
  }

  rear->next = temp;
  rear = temp;
}
```

```cpp
void deQueue()
{
  if (front == NULL)
    return;

  QNode* temp = front;  
  front = front->next;

  if (front == NULL)
    rear = NULL;

  delete (temp);
}
```

[https://www.geeksforgeeks.org/queue-linked-list-implementation/](https://www.geeksforgeeks.org/queue-linked-list-implementation/)

````


````` {admonition} Visualize: Queue LL (in Memory)
:class: tip

```` {card} 
:link: https://pythontutor.com/visualize.html#code=//%20C%2B%2B%20program%20for%20the%20above%20approach%0A%0A%23include%20%3Cbits/stdc%2B%2B.h%3E%0Ausing%20namespace%20std%3B%0A%0Astruct%20QNode%20%7B%0A%20%20%20%20int%20data%3B%0A%20%20%20%20QNode*%20next%3B%0A%20%20%20%20QNode%28int%20d%29%0A%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20data%20%3D%20d%3B%0A%20%20%20%20%20%20%20%20next%20%3D%20NULL%3B%0A%20%20%20%20%7D%0A%7D%3B%0A%0Astruct%20Queue%20%7B%0A%20%20%20%20QNode%20*front,%20*rear%3B%0A%20%20%20%20Queue%28%29%20%7B%20front%20%3D%20rear%20%3D%20NULL%3B%20%7D%0A%0A%20%20%20%20void%20enQueue%28int%20x%29%0A%20%20%20%20%7B%0A%0A%20%20%20%20%20%20%20%20//%20Create%20a%20new%20LL%20node%0A%20%20%20%20%20%20%20%20QNode*%20temp%20%3D%20new%20QNode%28x%29%3B%0A%0A%20%20%20%20%20%20%20%20//%20If%20queue%20is%20empty,%20then%0A%20%20%20%20%20%20%20%20//%20new%20node%20is%20front%20and%20rear%20both%0A%20%20%20%20%20%20%20%20if%20%28rear%20%3D%3D%20NULL%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20front%20%3D%20rear%20%3D%20temp%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20return%3B%0A%20%20%20%20%20%20%20%20%7D%0A%0A%20%20%20%20%20%20%20%20//%20Add%20the%20new%20node%20at%0A%20%20%20%20%20%20%20%20//%20the%20end%20of%20queue%20and%20change%20rear%0A%20%20%20%20%20%20%20%20rear-%3Enext%20%3D%20temp%3B%0A%20%20%20%20%20%20%20%20rear%20%3D%20temp%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20//%20Function%20to%20remove%0A%20%20%20%20//%20a%20key%20from%20given%20queue%20q%0A%20%20%20%20void%20deQueue%28%29%0A%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20//%20If%20queue%20is%20empty,%20return%20NULL.%0A%20%20%20%20%20%20%20%20if%20%28front%20%3D%3D%20NULL%29%0A%20%20%20%20%20%20%20%20%20%20%20%20return%3B%0A%0A%20%20%20%20%20%20%20%20//%20Store%20previous%20front%20and%0A%20%20%20%20%20%20%20%20//%20move%20front%20one%20node%20ahead%0A%20%20%20%20%20%20%20%20QNode*%20temp%20%3D%20front%3B%0A%20%20%20%20%20%20%20%20front%20%3D%20front-%3Enext%3B%0A%0A%20%20%20%20%20%20%20%20//%20If%20front%20becomes%20NULL,%20then%0A%20%20%20%20%20%20%20%20//%20change%20rear%20also%20as%20NULL%0A%20%20%20%20%20%20%20%20if%20%28front%20%3D%3D%20NULL%29%0A%20%20%20%20%20%20%20%20%20%20%20%20rear%20%3D%20NULL%3B%0A%0A%20%20%20%20%20%20%20%20delete%20%28temp%29%3B%0A%20%20%20%20%7D%0A%7D%3B%0A%0A//%20Driver%20code%0Aint%20main%28%29%0A%7B%0A%0A%20%20%20%20Queue%20q%3B%0A%20%20%20%20q.enQueue%2810%29%3B%0A%20%20%20%20q.enQueue%2820%29%3B%0A%20%20%20%20q.deQueue%28%29%3B%0A%20%20%20%20q.deQueue%28%29%3B%0A%20%20%20%20q.enQueue%2830%29%3B%0A%20%20%20%20q.enQueue%2840%29%3B%0A%20%20%20%20q.enQueue%2850%29%3B%0A%20%20%20%20q.deQueue%28%29%3B%0A%20%20%20%20cout%20%3C%3C%20%22Queue%20Front%20%3A%20%22%20%3C%3C%20%28q.front%29-%3Edata%20%3C%3C%20endl%3B%0A%20%20%20%20cout%20%3C%3C%20%22Queue%20Rear%20%3A%20%22%20%3C%3C%20%28q.rear%29-%3Edata%3B%0A%7D%0A//%20This%20code%20is%20contributed%20by%20rathbhupendra&cumulative=false&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=cpp_g%2B%2B9.3.0&rawInputLstJSON=%5B%5D&textReferences=false

Click to interact...

``` {figure} img/w5_queue_ll.png
```

_Note: may need a few seconds to execute code..._

````
`````

%<iframe width="800" height="500" frameborder="0" src=""> </iframe>


```````
``````````

### Considerations

`````````` {div} full-width
````` {card}

``` {figure} https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fprepinsta.com%2Fwp-content%2Fuploads%2F2020%2F06%2FCircular-Queues-in-DSA-Limitations-with-Linear-Queues.png&f=1&nofb=1&ipt=cc9c379ca83596886121fd079623ed7fd0afb84c302ce5dabac536a1d1401366&ipo=images
```

``` {dropdown} Underflow
error can be thrown when calling **dequeue** on an empty queue
```

```` {dropdown} Overflow
error can be thrown when calling **enqueue** on a full queue (especially in fixed-length implementations)

``` {image} https://user-images.githubusercontent.com/5148166/27678605-b48b3f24-5cad-11e7-9417-ab05449fecb9.PNG
:align: center

````

`````
``````````

### Applications

`````````` {div} full-width
``` {card}

**Media Playlists (Youtube, Spotify, Music,etc.)**

**Process management in Operating Systems**

**Simulations**

**Used in other algorithms**

**etc...**

```
``````````



