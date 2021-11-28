```cpp
//syntax:
for (init; condition; increment) {
	statement(s);
}
```
exact same as Java.
1. the init step is executed first, and doesn't repeat.
2. the condition is evaluated, and the body of the loop is executed if the condition is true.
3. in the next step, the increment statement updates the loop control variable.
4. then, the loop's body repeats itself, only stopping when the condition becomes false.
```cpp
for (int x = 1; x < 10; x ++) {
	//some code
}
```
note that the init and increment statements may be left out, if not needed, but remember that the semicolons are mandatory.

```cpp
for (int a = 0; a < 10; a++) {
	cout << a << endl;
}
```