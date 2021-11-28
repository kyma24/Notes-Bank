the **if** statement is used to execute some code if a condition is true.
```cpp
// syntax:

if (condition) {
	//statements
}
```

the **condition** specifies which expression is to be evaluated. if the condition is true, the statements in the curly brackets are executed.

use **relational operators** to evaluate conditions.
```cpp
//i.e.
if (7 > 4) {
	cout << "Yes";
}
```
the **if** statement evaluates the condition(7 > 4), finds it to be **true**, and then executes the **cout** statement.
if change the greater operator to a less than operator(7 < 4), the statement won't be executed and nothing will be printed.

```cpp
//additional relational operators example:
if (10 == 10) {
	cout << "Yes";
}

if (10 != 10) {
	cout << "Yes";
}

int a = 55;
int b = 33;
if (a > b) {
	cout << "a is greater than b";
}
```