the **cout** object doesn't insert a line break at the end of the output.
One way to print two lines is to use the **endl** manipulator, which will put in a line break.
```cpp
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello world!" << endl;
	cout << "I love programming!";
	return 0;
}
```

Like Java/Python, the new line character **\\n** can be used as an alternative to **endl**.
Using a single cout statement w/ as many instances of \\n as the program requires will print out **multiple lines of text**.
```cpp
//i.e.
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello world! \n";
	cout << "I love programming!\n" << "I love C++\n";
	return 0;
}
```

like always, the **backslash**(\\) is called an **escape character**, and indicates a "special" character.