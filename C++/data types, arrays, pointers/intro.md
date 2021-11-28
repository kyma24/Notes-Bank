the operating system allocates memory and selects what will be stored in the reserved memory based on the variable's **data type**.
the data type defines the proper use of an identifier, what kind of data can be stored, and which types of operations can be performed.

```cpp
//i.e. legal vs illegal
55 + 15 // legal C++ expression
//Both operands of the + operator are integers

55 + "John" // illegal
//The + operator is not defined for integer and string
```

numeric data types include:
**Integers** i.e. -7, 42.
**Floating point** i.e. 3.14, -42.67.

a **string** is composed of numbers, characters, or symbols. String literals are placed in **double quotation** marks; some examples are "Hello", "My name is David", and similar.
**characters** are single letters or symbols, and must be enclosed between **single quotes**, like 'a', 'b', etc.
note that in C++, single quotation marks indicate a **character**; double quotes create a **string** literal. While 'a' is a single character literal, "a" is a string literal.

like always, the Boolean data type returns just 2 different values: **true**(1) and **false**(0).