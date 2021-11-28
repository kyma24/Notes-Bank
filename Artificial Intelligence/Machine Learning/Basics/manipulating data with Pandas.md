-   basics: manipulating data with pandas
    
    often it is only needed to deal with some of the columns that are in the dataset. To select a single column, use the **square brackets** and the **column name**.
    
    in this example, just the column with the passenger fares is being selected.
    
    ```python
    col = df['Fare']
    print(col)
    ```
    
    the result is called a Pandas **Series**.
    
    A series is like a DataFrame, but it's just a single column.
    
    ```python
    import pandas as pd
    df =
    pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
    col = df['Fare']
    print(col)
    ```
    
    note: a Pandas Series is a single column from a Pandas DataFrame
    
    ```python
    #i.e.
    
    #based on this code, the data type of the variable age_col is a Pandas Series
    
    age_col = df['Age']
    ```
    
    can also select multiple columns from the original DataFrame, creating a smaller DataFrame.
    
    for example, the **Age**, **Sex**, and **Survived** columns can be selected from the original DataFrame
    
    the values can be put in a list as follows:
    
    ```python
    ['Age', 'Sex', 'Survived']
    ```
    
    now this list can be used inside of the bracket notation df\[...\] When printing a large DataFrame that's too big to display, the head method can be used to just print the first 5 rows.
    
    ```python
    small_df = df[['Age', 'Sex', 'Survived']]
    print(small_df.head())
    ```
    
    ```python
    import pandas as pd
    df =
    pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
    small_df = df[['Age', 'Sex', 'Survived']]
    print(small_df.head())
    ```
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1866866f-67b8-427b-b75a-b1de76b3951e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164519Z&X-Amz-Expires=86400&X-Amz-Signature=1d889f03829b3fba44abe65ec0561a95e1ae826f30a522e826c3b7b57f970bd0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    note: when selecting a single column from a Pandas DataFrame, the single square brackets are used. When selecting multiple columns, the double square brackets are used.
    
    ```python
    new_df = df[['Pclass', 'Age', 'Fare']]
    #creates DataFrame new_df which has columns Pclass, Age, & Fare
    ```
    
    often want the data in a slightly different format than it originally comes in. For example, the data has the sex of the passenger as a string("male" or "female"). This is easy for a human to read, but once computations are done on the data later, the value should be boolean values.
    
    can easily create a new column in the DataFrame that is True if the passenger is male and False if they're female.
    
    Recall the syntax for selecting the Sex column:
    
    ```python
    df['Sex']
    ```
    
    A Pandas Series will be created that will be a series of Trues and Falses(True if the passenger is male and False if the passenger is female).
    
    ```python
    df['Sex'] == 'male'
    ```
    
    now to create a column with this result. To create a new column, use the same bracket syntax(df\['male'\]) and then assign this new value to it.
    
    ```python
    df['male'] = df['Sex'] == 'male'
    ```
    
    ```python
    import pandas as pd
    df =
    pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
    df['male'] = df['Sex'] == 'male'
    print(df.head())
    ```
    
    the dataframe now looks as follows. Note the new column at the end.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0a2adba1-d114-492d-ae91-623f0cd6542b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T164533Z&X-Amz-Expires=86400&X-Amz-Signature=e7c82f37255609add74e916514b84d13ea42c68da9eb6f060d7db547526f3e21&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    often the data isn't in the ideal format. Luckily Python makes it easy for the user to create new columns based on the data so that it can be formatted appropriately