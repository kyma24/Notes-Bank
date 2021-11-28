### Multi-Layer Perceptron
To create a **neural network** we combine neurons together so that the outputs of some neurons are inputs of other neurons. We will be working with **feed forward** neural networks which means that the neurons only send signals in one direction. In particular, we will be working with what is called a **Multi-Layer Perceptron(MLP)**. The neural network has multiple layers which we see depicted below.
![contentImage](https://api.sololearn.com/DownloadFile?id=3956)

A multi-layer perceptron will always have one **input layer**, with a neuron(or **node**) for each input. In the neural network above, there are two inputs and thus two input nodes. It will have one **output layer**, with a node for each output. Above there is 1 output node for a single output value. It can have any number of **hidden layers** and each hidden layer can have any number of nodes. Above there is one hidden layer with 5 nodes.

The nodes in the input layer take a single input value and pass it forward. The nodes in the hidden layers as well as the output layer can take multiple inputs but they always produce a single output. Sometimes the nodes need to pass their output to multiple nodes. In the example above, the nodes in the input layer pass their output to each of the five nodes in the hidden layer.


note that a **single-layer perceptron** is a neural network without any hidden layers. These are rarely used. Most neural networks are **multi-layer perceptrons**, generally with one or two hidden layers.

### Example Neural Network
Let's dive deeper into how this works with an example. A neural network that solves any real problem will be too large to interpret, so we will walk through a simple example.

We have a neural network with two inputs, a single hidden layer with two nodes and one output. The **weights** and **biases** are given in the nodes below. All the nodes use the sigmoid activation function.
![contentImage](https://api.sololearn.com/DownloadFile?id=3957)

Let's see what output we get for the input (3, 2).

Here is the output for the first node in the hidden layer.
![contentImage](https://api.sololearn.com/DownloadFile?id=4103)

Here is the output for the second node in the hidden layer.
![contentImage](https://api.sololearn.com/DownloadFile?id=4104)

Here is the output from the node in the output layer. Note that this node takes the outputs from the hidden layer as input.
![contentImage](https://api.sololearn.com/DownloadFile?id=4105)

Thus for the input (3, 2), the output of the neural network is 0.8680.

note that to change how the neural network performs, we can change the weights and bias values.

### More than 2 Target Values
A nice benefit of a MLP classifier is that it easily extends to problems that have **more than 2 target values**. In the beginning, have dealt with boolean possibilities. In some cases, we will be choosing among 3 or more possible outputs. A neural network does this naturally. We just need to add more nodes to the output layer. For example, if we are trying to predict if an image is a bird, cat or dog, we will have three output nodes. The first (y1) measures if the image is a bird, the second (y2) measures if the image is a cat, and the third (y3) measures if the image is a dog. The model chooses the output with the highest value.
![contentImage](https://api.sololearn.com/DownloadFile?id=3961)

For example, for a given image input, the neural net outputs y1 = 0.3, y2 = 0.2 and y3 = 0.5, the model would then determine the image has a dog (y3) in it.

note that we can use any classifier for a multi-class problem, but neural networks generalize naturally.