sometimes need to test a variable for equality against multiple values. That can be achieved by using multiple if statements.
```cpp
//i.e.
int age = 42;
if (age == 16) {
	cout << "Too young";
}
if (age == 42) {
	cout << "Adult"
}
if (age == 70) {
	cout << "Senior"
}
```

the **switch** statement tests a variable against a list of values, which are called **cases**, to determine whether it is equal to any of them.
```cpp
switch (expression) {
	case value 1:
		statement(s);
		break;
	case value 2:
		statement(s);
		break;
		...
	case value N:
		statement(s);
		break;
}
```
switch evaluates the expression to determine whether it's equal to the value in the case statement. If a match is found, it executes the statements in that case.
a switch can contain any number of **case** statements, which are followed by the **value** in question and a **colon**.

```cpp
//age example with switch
int age = 42;
switch (age) {
	case 16:
		cout << "Too young";
		break;
	case 42:
		cout << "Adult";
		break;
	case 70:
		cout << "Senior";
		break;
}
```

### the default Case
in a switch statement, the optional **default** case can be used to perform a task when none of the cases is determined to be true.
```cpp
//i.e.
int age = 25;
switch (age) {
	case 16:
		cout << "Too young";
		break;
	case 42:
		cout << "Adult";
		break;
	case 70:
		cout << "Senior";
		break;
	default:
		cout << "This is the default case";
}
```

the **break** statement's role is to terminate the switch statement.
In instances in which the variable is equal to a case, the statements that come after the case continue to execute until they encouter a **break** statement. In other words, leaving out a **break** statement results in the execution of all of the statements in the following cases, even those that don't match the expression.
```cpp
//i.e.
int age = 42;
switch (age) {
	case 16:
		cout << "Too young" << endl;
	case 42:
		cout << "Adult" << endl;
	case 70:
		cout << "Senior" << endl;
	default:
		cout << "This is the default case" << endl;
}
```
as seen, the program executed the matching case statement, printing "Adult" to the screen. W/ no specified **break** statement, the statements continued to run after the matching case. Thus, all the other case statements printed. This type of behavior is called **fall-through**.
However, as the switch statement's final case, the **default** case requires no **break** statement.