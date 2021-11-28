**comments** are explanatory statements that can be included in the C++ code to explain what the code is doing.
The compiler ignores everything that appears in the comment, so none of that info shows in the result.

A comment beginning w/ **two slashes(//)** is called a single-line comment. The slashes tell the compiler to ignore everything that follows, until the end of the line.
```cpp
//i.e.
#include <iostream>
using namespace std;

int main()
{
	// prints "Hello world"
	cout << "Hellow world!";
	return 0;
}
```
when the abv code is compiled, it will ignore the **// prints "Hello world"** statement.

note: adding comments to the code is a good practice. It facilitates a clear understanding of the code for the user.


comments that require multiple lines begin w/ **/\*** and end w/ **\*/**
these can be placed on the same line or insert one or more lines between them
```cpp
/*We are going to
	print "Hello world!"*/
	
	cout << "Hello world!"; // prints Hello world!
```
comments can be written anywhere, and can be repeated any number of times throughout the code.