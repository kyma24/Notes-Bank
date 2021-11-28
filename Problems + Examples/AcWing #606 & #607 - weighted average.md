-   AcWing #606: weighted average
    
    Values 0 ≤ A,B ≤ 10.0 are inputted on separate lines. A is with weight 3.5, B is with weight 7.5. Output is in format "MEDIA = X".
    
    ```python
    def weighted(a,b):
        return "MEDIA = " + f'{((a*3.5)+(b*7.5))/11:.5f}'
    
    A = eval(input())
    B = eval(input())
    print(weighted(A,B))
    ```

- AcWing #607: weighted average
	
	Values 0 ≤ A, B, C ≤ 10.0 are inputted on separate lines. A is with weight 2, B is with weight 3, C is with weight 5. Output is in format "MEDIA = X".
	
	```python
	def weighted(a,b,c):
		return "MEDIA = " + f'{((a*2)+(b*3)+(c*5))/10:.1f}'
	
	A = eval(input())
	B = eval(input())
	C = eval(input())
	print(weighted(A,B,C))
	```