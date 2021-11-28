-   AcWing #616: distance between two points
    
    find the distance between two points. round to 4 decimal spaces. -10^9 ≤ xi, yi ≤ 10^9
    
    ```python
    import math
    def distance(x1,y1,x2,y2):
        diff1 = abs(x1-x2)
        diff2 = abs(y1-y2)
        return f'{math.sqrt((diff1**2)+(diff2**2)):.4f}'
    
    pt1 = input().split()
    pt2 = input().split()
    
    print(distance(eval(pt1[0]),eval(pt1[1]),eval(pt2[0]),eval(pt2[1])))
    ```