# Inheritance

<style>
    iframe {width:100%;height:600px;}
</style>

## [Overview]()

`````````` {div} full-width
```` {admonition} Definition
:class: seealso

<iframe width="100%" height="600" src="https://www.youtube.com/embed/_b_QiItg-9s?si=CUccstdtnUgep7Iy" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

> Inheritance is a mechanism by which a new class (subclass or derived class) inherits properties (fields and methods) and behaviors from an existing class (superclass or base class). The subclass can extend or modify the behavior of the superclass.

````

````` {admonition} Use Cases
:class: tip

```` {grid}
```  {grid-item-card}
Creating specialized classes that share common attributes and behaviors.
```
```  {grid-item-card}
Extending the functionality of existing classes without modifying their code.
```
```  {grid-item-card}
Implementing polymorphism, allowing objects of different classes to be treated as objects of a common superclass.
```
````

`````

````````` {admonition} Pros & Cons
:class: warning

```````` {grid}
```````  {grid-item}
```` {card} 👍
``` {dropdown} Modularity
Classes can be organized hierarchically, aiding in code management.
```
``` {dropdown} Reusability
Reusing existing code reduces redundancy and development time.
```
``` {dropdown} Efficiency
By inheriting methods and fields, new classes can leverage existing functionality.
```
``` {dropdown} Polymorphism
Subclasses can be treated as instances of their superclass, allowing dynamic method invocation.
```
````
```````
```````  {grid-item}
```` {card} 👎
``` {dropdown} Tight Coupling
Changes to the superclass can affect its subclasses, leading to unintended consequences.
```
``` {dropdown} Inheritance Hierarchy Complexity
Deep hierarchies can be intricate and challenging to manage.
```
``` {dropdown} Fragile Base Class Problem
Modifications to the base class can inadvertently break subclasses.
```
````
```````
````````
`````````
``````````

### `class inheritance` Syntax

`````````` {div} full-width
`````````  {card}

```````    {tab-set}
``````     {tab-item} Pseudocode
<iframe src="https://www.youtube.com/embed/XHjuHPn8QKY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` plaintext
class Animal:
    method speak()  // Common method, to be overridden

class Dog extends Animal:
    method speak()
        output "Woof!"

class Cat extends Animal:
    method speak()
        output "Meow!"


```
``````

``````     {tab-item} C++
<iframe src="https://www.youtube.com/embed/X8nYM8wdNRE?si=c14qkCqIhzO7uyAV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 4-6,10

#include <iostream>

class Animal {
public:
    virtual void speak() {
        std::cout << "Some sound..." << std::endl;
    }
};

class Dog : public Animal {
public:
    void speak() override {
        std::cout << "Woof!" << std::endl;
    }
};

class Cat : public Animal {
public:
    void speak() override {
        std::cout << "Meow!" << std::endl;
    }
};

int main() {
    Animal *a;
    Dog d;
    Cat c;

    a = &d;
    a->speak(); // Output: Woof!

    a = &c;
    a->speak(); // Output: Meow!

    return 0;
}


```
``````

``````     {tab-item} Python
<iframe src="https://www.youtube.com/embed/6c6NYPjO_rI?si=ToU063_8pQcvUNED" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} python
:lineno-start: 1
:emphasize-lines: 1-2,6

class Animal:
    def speak(self):
        print("Some sound...")

class Dog(Animal):
    def speak(self):
        print("Woof!")

class Cat(Animal):
    def speak(self):
        print("Meow!")

a = Animal()
d = Dog()
c = Cat()

a.speak()  # Output: Some sound...
d.speak()  # Output: Woof!
c.speak()  # Output: Meow!


```
``````

``````     {tab-item} Java
<iframe src="https://www.youtube.com/embed/Zs342ePFvRI?si=DEXHT00J4iR5CxdZ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} java
:lineno-start: 1
:emphasize-lines: 3-5,9

class Animal {
    void speak() {
        System.out.println("Some sound...");
    }
}

class Dog extends Animal {
    void speak() {
        System.out.println("Woof!");
    }
}

class Cat extends Animal {
    void speak() {
        System.out.println("Meow!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Animal();
        Dog d = new Dog();
        Cat c = new Cat();

        a.speak(); // Output: Some sound...
        d.speak(); // Output: Woof!
        c.speak(); // Output: Meow!
    }
}


```
``````

``````     {tab-item} Rust
<iframe src="https://www.youtube.com/embed/UGDa0P2PXrY?si=T0rZ2DH7q2xgDeQw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} rust
:lineno-start: 1
:emphasize-lines: 1-3,8

trait Animal {
    fn speak(&self);
}

struct Dog;

impl Animal for Dog {
    fn speak(&self) {
        println!("Woof!");
    }
}

struct Cat;

impl Animal for Cat {
    fn speak(&self) {
        println!("Meow!");
    }
}

fn main() {
    let d = Dog;
    let c = Cat;

    d.speak(); // Output: Woof!
    c.speak(); // Output: Meow!
}


```
``````

``````     {tab-item} Golang
<iframe src="https://www.youtube.com/embed/I0Ei70cZtf8?si=81DcyWUzBbYrvfP_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {code-block} golang
:lineno-start: 1
:emphasize-lines: 5-7,12

package main

import "fmt"

type Animal interface {
    Speak()
}

type Dog struct{}

func (d Dog) Speak() {
    fmt.Println("Woof!")
}

type Cat struct{}

func (c Cat) Speak() {
    fmt.Println("Meow!")
}

func main() {
    var a Animal

    d := Dog{}
    c := Cat{}

    a = d
    a.Speak() // Output: Woof!

    a = c
    a.Speak() // Output: Meow!
}


```
``````
```````

```` {admonition} Output
:class: important, dropdown

<!-- TODO : OUTPUT DESCRIPTION -->
> Python & Java
``` {code-block} bash
Some sound...
Woof!
Meow!
```

> C++, Rust, and Golang
``` {code-block} bash
Some sound...
Woof!
Meow!
```
````
`````````
``````````

### Comparing & Contrast

`````````` {div} full-width
```````    {card}
`````` {list-table}
:header-rows: 1

* - Language
  - Inheritance Syntax
  - Overriding Method
  - Polymorphism
* - C++	
  - `class Derived : public Base`
  - `virtual` method, `override` keyword
  - Yes
* - Python
  - `class Derived(Base):`
  - `def` method, method overriding
  - Yes
* - Java
  - `class Derived extends Base`
  - `void` method, `@Override` annotation
  - Yes
* - Rust
  - `impl Trait for Struct`
  - Trait implementation
  - Yes
* - Go
  - `type Struct struct { }`
  - Method implementation
  - Yes

``````
``````` 

``````````

