unlike **for** and **while** loops, which test the loop condition @ the top of the loop, the **do...while** loop checks its condition at the bottom of the loop.
A **do...while** loop is similar to a **while** loop. The one difference is that a **do...while** loop is guaranteed to execute **at least one time**, bc the statement is executed before the condition is established.
```cpp
//syntax:
do {
	statement(s);
} while(condition);
```
i.e. can take the input from the user, then check it. If the input is wrong, can take it again.

```cpp
//i.e.
int a = 0;
do {
	cout << a << endl;
	a++;
} while(a < 5);
```