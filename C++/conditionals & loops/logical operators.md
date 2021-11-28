```cpp
//i.e. and operator
int age = 20;
if (age > 16 && age < 60) {
	cout << "Accepted!" << endl;
}
```

```cpp
//i.e. multiple and operators
int age = 20;
int grade = 80;

if (age > 16 && age < 60 && grade > 50) {
	cout << "Accepted!" << endl;
}
```

```cpp
//i.e. or operator
int age = 16;
int score = 90;
if (age > 20 || score > 50) {
	cout << "Accepted!" << endl;
}
```

```cpp
//i.e. not operator
int age = 10;
if (!(age > 16)) {
	cout << "Your age is less than 16" << endl;
}
```