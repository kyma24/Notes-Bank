the increment operator has 2 forms: **prefix** and **postfix**
```cpp
++x; // prefix
x++; //postfix
```
**Prefix** increments the value, and then proceeds with the expression.
**Postfix** evaluates the expression and then performs the incrementing.

**Prefix example:**
```cpp
x = 5;
y = ++x;
// x is 6, y is 6
```

**Postfix example:**
```cpp
x = 5;
y = x++;
// x is 6, y is 5
```

the **prefix** example increments the value of x, and then assigns it to y.
the **postfix** example assigns the value of x to y, and then increments it.



the **decrement** operator(--) works in much the same way as the increment operator, but instead of increasing the value, it decreases it by one.
```cpp
--x; // prefix
x--;
```
