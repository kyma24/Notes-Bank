```python
#formula: max(a,b) = (a+b+abs(a-b))/2
def max(a,b,c):
    x = (a + b + abs(a-b))/2
    return str(int((x + c + abs(x - c))/2)) + " eh o maior"
thres = input().split()
print(max(eval(thres[0]),eval(thres[1]),eval(thres[2])))
```