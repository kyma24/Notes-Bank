-   AcWing #21: Fibonacci (Python) (1903 ms)
    
    Input a number n, and find the nth term of the Fibonacci sequence. Assume that it starts at value 0, at the value of 0, with n less than equal to 39.
    
    ```python
    class Solution(object):
        def Fibonacci(self, n):
            """
            :type n: int
            :rtype: int
    
            result = 0
            if n == 0:
                result = 0
            elif n == 1:
                result = 1
            else:
                result = Fibonacci(n-1) + Fibonacci(n-2)
                
            return result
            """
            result = [0]*(n+1)
    				 #defines an array with n+1 items, each with a value of 0
            
            for i in range (0, n+1):
                if i == 0:
                    result[i] = 0
                elif i == 1:
                    result[i] = 1
                else:
                    result [i] = result [i-1] + result[i-2]
    
            return result[n]
    ```