conditional expressions provide the functionality of if statements while using less code. They shouldn't be overused, as they can easily reduce readability, but are often useful when assigning variables.

Conditional expressions are also known as applications of the **ternary operator**.

```python
#i.e.
a = 7
b = 1 if a >= 5 else 42
print(b)
```

the ternary operator checks the condition and returns the corresponding value.

In the example abv, as the condition is true, **b** is assigned 1. If **a** was less than 5, it would have been assigned 42.

```python
#i.e.
status = 1
msg = "Logout" if status == 1 else "Login"
```

The ternary operator is so called bc unlike most operators it takes 3 arguments.