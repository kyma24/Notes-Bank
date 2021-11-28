![Multi-Layer Neural Networks with Sigmoid Function— Deep Learning for  Rookies (2) | by Nahua Kang | Towards Data Science](https://miro.medium.com/max/12840/1*v88ySSMr7JLaIBjwr4chTw.jpeg)
![Single Layer Perceptron in TensorFlow - Javatpoint](https://static.javatpoint.com/tutorial/tensorflow/images/single-layer-perceptron-in-tensorflow2.png)
![How to Create a Simple Neural Network in Python - KDnuggets](https://www.kdnuggets.com/wp-content/uploads/simple-neural-network.png)
![Feed-forward neural network with sigmoid activation function: X i (i... |  Download Scientific Diagram](https://www.researchgate.net/profile/Aleksandra-Vuckovic/publication/3978633/figure/fig2/AS:394699887136770@1471115194381/Feed-forward-neural-network-with-sigmoid-activation-function-X-i-i-1P-input.png)
what parameters should the network have to successfully capture any pattern in the neurons?

Add weights. take all of the activations from the first layer of the network and compute the weighted sum according to these weights.

if made the weights associated with almost all of the pixels zero except for positive weights in the section we care about, then taking the weighted sum of all the pixel values is equivalent to just adding up the values of the pixel just in the region we care abt.

if really want to pick up on if there is an edge in the region, could add some negative weights associated with the surrounding pixels, which means that the sum is largest when the middle pixels are bright, but the surrounding pixels are darker.

whenever computing a weighted sum, can come out with any number, but for this network what we want is for activations to be some value between 0 & 1, so a common thing to do is to pump the weighted sum into some function that squishes the real number line into the range btwn 0 & 1.
![Why is ReLu better than tanh and sigmoid function in artificial neural  networks? - Programmer Sought](https://programmersought.com/images/974/d43415b88a3e9cbc566c1ad341b18bd6.JPEG)

A common function that does this is called the sigmoid function, also known as a logistic curve.
![How the sigmoid function is used in AI - EDN](https://www.edn.com/wp-content/uploads/media-1311098-f1l.jpg)
$$
σ(x) = \frac{1}{1 + e^{-x}}
$$
Basically, very negative inputs end up close to zero and very positive inputs end up close to 1, and it just steadily increases around the input zero.

So, the activation of the neuron here is basically a measure of how positive the relevant weighted sum is.

But maybe it's not that you want the neuron to light up when the weighted sum is bigger than 0; maybe you only want it to be active when the sum is bigger than, say, 10. That is, you want some bias for it to be inactive, or **Bias for Inactivity**.

What we'll do then is just add in some other number, like negative ten, to this weighted sum before passing it into the sigmoid function. This additional number is called the **bias**.

The weights tell you what pixel pattern this neuron in the second layer is picking up on and the bias tells you how high the weighted sum needs to be before the neuron starts getting meaningfully active.

But that's just one neuron. Every single other neuron is going to be connected to the 28 x 28 = 784 neurons from the first layer and each one of those 784 connections has its own weight associated with it.

Also, each one has some bias, or some other number that you add on to the weighted sum before condensing it with the sigmoid.

All the layers also have a connection of weights and biases associated with it, which sums to about 13,000 total weights and biases for this neural network.

![[neural network layer.png]]

When talking abt learning, what that's referring to is getting the computer to find a valid setting for all of thes numbers so that it'll actually solve the problem at hand, or finding the right values to plug into the weights and biases.

the function:
$$
a_{0}^{(1)} = σ(w_{0.0} a_{0}^{(0)} + w_{0.1} a_{1}^{(0)} + ... + w_{0.n} a_{n}^{(0)} + b_{0})
$$
(the ${a_{n}^{(0)}}$ are the activations, the ${w_{0.n}}$ are the weights, σ is the sigmoid and ${b_{0}}$ is the bias)

is quite cumbersome to write down. There is a more notationally compact way that these connections are represented.

This is how it would be seen if you choose to read up more abt neural networks.

1. organize all of the activations from one layer into a column as a vector
2. then, organize all of the weights as a matrix where each row of that matrix corresponds to the connections between one layer and a particular neuron in the next layer.
		what that means is that taking the weighted sum of the activations in the first layer according to these weights corresponds to one of the terms in the matrix vector product of everything we have in the first layer(activations).
3. now, instead of adding the bias to each one of these values independently, we represent it by organizing all of those biases into a vector and adding the entire vector to the previous matrix-vector product. ![[distribute vector neural network.png]]
4. Now, for the final step, wrap a sigmoid around the outside of the matrix and vector expression. What this is supposed to represent is that you're going to apply the sigmoid function to each specific component of the resulting vector inside.

![[final neural network function.png]]



so once you write down this weight matrix and these vectors as their own symbols, you can communicate the full transition of activations from one layer to the next in an extremely tight and neat little expression.
$$
σ(Wa^{(0)} + b)
$$
This makes the relevant code both a lot simpler and a lot faster since many libraries optimize matrix multiplication.
![[ml code snippet.png]]

Neurons are things that hold numbers, but this depends on what type of image you feed it. A better description of a neuron is a **function**; it takes the outputs of all the neurons in the previous layer and spits out a number between 0 and 1. <- the neurons in this case contain the grayscale value, there are 2 hidden layers each with 16 neurons

Really, the entire network is just a function; one that takes in 784 numbers as an input and spits out 10 possible numbers as an output. It's an absurdly complicated function; one that involves thirteen thousand parameters in the forms of these weights and biases that pick up on certain patterns and which involves iterating many matrix-vector products and the sigmoid function.

[Python for Number Recognition](https://github.com/mnielsen/neural-networks-and-deep-learning)

[Online Book on Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com/)