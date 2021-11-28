Given a number of stairs, you can either go one or jump two per step.

Python:
```python
def stair(k):
    global count
    if k == s:
        count += 1
        return
    if k > s:
        return

    stair(k + 1)
    stair(k + 2)

count = 0
s = int(input())
stair(0)
print(count)
```

Java:
```java
import java.util.Scanner;

public class Main
{
    public static int count = 0;
    public static int stair = 0;

    public static void path (int k)
    {
        if (k == stair)
            count += 1;

        if (k > stair)
            return;

        path (k + 2);
        path (k + 1);
    }

    public static void main(String[] args)
    {
        Scanner cin = new Scanner(System.in);

        stair = cin.nextInt();

        path(0);

        System.out.println(count);
    }
}
```