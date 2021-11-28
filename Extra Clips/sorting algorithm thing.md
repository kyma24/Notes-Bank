```python
for i in range(1, N-1):
	for j in range(i+1, N):
		if A[i] < A[j]:
			T = A[j]
			A[j] = A[i]
			A[i] = T
```
This thing sorts from max to min. woaaaaah