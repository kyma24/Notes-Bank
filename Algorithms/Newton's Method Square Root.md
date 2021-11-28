```python
def sqrt(n):
	root = n/2 # initial guess will be 1/2 of n
	for k in range(20):
		root = (1/2)*(root + (n/root))
	
	return root
```

Newton's Method performs iterative computation that converges on correct value.

Equation ${newguess = \frac{1}{2}*(oldguess+\frac{n}{oldguess})}$ takes value ${n}$ and repeatedly guesses the square root by making each ${newguess}$ the ${oldguess}$ in the subsequent iteration. The initial guess used here is ${\frac{n}{2}}$. Above shows a function definition that accepts a value ${n}$ and returns the square root of ${n}$ after making 20 guesses.