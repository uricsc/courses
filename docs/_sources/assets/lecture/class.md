# [Object-Oriented Programming]()

<style>
    iframe {width:100%;height:600px;}
</style>

```` {div} full-width
``` {figure} https://www.unionsquaredesign.com/wp-content/uploads/2016/10/CPT-OOP-objects_and_classes_-_attmeth.svg.png
:width: 450
```
````

## [Overview]()

`````````` {div} full-width
```` {admonition} Definition
:class: seealso

<iframe src="https://www.youtube.com/embed/SiBw7os-_zI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

> [Object-Oriented Programming (OOP)](https://youtu.be/m_MQYyJpIjg) is a programming paradigm that revolves around the concept of objects, which are instances of classes. Classes are user-defined data types that encapsulate data and behavior. They allow us to model real-world entities and their interactions through the use of attributes (data) and methods (functions).
>
> *Note: not all languages are built for OOP. But OOP can be injected into your code through a little creative programming*

````

````` {admonition} Use Cases
:class: tip

OOP is widely used in various domains, such as software development, game development, simulation, and more. It helps in creating modular, maintainable, and extensible code.

`````

````````` {admonition} Pros & Cons
:class: warning

```````` {grid}
```````  {grid-item}
```` {card} 👍
``` {dropdown} Modularity
Code can be organized into self-contained objects, making it easier to understand and maintain.
```
``` {dropdown} Reusability
Classes and objects promote code reuse, reducing redundant implementations.
```
``` {dropdown} Encapsulation
Data hiding ensures that the internal representation of an object is hidden, and access to it is restricted to methods, promoting security and data integrity.
```
``` {dropdown} Inheritance
Inheritance enables the creation of hierarchies and facilitates code sharing and extension.
```
``` {dropdown} Polymorphism
Polymorphism allows objects of different classes to be treated as objects of a common superclass, promoting flexibility and generality.
```
````
```````
```````  {grid-item}
```` {card} 👎
``` {dropdown} Complexity
OOP can introduce additional complexity, especially for smaller projects where simpler paradigms might suffice.
```
``` {dropdown} Overhead
It can lead to performance overhead due to dynamic dispatch and object creation.
```
``` {dropdown} Learning Curve
Understanding and mastering OOP concepts can be challenging for beginners.
```
````
```````
````````
`````````
``````````

### `class` / `struct` Syntax

`````````` {div} full-width
`````````  {card}

```````    {tab-set}
``````     {tab-item} Pseudocode
<iframe src="https://www.youtube.com/embed/XHjuHPn8QKY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
CLASS Animal:
    ATTRIBUTES:
        name
        age
    METHODS:
        constructor(name, age)
        make_sound()
    END CLASS

FUNCTION main():
    animal1 = Animal("Buddy", 3)
    animal1.make_sound()
    animal2 = Animal("Charlie", 5)
    animal2.make_sound()
END FUNCTION

```
``````

``````     {tab-item} C++
<iframe src="https://www.youtube.com/embed/2BP8NhxjrO0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 4-6,10

#include <iostream>
using namespace std;

class Animal {
public:
    string name;
    int age;

    Animal(string name, int age) {
        this->name = name;
        this->age = age;
    }

    void make_sound() {
        cout << "Animal sound!" << endl;
    }
};

int main() {
    Animal animal1("Buddy", 3);
    animal1.make_sound();
    Animal animal2("Charlie", 5);
    animal2.make_sound();
    return 0;
}

```
``````

``````     {tab-item} Python
<iframe src="https://www.youtube.com/embed/f0TrMH9s-VE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} python
:lineno-start: 1
:emphasize-lines: 1-2,6

class Animal:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def make_sound(self):
        print("Animal sound!")

def main():
    animal1 = Animal("Buddy", 3)
    animal1.make_sound()
    animal2 = Animal("Charlie", 5)
    animal2.make_sound()

if __name__ == "__main__":
    main()

```
``````

``````     {tab-item} Java
<iframe src="https://www.youtube.com/embed/IUqKuGNasdM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} java
:lineno-start: 1
:emphasize-lines: 3-5,9

class Animal {
    String name;
    int age;

    Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }

    void makeSound() {
        System.out.println("Animal sound!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal1 = new Animal("Buddy", 3);
        animal1.makeSound();
        Animal animal2 = new Animal("Charlie", 5);
        animal2.makeSound();
    }
}

```
``````

``````     {tab-item} Rust
<iframe src="https://www.youtube.com/embed/n3bPhdiJm9I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} rust
:lineno-start: 1
:emphasize-lines: 1-3,8

struct Animal {
    name: String,
    age: i32,
}

impl Animal {
    fn new(name: &str, age: i32) -> Animal {
        Animal {
            name: name.to_string(),
            age,
        }
    }

    fn make_sound(&self) {
        println!("Animal sound!");
    }
}

fn main() {
    let animal1 = Animal::new("Buddy", 3);
    animal1.make_sound();
    let animal2 = Animal::new("Charlie", 5);
    animal2.make_sound();
}

```
``````

``````     {tab-item} Golang
<iframe src="https://www.youtube.com/embed/sPX6ORiyd0o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} golang
:lineno-start: 1
:emphasize-lines: 5-7,12

package main

import "fmt"

type Animal struct {
    name string
    age  int
}

func NewAnimal(name string, age int) *Animal {
    return &Animal{name: name, age: age}
}

func (a *Animal) makeSound() {
    fmt.Println("Animal sound!")
}

func main() {
    animal1 := NewAnimal("Buddy", 3)
    animal1.makeSound()
    animal2 := NewAnimal("Charlie", 5)
    animal2.makeSound()
}

```
``````
```````

```` {admonition} Output
:class: important, dropdown

<!-- TODO : OUTPUT DESCRIPTION -->
> 

``` {code-block} bash
Animal sound!
Animal sound!
```
````
`````````
``````````