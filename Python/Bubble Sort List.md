```python
def bubbleSort(l):
    for i in range(len(l)):
        hasSwapped = False
        for j in range(len(l)-i-1):
            if l[j] < l[j+1]:
                l[j], l[j+1] = l[j+1], l[j]
                hasSwapped = True
        if hasSwapped == False:
            print(i)
            break

L = [1, 3, 5, 9, 8]
bubbleSort(L)
print(L)
```