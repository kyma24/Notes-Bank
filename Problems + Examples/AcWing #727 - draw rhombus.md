```python
n = int(input())

cx = n // 2
cy = n // 2

for i in range(0, n):
	for j in range(0, n):
		if (abs(i-cx) + abs(j-cy)) <= n//2: # if manhattan distance less than/equal to half of the input
			print("*", end="")
		else:
			print(" ", end="")
	print("")
```

Manhattan distance: distance between points ${(x_{1}, y_{1})}$ and ${(x_{2}, y_{2})}$ on a grid is ${|x_{1} - x_{2}| + |y_{1} - y_{2}|}$
![Manhattan region of radius 4. Each number is the Manhattan distance from the center point 0.](https://www.researchgate.net/profile/Sinan-Kockara/publication/282418255/figure/fig11/AS:292765545058310@1446812153514/Manhattan-region-of-radius-4-Each-number-is-the-Manhattan-distance-from-the-center-point.png)