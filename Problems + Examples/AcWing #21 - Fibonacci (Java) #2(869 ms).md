-   AcWing #21: Fibonacci (Java) #2(869 ms)
    
    ```java
    class Solution {
        public int Fibonacci(int n) 
        {
            if (n == 0)
                return 0;
                
            int[] f = new int[n+1];
            
            f[0] = 0;
            f[1] = 1;
            
            for (int i =2; i < n+1; i++ )
            {
                f [i] = f[i-2] + f[i-1];
            }
            return f[n];
        }
    }
    ```