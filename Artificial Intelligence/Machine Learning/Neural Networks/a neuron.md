## What is a Neuron
An **artificial neuron**(often called a **node**) is modeled after a biological neuron. It is a simple object that can take input, do some calculations with the input, and produce an output.

We visually represent neurons as follows. x1 and x2 are the inputs. Inside the neuron, some computation is done based on x1 and x2 to produce the output y1.
![contentImage](https://api.sololearn.com/DownloadFile?id=3946)

Neurons can take any number of inputs and can also produce any number of outputs.

note that each neuron is only capable of a small computation, but when working together they become capable of solving large and complicated problems.

### Neuron Computations
Inside the neuron, to do the computation to produce the output, we first put the inputs into the following equation(just like in logistic regression)
![contentImage](https://api.sololearn.com/DownloadFile?id=4107)

Recall that x1 and x2 are the inputs. In logistic regression, we referred to the values w1, w2, and b as the coefficients. In neural networks, we refer to w1 and w2 as the **weights**, and b as the **bias**.

We plug this value into what is called an **activation function**. The above equation can have any result of any real number. The activation function condenses it into a fixed range(often between 0 and 1).

A commonly used activation function is the **sigmoid** function, the same function that had been used in logistic regression. Recall that this function produces a value between 0 and 1. It is defined as follows.
![contentImage](https://api.sololearn.com/DownloadFile?id=4097)

The sigmoid has the following shape.
![contentImage](https://api.sololearn.com/DownloadFile?id=4098)

To get the output from the inputs we do the following computation. The weights, w1 and w2, and the bias, b, control what the neuron does. We call these values(w1, w2, b) the **parameters**. The function f is the activation function(in this case the sigmoid function). The value y is the neuron's output.
![contentImage](https://api.sololearn.com/DownloadFile?id=4310)

note that this function can be generalized to have any number of inputs(xi) and thus the corresponding number of weights(wi).

### Activation Functions
There are three commonly used **activation functions**: **sigmoid**(from before), **tanh**, and **ReLU**.

**Tanh** has a similar form to sigmoid, though ranges from -1 to 1 instead of 0 to 1. Tanh is the hyperbolic tan function and is defined as follows:
![contentImage](https://api.sololearn.com/DownloadFile?id=4309)

The graph looks like this:
![contentImage](https://api.sololearn.com/DownloadFile?id=3951)

**ReLU** stands for Rectified Linear Unit. It is the identity function for positive numbers and sends negative numbers to 0.

Here's the equation and graph.
![contentImage](https://api.sololearn.com/DownloadFile?id=4100)
![contentImage](https://api.sololearn.com/DownloadFile?id=3952)

note that any of these activation functions will work well. Which one to use will depend on the specifics of the data. In practice, we figure out which one to use by comparing the performance of different neural networks.

### An Example
Assume we have a neuron that takes 2 inputs and produces 1 output and whose activation function is the **sigmoid**. The parameters are:

Weights (w1, w2) = \[0, 1\]
Bias (b) = 2

If we give the neuron input (1, 2) we get the following calculation.
![contentImage](https://api.sololearn.com/DownloadFile?id=4101)

The neuron yields an output of 0.9820.

Alternatively, if we give the neuron input (2, -2) we get the following calculation.
![contentImage](https://api.sololearn.com/DownloadFile?id=4102)

The neuron with this input yields an output of 0.5.

note that a neuron by itself doesn't have much power, but when we build a network of neurons, we can see how powerful they are together.