-   AcWing #609: wages
    
    ```python
    def wage(n,s,h):
        return "NUMBER = " + str(n) + "\\n" + "SALARY = U$ " + f'{s*h:.2f}'
    
    num = input()
    sal = eval(input())
    hr = eval(input())
    print(wage(num,sal,hr))
    ```