an **if** statement can be followed by an optional **else** statement, which executes when the condition is **false**.
```cpp
//syntax:
if (condition) {
	//statements
}
else {
	//statements
}
```
just like in Java: if only one statement is used inside if/else statement, the braces an be omitted.

```cpp
int mark = 90;

if (mark < 50) {
	cout << "You failed." << endl;
}
else {
	cout << "You passed." << endl;
}
```

```cpp
//i.e. nested if statement
int mark = 100;
if (mark >= 50) {
	cout << "You passed." << endl;
	if (mark == 100) {
		cout << "Perfect!" << endl;
	}
}
else {
	cout << "You failed." << endl;
}
```

```cpp
//i.e. nested if else statement
int age = 18;
if (age > 14) {
	if (age >= 18) {
		cout << "Adult";
	}
	else {
		cout << "Teenager";
	}
}
else {
	if (age > 0) {
		cout << "Child";
	}
	else {
		cout << "Something's wrong";
	}
}
```