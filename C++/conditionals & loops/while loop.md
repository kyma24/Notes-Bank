```cpp
//syntax:
while (condition) {
	statement(s);
}
```
the loop iterates while the condition is true.

the loop's body is the block of statements within curly braces.
```cpp
int num = 1;
while (num < 6) {
	cout << "Number: " << num << endl;
	num = num + 1;
}
```

the increment value can be changed. if changed, the number of times the loop will run will be divided by that amount.
```cpp
int num = 1;
while (num < 6) {
	cout << "Number: " << num << endl;
	num = num + 3;
}
```
w/o a increment statement, it will be a deadloop.

the loop can be used to obtain multiple inputs from the user.
```cpp
int num = 1;
int number;

while (num <= 5) {
	cin >> number;
	num++;
}
```

can also make the loop calculate the sum of the numbers the user has entered.
```cpp
int num = 1;
it number;
int total = 0;

while (num <= 5) {
	cin >> number;
	total += number;
	num ++;
}
cout << total << endl;
```