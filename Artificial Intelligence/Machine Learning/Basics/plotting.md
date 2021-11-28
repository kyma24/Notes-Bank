-   basics: plotting
    -   scatter plot
        
        can use the **matplotlib** library to plot the data. Plotting the data can often help build intuition about the data.
        
        first need to import matplotlib. It's a standard practice to nickname it plt.
        
        ```python
        import matplotlib.pyplot as plt
        ```
        
        use the scatter function to plot the data. The first argument of the scatter function is the x-axis and the second argument is the y-axis.
        
        ```python
        plt.scatter(df['Age'], df['Fare'])
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3f6f0e4a-840d-449c-9a09-d0f9ccf640ac/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164641Z&X-Amz-Expires=86400&X-Amz-Signature=a6a990ebc9b347f91cdb370be5d1ae58fdc1615531925a210a30b9f542ed4037&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        this plots the Age on the x-axis and the Fare on the y-axis.
        
        to make it easier to interpret, can add x and y labels.
        
        ```python
        plt.xlabel('Age')
        plt.ylabel('Fare')
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/28f8fb5f-a817-41b2-938e-28d87054f0f3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164654Z&X-Amz-Expires=86400&X-Amz-Signature=97b943e1d92571dd4d491ebeb76c9c9c91f4575815b1b6ec71604cf1bbaf9df7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        can also use the data to color code the scatter plot. This will give each of the three classes a different color. Add the **c** parameter and give it a Pandas series. In this case, the Pandas series has 3 possible values(1st, 2nd, and 3rd class), so will see the datapoints each get one of three colors.
        
        ```python
        plt.scatter(df['Age'], df['Fare'], c=df['Pclass'])
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2a5f3c47-7069-4e2f-a563-66129d8b4295/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164706Z&X-Amz-Expires=86400&X-Amz-Signature=b0dd41e4da6e25a7c51a88781be08d57b5ecdd2bd485d7ff415620961d3512a0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        the purple dots are first class, the green dots are second class, and the yellow dots are third class.
        
        note: a scatter plot is used to show all the values from the data on a graph. In order to get a visual representation of the data, have to limit the data to two features.
        
    -   line graph
        
        now that can put individual datapoints on a plot, see how to draw the line. The **plot** function does just that. the following draws a line to approximately separate the 1st class from the 2nd and 3rd class. From eyeballing, wll put the line from (0, 85) to (80, 5). The syntax below has a list of the x values and a list of the y values.
        
        ```python
        plt.plot([0, 80], [85, 5])
        ```
        
        ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5611aa19-0236-4cf2-840b-6040148037c0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164723Z&X-Amz-Expires=86400&X-Amz-Signature=d50a2914b821028b6dfbbc2c719ac067a35300582f4292aab569eea050bcb0fd&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
        
        can see that the yellow(3rd class) and green(2nd class) points are mostly below the line and the purple(1st class) are mostly above. This is did manually, but later will learn how to do it algorithmically.