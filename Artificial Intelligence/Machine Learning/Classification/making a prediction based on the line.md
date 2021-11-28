-   making a prediction based on the line
    
    look again at the same line
    
    ```html
    0 = (1)x + (-1)y - 30
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/567ca120-63bc-43c2-8800-323dfa6ae56c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T165302Z&X-Amz-Expires=86400&X-Amz-Signature=7a36a1af5164196733f9a5e8f4c3cf0e773ca58f56b47a739a0e0eb4cd99ac37&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    If take a passenger's data, can use the equation to determine which side of the line they fall on. i.e. have a passenger whose Fare is 100 and Age is 20.
    
    Plug in the values to the equation:
    
    ```html
    (1)100 + (-1)20 - 30 = 100 - 20 - 30 = 50
    ```
    
    since this value is positive, the point is on the right side of the line and would predict that the passenger survived.
    
    Now say a passenger had a Fare of 10 and their Age is 50. Plug these values into the equation.
    
    ```jsx
    (1)10 + (-1)50 - 30 = -70
    ```
    
    Since this value is negative, the point is on the left side of the line and would predict that the passenger didn't survive.
    
    Can see these 2 points on the plot below.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2fd57615-364c-40f5-a466-5ff32217c06f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T165313Z&X-Amz-Expires=86400&X-Amz-Signature=bdbe2e4372d3c2eb1c6770cde2494d4649218d2e6506c9f5267b9f78ba6897af&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    which side of the line a point lies on determines whether think that passenger will survive or not.