-   classification terminology
    
    look back at Titanic dataset. Here again is the Pandas DataFrame of the data:
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8a1b3173-9a46-45fe-b184-5d50389a1241/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T165108Z&X-Amz-Expires=86400&X-Amz-Signature=5b72a57c23af47e8433fc43aa67ec8db7478fb15cee1e6a88fa801124dddefc3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    The **Survived** column is what trying to predict. Call this the **target**. Can see that it's a list of 1's and 0's. A 1 means that the person survived, and a 0 means that they didn't.
    
    The remaining columns are the info abt the passenger that can be used to predict the target. Call each of these columns a **feature**. Features are the data that are used to make a prediction.
    
    Sometimes will hear features called predictors.
    
    While know whether each passenger in the dataset survived, like to be able to make predictions abt additional passengers that weren't able to collect that data for. Will build a machine learning **model** to help do this.