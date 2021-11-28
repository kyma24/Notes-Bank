-   classification graphically
    
    will eventually want to use all the features, but for simplicity start with only two of the features(Fare and Age). Using two features enables the user to visualize the data in a graph.
    
    On the x-axis have the passenger's fare and on the y-axis their age. The yellow dots are passengers that survived and the purple dots are passengers that didn't survive.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bf86c580-d4e4-4c84-8439-63a1333d0624/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T165142Z&X-Amz-Expires=86400&X-Amz-Signature=71833696efe4d04452def61397ac19c38bbee081f92700c176092858c541fc41&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    can see that there are more yellow dots at the bottom of the graph than the top. This is bc children were more likely to survive than adults, which fits the intuition. Similarly there are more yellow dots on the right of the graph, meaning people that paid more were more likely to survive.
    
    The task of a linear model is to find the line that best separates the two classes, so that the yellow points are on one side and the purple points are the other.
    
    Here is example of a good line. The line is used to make predictions abt new passengers. If a passenger's datapoint lies on the right side of the line, would predict that they survive. If on the left side, would predict that they didn't survive.
    
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ff56610a-85b6-4edf-b502-38deb561fc05/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210308T165156Z&X-Amz-Expires=86400&X-Amz-Signature=afb9ef1c2dcb641800281c84570faad47cde17f491858a7a367edc44bad51a4c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
    
    The challenge of building the model will be determining what the best possible line is.