-   basics: stats review
    -   quartiles & percentiles/median
        
        median - 50th percentile
        
        50% of data is less than median & 50% of data is greater than median.
        
        25th percentile & 75th percentile: inter quartile range = 75th percentile(quartile 3) - 25th percentile(quartile 1)
        
        ```
        15, 16, 18, 19, 22, 24, 29, 30, 34
        ```
        
        9 values, so 25% of data would be around 2 datapoints. so the 3rd datapoint is greater than 25% of the data. Thus, the 25th percentile is 18.
        
        similarly, 75% of the data is approximately 6 datapoints. So the 7th datapoint is greater than 75% of the data. Thus, the 75th percentile is 29.
        
        full range of data is btwn 15 and 34. the 25th and 75th percentiles tell us that half of our data is between 18 and 29. this helps us gain understanding of how data is distributed.
        
    -   standard deviation & variance
        
        we can get deeper understanding of distribution of data with the standard deviation and variance.
        
        the standard deviation and variance are measures of how dispersed or spread out the data is.
        
        ```
        15, 16, 18, 19, 22, 24, 29, 30, 34
        ```
        
        remember: mean is 23.
        
        let's calculate how far each value is from the mean. 15 is 8 away from the mean, etc.
        
        list of distances:
        
        ```
        8, 7, 5, 4, 1, 1, 6, 7, 11
        ```
        
        then we square the values and add them together.
        
        $8^2 + 7^2 + 5^2 + 4^2 + 1^2 + 1^2 + 6^2 + 7^2 + 11^2 = 64 + 49 + 25 + 16 + 1 + 1 + 36 + 49 + 121 = 362$
        
        we divide this value by the total number of values and that gives us the **variance**.
        
        ```
        362 / 9 = 40.22
        ```
        
        to get standard deviation, just take the square root of this number and get 6.34.
        
        if our data is normally distributed(like the graph below), 68% of the population is within one standard deviation of the mean. In the graph, we've highlighted the area within one standard deviation of the mean. You can see that the shaded area is about 2/3 or more precisely 68% of the total area under the curve. If we assume that our data is normally distributed, we can say that 68% of the data is within one standard deviation of the mean.
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8f208562-7fb6-4a09-b156-de37911c6fcc/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164218Z&X-Amz-Expires=86400&X-Amz-Signature=275c283d59fbc5ae74bb4dbce4e7de5fc9921536c102ff43ad88edd7bfc45337&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        in the example, while the numbers are likely not exactly normally distributed, we assume that they are and say that approx. 68% of the population has a value within one standard deviation of the mean. Since the mean is 23 and the standard deviation is 6.34, we can say that approx. 68% of values in our population are btwn 16.66(23-6.34) and 29.34(23+6.34).
        
        note: even though data is never a perfect normal distribution, we can still use the standard deviation to gain insight abt how the data is distributed.
        
    -   stats w/ Python
        
        we can calculate all of these operations w/ Python. We will use the Python package numpy. It will also be used later on for manipulating arrays, but for now we will just use a few functions for statistical calculations: mean, median, percentile, std, var.
        
        first, import package. standard practice to nickname numpy as np
        
        ```python
        import numpy as np
        ```
        
        let's initialize the variable data to have the list of values.
        
        ```python
        data = [15, 16, 18, 19, 22, 24, 29, 30, 34]
        ```
        
        now we can use numpy functions. for the mean, median, standard deviation and variance functions, we just pass in the data list. For the percentile function we pass the data list and the percentile(as a number btwn 0 and 100).
        
        ```python
        import numpy as np
        data = [15, 16, 18, 19, 22, 24, 29, 30, 34]
        print("mean:", np.mean(data))
        print("median:", np.median(data))
        print("50th percentile(median):", np.percentile(data, 50))
        print("25th percentile:", np.percentile(data, 25))
        print("75th percentile:", np.percentile(data, 75))
        print("standard deviation:", np.std(data))
        print("variance", np.var(data))
        ```
        
        note: numpy is python library that allows fast & easy mathematical operations to be performed on arrays.