-   basics: reading data w/ pandas
    
    One of the reasons why Python is so popular is that there are numerous helpful python modules for working with data. One of these is **Pandas**.
    
    Pandas is a Python module that helps the user read and manipulate data. What's cool abt this is that you can take in data and view it as a table that's humanly readable, but it can also be interpreted numerically so that you can do computations with it.
    
    we call this table of data a **DataFrame**.(the Pandas data object is called DataFrame)
    
    import Pandas to start. It's a standard practice to nickname it **pd** so that it's faster to type later on.
    
    ```python
    import pandas as pd
    ```
    
    As an example, a dataset of Titanic passengers will be worked with. For each passenger, there will be some data on them as well as whether or not they survived the crash.
    
    The data is stored as **CSV**(comma-separated values) file. The titanic.csv file is below. The first line is the header and then each subsequent line is the data for a single passenger.
    
    ```python
    Survived, Pclass, Sex, Age, Siblings/Spouses, Parents/Children, Fare
    0, 3, male, 22.0, 1, 0, 7.25
    1, 1, female, 38.0, 1, 0, 71.2833
    1, 3, female, 26.0, 0, 0, 7.925
    1, 1, female, 35.0, 1, 0, 53.1
    ```
    
    this data will be pulled into pandas so that it can be viewed as a DataFrame.
    
    The **read\_csv** function takes a file in csv format and converts it to a Pandas DataFrame.
    
    ```python
    df = pd.read_csv('titanic.csv')
    ```
    
    the **object df** is now the pandas dataframe with the Titanic dataset. Now we can use the **head** method to look at the data.
    
    The **head** method returns the first 5 rows of the DataFrame.
    
    ```python
    print(df.head())
    ```
    
    ```python
    import pandas as pd
    df =
    pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
    print(df.head())
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/780c244e-bfe5-4e0a-bfb2-088acb326fdf/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164337Z&X-Amz-Expires=86400&X-Amz-Signature=90884e9b0795cde90442c9f661ba0d4586948af7b32a8d971522c91ebea2c990&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    generally data is stored in CSV(comma-separated values) files, which we can easily read in w/ panda's read\_csv function. The head method returns the first 5 rows.
    
    usually the data is much too big for it to be completely displayed. Looking at the first few rows is the first step to understanding the data, but summary statistics may also be needed.
    
    In pandas, the **describe** method can be used. It returns a table of statistics about the columns.
    
    ```python
    print(df.describe())
    ```
    
    the line in the code below is added to force python to display all 6 columns. Without the line, it will abbreviate the results.
    
    ```python
    import pandas as pd
    pd.options.display.max_columns = 6
    df =
    pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
    print(df.describe())
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a68a59cd-5b9c-46d1-8f17-1ec59a4a4f1e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164349Z&X-Amz-Expires=86400&X-Amz-Signature=e51ad112e88dfe63647ba93a816c941c8e0842cb860d110871ef60da534a10f4&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    for each column there are several statistics. Note that it only gives statistics for the numerical columns.
    
    **Count**: this is the number of rows that have a value. In this case, every passenger has a value for each of the columns, so the value is 887(the total number of passengers)
    
    **Mean**: the standard average
    
    **Std**: standard deviation. Measure of how dispersed the data is
    
    **Min**: the smallest value
    
    **25%**: the 25th percentile(1st quartile)
    
    **50%**: the 50th percentile(2nd quartile, or median)
    
    **75%**: the 75th percentile(3rd quartile)
    
    **Max**: the largest value
    
    the pandas describe method is used to start building some intuition about the data.