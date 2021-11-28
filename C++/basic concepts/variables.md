creating a **variable** reserves a memory location, or a space in memory for storing values. The compiler requires that the user provide a **data type** for each variable declared.
C++ offers a rich assortment of built-in as well as user defined **data types**.

**Integer**, a built-in type, represents a whole number value. Define integer using the keyword **int**.
C++ requires that the **type** and the **identifier** are specified for each variable defined.
An **identifier** is a name for a variable, function, class, module, or any other user-defined item. An identifier starts with a letter(A-Z or a-z) or an underscore(\_), followed by additional letters, underscores, and digits(0 to 9).
i.e. define a variable called **myVariable** that can hold **integer** values as follows:
```cpp
int myVariable = 10;
```
note that different operating systems can reserve different sizes of memory for the same data type.


now, assign a value to the variable and print it.
```cpp
#include <iostream>
using namespace std;

int main()
{
	int myVariable = 10;
	cout << myVariable;
	return 0;
}
```
the C++ programming language is **case-sensitive**, so **myVariable** and **myvariable** are two different identifiers.


define all variables with a **name** and a **data type** before using them in a program. In cases in which you have multiple variables of the same type, it's possible to define them in one declaration, separating them with **commas**:
```cpp
int a, b;
//defines two variables of type int
```
A variable can be assigned a value, and can be used to perform operations.
i.e. can create an additional value called **sum**, and add two variables together.
```cpp
int a = 30;
int b = 15;
int sum = a + b;
// now sum equals 45
```


create a program to calculate and print the sum of two integers.
```cpp
#include <iostream>
using namespace std;

int main()
{
	int a = 30;
	int b = 12;
	int sum = a + b;
	
	cout << sum;
	
	return 0;
}
```
