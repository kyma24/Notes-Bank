output "Hello world!" to the screen.
To do that, will add **cout << "Hello world!";** line to the main() function body:
```cpp
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello world!";
	return 0;
}
```
**cout** is the stream object used to perfrom output on the standard output device which is usually the display screen.
cout is used in combo with the **insert operator <<**.

note that in C++, **streams** are used to perform input and output operations.

can add **multiple insertion operators** after cout.
```cpp
//i.e.
{
	cout << "This " << "is " << "awesome!";
	return 0;
}
```
in C++, the semicolon is used to terminate a statement(like Java and JavaScript). Each statement must end w/ a semicolon. It indicates the end of one logical expression.