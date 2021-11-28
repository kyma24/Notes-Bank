## Declaring Variables
the user has the option to assign a value to the variable at the time that the variable is declared or to declare it and assign a value later.
can also change the value of a variable.
```cpp
//i.e.
int a;
int b = 42;

a = 10;
b = 3;
```
can also assign a value to a variable only in a declared data type.

## User Input
to enable the user to input a value, use **cin** in combo w/ the extraction operator(**>>**). The variable containing the extracted data follows the operator.
The following example shows how to accept user input and store it in the **num** variable:
```cpp
int num;
cin >> num;
```
as with **cout**, extractions on **cin** can be chained to request more than one input in a single statement: cin >> a >> b;

## Accepting User Input
the following program prompts the user to input a number and stores it in the variable a:
```cpp
#include <iostream>
using namespace std;

int main()
{
	int a;
	cout << "Please enter a number \n";
	cin >> a;
	
	return 0;
}
```
when the program runs, it displays the message "Please enter a number", and then waits for the user to enter a number and press Enter, or Return.
The entered number is stored in the variable **a**.

The program willl wait for as long as the user needs to type in a number.

you can accept user input multiple times throughout the program:
```cpp
#include <iostream>
using namespace std;

int main()
{
	int a, b;
	cout << "Enter a number \n";
	cin >> a;
	cout << "Enter another number \n";
	cin >> b;
	
	return 0;
}
```

let's create a program that accepts the input of two numbers and prints their sum.
```cpp
#include <iostream>
using namespace std;

int main()
{
	int a, b;
	int sum;
	cout << "Enter a number \n";
	cin >> a;
	cout << "Enter another number \n";
	cin >> b;
	sum = a + b;
	cout << "Sum is: " << sum << endl;
	
	return 0;
}
```