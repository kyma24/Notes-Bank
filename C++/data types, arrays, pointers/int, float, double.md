the **integer** type holds non-fractional numbers, which can be positive or negative. Examples of itegers would include 42, -42, and similar numbers.
the size of the integer type varies according to the architecture of the system on which the program runs, although 4 bytes is the minimum size in most modern system architectures.

use the **int** keyword to define the integer data type.
```cpp
int a = 42;
```

several of the basic types, including integers, can be modified using one or more of these type **modifiers**:
- **signed**: a signed integer can hold both negative and positive numbers
- **unsigned**: an unsigned integer can hold only positive values
- **short**: half of the default size
- **long**: twice the default size

```cpp
//i.e.
unsigned long int a;
```

note that the integer data type reserves 4-8 bytes depending on the operating system.

### Floating Point Numbers
a **floating point** type variable can hold a real number, such as 420.0, -3.33, or 0.03325.
the words floating point refer to the fact that a varying number of digits can appear before and after the decimal point.

there are 3 different floating point data types: **float**, **double**, and **long double**.

in most modern architectures, a **float** is 4 bytes, a **double** is 8, and a **long double** can be equivalent to a double(8 bytes), or even 16 bytes.
```cpp
//i.e.
double temp = 4.21;
```

note that floating point data types are always **signed**, which means that they have the capability to hold both positive and negative values.