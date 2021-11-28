Given length and width of grid by user, find the number of paths from one corner to the opposite.

Python:
```python
def dfs (x, y):
    global a
    if x == n and y == m:
        a += 1
    else:
        if x < n:
            dfs (x + 1, y)
        if y < m:
            dfs (x, y + 1)

global n, m
a = 0
n, m = map(int, input().split())
a = 0

dfs (0, 0)
print (a)
```

Java:
```java
import java.util.Scanner;

public class Main
{
    public static int row = 0;
    public static int col = 0;

    public static int ans = 0;

    public static void dfs (int x, int y)
    {
        if (x == row && y == col)
            ans += 1;
        else
        {
            if (x < row)
                dfs (x + 1, y);

            if (y < col)
                dfs (x, y + 1);
        }
    }

    public static void main (String[] args)
    {
        Scanner cin = new Scanner(System.in);

        row = cin.nextInt();
        col = cin.nextInt();

        dfs (0, 0);
        System.out.println (ans);
    }
}
```