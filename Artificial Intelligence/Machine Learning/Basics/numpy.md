-   basics: numpy
    -   basics
        
        it is a Python package for manipulating lists and tables of numerical data. It can be used to do a lot of statistical calculations. The list or table of data is called a **numpy array**.(the data object in numpy is called an array)
        
        Often will take the data from the pandas DataFrame and put it in numpy arrays. Pandas DataFrames are very useful because there are the column names and other text data that makes it humanly readable. A DataFrame, while easy for a human to read, is not the ideal format for doing calculations. The numpy arrays are generally less human readable, but are in a format that enables the necessary computation.
        
        note: **Numpy** is a Python module for doing calculations on tables of data. Pandas was actually built using Numpy as it's foundation.
        
    -   converting from Pandas Series to Numpy Array
        
        Often start with the data in the Pandas DataFrame, but then want to convert it to a numpy array. The **values** attribute does this for the user.
        
        i.e. convert the **Fare** column to a **numpy array**.
        
        first, recall that it is possible to use the single bracket notation to get a pandas Series of the Fare column as follows.
        
        ```python
        df['Fare']
        ```
        
        then the values attribute can be used to get the values as a numpy array.
        
        ```python
        df['Fare'].values
        ```
        
        ```python
        import pandas as pd
        df =
        pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
        print(df['Fare'].values)
        ```
        
        the above array will look like this:
        
        ```python
        array([ 7.25 , 71.2833,  7.925, 53.1, 8.05, 8.4583, …
        ```
        
        the result is a 1-dimensional array. This can be told since there's only one set of brackets and it only expands across the page, not down as well.
        
        note: the **values** attribute of a Pandas Series give the data as a numpy array.
        
    -   converting from Pandas DataFrame to a Numpy Array
        
        If a pandas DataFrame is present instead of a Series, can still use the values attribute, but it returns a **2-dimensional numpy array**.
        
        Recall that it is possible to create a smaller pandas DataFrame with the following syntax.
        
        ```python
        df[['Pclass', 'Fare', 'Age']]
        ```
        
        again, apply the **values** attribute to get a numpy array.
        
        ```python
        df[['Pclass', 'Fare', 'Age']].values
        ```
        
        ```python
        import pandas as pd
        df =
        pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
        print(df[['Pclass', 'Fare', 'Age']].values)
        ```
        
        this is what the above array looks like:
        
        ```python
        array([[ 3.    ,  7.25  , 22.    ],
               [ 1.    , 71.2833, 38.    ],
               [ 3.    ,  7.925 , 26.    ],
                            ...           ,
               [ 3.    , 23.45  ,  7.    ],
               [ 1.    , 30.    , 26.    ],
               [ 3.    ,  7.75  , 32.    ]])
        ```
        
        this is a 2-dimensional numpy array. It can be told because there's two sets of brackets and it expands both across the page and down.
        
    -   numpy shape attribute
        
        the numpy **shape** attribute is used to determine the size of the numpy array.
        
        the size tells the user how many rows and columns are in the data.
        
        first, to create a numpy array with the Pclass, Fare, and Age.
        
        ```python
        arr = df[['Pclass', 'Fare', 'Age']].values
        ```
        
        if the shape is looked at, the number of rows and the number of columns are gotten:
        
        ```python
        print(arr.shape) #(887, 3)
        ```
        
        ```python
        import pandas as pd
        df =
        pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
        arr = df[['Pclass', 'Fare', 'Age']].values
        print(arr.shape)
        ```
        
        the result means we have 887 rows and 3 columns.
        
        note: use the shape attribute to find the number of rows and number of columns for a Numpy array. The shape attribute can also be used on a pandas DataFrame(df.shape).
        
    -   select from a numpy array
        
        assume the following numpy array has been created:
        
        ```python
        arr = df[['Pclass', 'Fare', 'Age']].values
        ```
        
        a single element from a numpy array can be selected with the following:
        
        ```python
        arr[0, 1]
        ```
        
        this will be the **2nd column** of the **1st row**(remember that this starts counting at **0**)
        
        so it'll be the Fare of the 1st passenger, or 7.25
        
        can also select a single row, for example, the whole row of the first passenger:
        
        ```python
        print(arr[0])
        ```
        
        to select a single column, in this case the Age column, special syntax has to be used:
        
        ```python
        print(arr[:,2])
        ```
        
        ```python
        import pandas as pd
        df =
        pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
        arr = df[['Pclass', 'Fare', 'Age']].values
        print(arr[0, 1])
        print(arr[0])
        print(arr[:,2])
        ```
        
        the syntax can be interpreted as all the rows are being taken, but just the column at index 2.
        
        note: using different syntax within brackets, it is possible to select single values, a whole row or a whole column.
        
        ```python
        arr = df[['Pclass', 'Fare', 'Age']].values
        #select all the fares of the passengers:
        arr[:, 1]
        ```
        
    -   masking
        
        often times the user will want to select all the rows that meet a certain criteria.
        
        in this example, all the rows of children(passengers under the age of 18) will be selected. A reminder of the definition of the array:
        
        ```python
        arr = df[['Pclass', 'Fare', 'Age']].values
        ```
        
        recall that the age column can be found with the following syntax:
        
        ```python
        arr[:, 2]
        ```
        
        first a person usually creates what is called a mask first. This is an array of Boolean values of whether the passenger is a child or not.
        
        ```python
        mask = arr[:, 2] < 18
        ```
        
        looking at the mask array to make sure it is understandable:
        
        ```python
        array([False, False, False, False, False, False, False, True, False, …
        ```
        
        the False values mean adult and the True values mean child, so the first 7 passengers are adults, the 8th is a child, and the 9th is an adult again. Now the mask can be used to just select the rows that are needed:
        
        ```python
        array([[3., 21.075, 2.],
               [2., 30.0708, 14.],
               [3., 16.7, 4.],
               [3., 7.8542, 14.],
        ```
        
        recall that the third column is the passengers age: it is seen that all the rows here are for passengers that are children.
        
        generally, it isn't needed to define a mask variable and can do the above in just as ingle line:
        
        ```python
        arr[arr[:, 2] < 18]
        ```
        
        ```python
        import pandas as pd
        
        df =
        pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
        #take the first 10 values for simplicity
        arr = df[['Pclass', 'Fare', 'Age']].values[:10]
        
        mask = arr[:, 2] < 18
        print(arr[mask])
        print(arr[arr[:, 2] < 18])
        
        #note: a mask is a boolean array that tells the user which values from the array that the user needs.
        ```
        
    -   summing and counting
        
        i.e. the user wants to know how many of the passengers are children. Still have the same array definition and can take the mask or boolean values from the previous part.
        
        ```python
        arr = df[['Pclass', 'Fare', 'Age']].values
        mask = arr[:, 2] < 18
        ```
        
        recall that True values are interpreted as 1 and False values are interpreted as 0. So just sum up the array and that's equivalent to counting the number of true values.
        
        ```python
        print(mask.sum())
        ```
        
        again, there is no need to define the mask variable.
        
        ```python
        print((arr[:, 2] < 18).sum())
        ```
        
        ```python
        import pandas as pd
        
        df = 
        pd.read_csv('<https://sololearn.com/uploads/files/titanic.csv>')
        arr = df[['Pclass', 'Fare', 'Age']].values
        mask = arr[:, 2] < 18
        
        print(mask.sum())
        print((arr[:, 2] < 18).sum())
        ```