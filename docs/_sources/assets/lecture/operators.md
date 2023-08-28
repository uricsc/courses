# Operators

```` {div} full-width
``` {figure} https://i.ytimg.com/vi/1mbgeb4w3wc/maxresdefault.jpg
```
````

``````` {div} full-width

``` {dropdown} <iframe width="1000" height="600" src="https://www.youtube.com/embed/RP3BWoep69U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
```

``````  {card}
`````  {tab-set}
````   {tab-item} Arithmetic

> Arithmetic operators are used to perform mathematical calculations.

``` cpp
int a = 10;
int b = 5;

int addition = a + b;   // Addition operator
int subtraction = a - b;   // Subtraction operator
int multiplication = a * b;   // Multiplication operator
int division = a / b;   // Division operator
int modulus = a % b;   // Modulus (remainder) operator

```

````
````   {tab-item} Logical

> Logical operators are used to perform logical operations on boolean values.

``` cpp
bool a = true;
bool b = false;

bool logicalAnd = (a && b);   // Logical AND operator
bool logicalOr = (a || b);   // Logical OR operator
bool logicalNotA = !a;   // Logical NOT operator for a
bool logicalNotB = !b;   // Logical NOT operator for b

```

````
````   {tab-item} Bitwise

> Bitwise operators are used to perform operations on individual bits of integer values.

``` cpp
int a = 10;
int b = 5;

int bitwiseAnd = a & b;   // Bitwise AND operator
int bitwiseOr = a | b;   // Bitwise OR operator
int bitwiseXor = a ^ b;   // Bitwise XOR (exclusive OR) operator
int bitwiseNotA = ~a;   // Bitwise NOT operator for a
int leftShift = a << 1;   // Left shift operator
int rightShift = a >> 1;   // Right shift operator

```

These are just a few examples of the types of operators in C++. It's important to note that the usage and behavior of operators can vary depending on the data types they are used with.

````
````   {tab-item} Relational

> Relational operators are used to compare values and return a boolean result (true or false).

``` cpp
int a = 10;
int b = 5;

bool equal = (a == b);   // Equal to operator
bool notEqual = (a != b);   // Not equal to operator
bool greaterThan = (a > b);   // Greater than operator
bool lessThan = (a < b);   // Less than operator
bool greaterThanOrEqual = (a >= b);   // Greater than or equal to operator
bool lessThanOrEqual = (a <= b);   // Less than or equal to operator

```

````
````   {tab-item} Assignment

> Assignment operators are used to assign values to variables.

``` cpp
int a = 10;
int b = 5;

a += b;   // Equivalent to: a = a + b
a -= b;   // Equivalent to: a = a - b
a *= b;   // Equivalent to: a = a * b
a /= b;   // Equivalent to: a = a / b
a %= b;   // Equivalent to: a = a % b

```

````
`````
``````
```````
