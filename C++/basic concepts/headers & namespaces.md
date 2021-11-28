## Headers
C++ offers various headers, each of which contains info needed for programs to work properly.
Have already seen the standard **\<iostream>** header on the first C++ program:
```cpp
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello world!";
	return 0;
}
```

**#include** is used for adding a standard or user-defined header files to the program.

note that the **\<iostream>** header defines the standard stream objects that input and output data.


## Namespaces
A **namespace** is a declarative region that provides a scope to the identifiers(names of elements) inside it.
In the code, the line **using namespace std;** tells the compiler to use the std(standard) namespace.
```cpp
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello world!";
	return 0;
}
```
the **std** namespace includes features of the **C++ Standard Library**.