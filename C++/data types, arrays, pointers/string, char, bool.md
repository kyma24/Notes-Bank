a **string** is an ordered sequence of characters, enclosed in **double quotation marks**.
it is part of the Standard Library.
need to include the **\<string>** library to use the string data type.
alternatively, can also use a library that includes the string library.
```cpp
#include <string>
using namespace std;

int main() {
	string a = "I am learning C++";
	return 0;
}
```
the \<string> library is included in the \<iostream> library, so don't need to include \<string> separately, if already use \<iostream>.

### characters
a **char** variable holds a 1-byte integer. However, instead of interpreting the value of the **char** as an integer, the value of a char variable is typically interpreted as an ASCII character.
a character is enclosed between **single quotes**.
```cpp
//i.e.
char test = 'S';
```

note: **American Standard Code for Information Interchange(ASCII)** is a character-encoding scheme that is used to represent text in computers.

### booleans
Boolean variables only have 2 possible values: **true**(1) and **false**(0).
to declare a boolean variable, use the keyword **bool**.
```cpp
//i.e.
bool online = false;
bool logged_in = true;
```

note that if a Boolean variable is assigned to an integer, **true** becomes 1 and **false** becomes 0.
if an integer values is assigned to a Boolean, 0 becomes **false** and any value that has a non-zero value becomes **true**.