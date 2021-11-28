```python
def concatenate(*args):
    result = ""
    for i in range(len(args)):
        result += args[i]
        if i < len(args)-1:
            result += "-"
    return result

print(concatenate("I", "love", "Python", "!"))

#separates passed-in terms with a dash
```