-   AcWing #21: Fibonacci (Java) #1(1144 ms)
    
    ```java
    class Solution {
        public int Fibonacci(int n) 
        {
            if (n == 0)
                return 0;
            else if (n == 1)
                return 1;
            else
                return Fibonacci (n-2) + Fibonacci (n-1);
        }
    }
    ```