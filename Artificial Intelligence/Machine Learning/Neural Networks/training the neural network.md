### Loss
in order to train a neural network, we need to define a **loss function**. This is a measure of how far off the neural network is from being perfect. When we train the neural network, we are optimizing a loss function.

We will use **cross entropy** as the loss function. This is the same as the likelihood we used in logistic regression but is called by a different name in this context. We calculate the cross entropy as follows.
![contentImage](https://api.sololearn.com/DownloadFile?id=4106)

We multiply together the cross entropy values for all the datapoints.

Let's say we have two models to compare on a tiny dataset with 4 datapoints. Here is a table of the true values, the predicted probabilities for model 1 and the predicted probabilities for model 2.
![contentImage](https://api.sololearn.com/DownloadFile?id=3963)

The cross entropy for model 1 is as follows.
![contentImage](https://api.sololearn.com/DownloadFile?id=3964)

The cross entropy for model 2 is as follows.
![contentImage](https://api.sololearn.com/DownloadFile?id=3965)

Cross entropy will be higher the better the model is, thus since model 2 has higher cross entropy than model 1, it is the better model.

Just like we did with the likelihood function in logistic regression, we use the loss function to find the best possible model.

### Backpropagation
A neural network has a lot of parameters that we can control. There are several coefficients for each node and there can be lots of nodes. The process for updating these values to converge on the best possible model is quite complicated. The neural network works backwards from the output node iteratively updating the coefficients of the nodes. This process of moving backwards through the neural network is called **backpropagation** or **backprop**.

Here, won't go through all the details as it involves calculating partial derivatives, but the idea is that we initialize all the coefficient values and interatively change the values so that at every iteration we see improvement in the loss function. Eventually can't improve the loss function anymore and then we have found the **optimal model**.

note that before we create a neural network we fix the number of nodes and number of layers. Then we use backprop to iteratively update all of the coefficient values until we converge on an optimal neural network.