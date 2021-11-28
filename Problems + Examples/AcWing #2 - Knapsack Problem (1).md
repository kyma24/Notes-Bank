have N items and a capacity V backpack. each item can only be used once.
#### Input:
two integers in the first line, N and V. Separated by spaces, respectively indicating the number of items and the volume of the backpack.
Next there are N lines, two integers per line, vi and wi. Separated by spaces, indicating the volume and the value of the item respectively.

#### Output:
output an integer that represents the maximum value.

#### Data Range:
0 < N , V ≤ 1000
0 < vi , wi ≤ 1000

```python
def max(n,b,c,i):
	#n is N
	#b is V
	#c is v
	#i is w
	

ipt = input().split()
N = ipt[0]
V = ipt[1]
v = [0] * N
w = [0] * N
for i in range(0,N):
	f = input().split()
	v[i] = f[0]
	w[i] = f[1]