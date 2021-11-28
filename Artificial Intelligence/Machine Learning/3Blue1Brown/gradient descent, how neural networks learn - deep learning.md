what we want is an algorithm where you can show the network a whole bunch of training data which comes in the form of different images of handwritten digits along with labels for what they're supposed to be, and it'll adjust those 13000 weights and biases so as to improve its performance on the training data.

basically, separate all data into training data and testing data, and see how accurately the network classifies those testing images.

remember conceptually that we're thinking of each neuron as being connected to all of the neurons in the previous layer and the weights in the weighted sum defining its activation are kind of like the strengths of those connections, and the bias is some indication of whether that neuron tends to be active or inactive.

### Cost Functions

To start things off, we're just going to initialize all of those weights and biases totally randomly. Needless to say, this network is going to perform horribly on a given training example since it's just doing something random.

For example, you feed in an image of a 3 and the output layer looks like a mess.

What you do is you define a cost function, which is a way of telling the computer that the answer is wrong by adding up the squares of the differences between each of the bad output activations and the value that you want them to have.

$$
(0.43 - 0.00)^2 +
$$
$$
(0.28 - 0.00)^2 +
$$
$$
(0.19 - 0.00)^2 +
$$
$$
(0.88 - 0.00)^2 +
$$
$$
(0.72 - 0.00)^2 +
$$
$$
(0.01 - 0.00)^2 +
$$
$$
(0.64 - 0.00)^2 +
$$
$$
(0.86 - 0.00)^2 +
$$
$$
(0.99 - 0.00)^2 +
$$
$$
(0.63 - 0.00)^2
$$

This is what's called the cost of a single training example. Notice that the sum is small when the network confidently classifies the image correctly, but it's large when the network seems like it doesn't know what it's doing.

So then what you do is consider the average cost over all of the tens of thousands of training examples at your disposal. This average cost is the measure for how bad the network is, and that would be complicated.

Input: 784 numbers (pixels)
Output: 10 numbers
Parameters: 13,002 weights/biases

the cost function is a layer of complexity on top of that. it takes as its input those 13,000 weights and biases and spits out a single number describing how bad those weights and biases are. And the way it's defined depends on the network's behavior over all the tens of thousands of pieces of training data.

Input: 13,002 weights/biases
Output: 1 number(the cost)
Parameters: lots of training examples

we want to tell the function how to do better and how to optimize the weights and biases. 

$$
C(w_{1}, w_{2}, ..., w_{13002})
$$

to make it easier, rather than struggling to imagine a function with 13,000 inputs, just imagine a simple function that has one number as an input and one number as an output.

$$
C(w)
$$

now, how do you find an input that minimizes the value of this function?

calculus students will know that you can sometimes figure out that minimum explicitly:

$$
\frac{dC}{dw}(w) = 0
$$

but for complicated cases, it's sometimes infeasible, especially in the 13000 input version for the neural network cost function.

a more flexible tactic is to start at any input and figure out which direction you should step to make that output lower.

Specifically, if you can figure out the slope of the function where you are, then shift to the left if that slope is positive...
![[positive slope.png]]
... and shift the input to the right if that slope is negative
![[negative slope.png]]

if you keep doing this process, it will eventually approach the lowest point. It can be visualized as a ball rolling down a hill.

notice that even for this really simplified single input function, there are many possible valleys that you might land in, depending on which random input you start at. There's no guarantee that the local minimum you land in is going to be the smallest possible value of the cost function.

that's going to carry over to the neural network case as well, so notice how if you make the step sizes proportional to the slope, then when the slope is flattening out towards the minimum, your steps get smaller and smaller and that kind of helps you from overshooting.

### Gradient Descent
![Visualizing the gradient descent method](https://scipython.com/static/media/uploads/blog/linreg-graddesc/linreg1d.png)
![An Easy Guide to Gradient Descent in Machine Learning](https://d1m75rqqgidzqn.cloudfront.net/wp-data/2020/06/12190927/8.png)
bumping up the complexity a bit, imagine instead a function with two inputs and one output. you might think of the input space as the xy plane and the cost function as being graphed as a surface above it.

![Gradient Descent: All You Need to Know | Hacker Noon](https://hackernoon.com/hn-images/1*f9a162GhpMbiTVTAua_lLQ.png)

now, instead of asking abt the slope of the function, you have to ask which direction should you step in this input space so as to decrease the output of the function most quickly. In other words, what's the downhill direction?

![The outline of Gradient Descent](https://suniljangirblog.files.wordpress.com/2018/12/1-1.gif?w=379)

in multivariable calculus, the "**Gradient**" of a function gives you the direction of steepest ascent/increase. Basically, which direction should you step to increase the function most quickly.

$$
\nabla C(x, y)
$$

naturally enough, taking the negative of that gradient gives you the direction to step that decreases the function most quickly.

even more than that, the length of the gradient vector is actually an indication for just how steep that steepest slope is.

It's the same basic idea for a function that has 13,000 inputs instead of two inputs.

Imagine organizing all 13,000 weights and biases of the network into a giant column vector.

$$
\begin{align}
    \overrightarrow{W} = \begin{bmatrix}
           2.25 \\
           -1.57 \\
		   1.98 \\
           \vdots \\
           -1.16 \\
		   3.82 \\
		   1.21
         \end{bmatrix} \hspace{2cm}
    -\nabla C \overrightarrow{W} = \begin{bmatrix}
           0.18 \\
           0.45 \\
		   -0.51\\
           \vdots \\
           0.40 \\
		   -0.32 \\
		   0.82
         \end{bmatrix}
  \end{align}
 $$
first vector: 13,002 weights & biases
second vector: How to nudge all weights and biases

The negative gradient of the cost function is just a vector. It's some direction inside this insanely huge input space that tells you which nudges to all of those numbers is going to cause the most rapid decrease to the cost function.

And of course, with the specially designed cost function before, changing the weights and biases to decrease it means making the output of the network on each piece of training data look less like a random array of ten values and more like an actual decision that we want it to make.

It's important to remember that this cost function involves an average over all of the training data. So if you minimize it, it means it's a better performance on all of those samples.


the algorithm for computing this gradient efficiently, which is effectively the heart of how a neural network learns, is called **back propagation**.

What we mean when we talk about a network learning is that it's just minimizing a cost function. And notice: one consequence of that is that it's important for this cost function to have a nice, smooth output so that we can find the local minimum by taking little steps downhill.

This is why artificial neurons have continuously ranging activations, rather than simply being active or inactive in a binary way, the way that biological neurons are.

this process of repeatedly nudging an input of a function by some multiple of the negative gradient is called **gradient descent**. It's a way to converge towards some local minimum of a cost function; basically a valley in a graph like this:
![How do ML Models actually do Gradient Descent? | by Mukundh Murthy | The  Startup | Medium](https://miro.medium.com/max/3374/1*6R4eCrQZIWFx_oUgmGPGow.png)

this is for two inputs, of course, bc nudges in a thirteen thousand dimensional input are a little(no, really) hard to understand, but there is actually a non-spatial way to think about this.

$$
\begin{align}
    \overrightarrow{W} = \begin{bmatrix}
           w_{0} \\
           w_{1} \\
		   w_{2} \\
           \vdots \\
           w_{13,000} \\
		   w_{13,001} \\
		   w_{13,002}
         \end{bmatrix}
  \end{align}
		 $$
$$
	\begin{align}
    \nabla C (\overrightarrow{W}) = \begin{bmatrix}
           0.31 \\
           0.03 \\
		   -1.25\\
           \vdots \\
           0.78 \\
		   -0.37 \\
		   0.16
         \end{bmatrix}
  \end{align}
 $$

each component of the negative gradient tells us two things:
1. the sign, of course, tells us whether the corresponding component of the input vector should be nudged up or down,...
2. ... but more importantly the relative magnitudes of all these components kind of tells you which changes matter more.

i.e. in the network, an adjustment to one of the weights might have a much greater impact on the cost function than some other weight. some of these connections just matter more for the training data.

so a way that you can think abt this gradient vector of the mind-warpingly massive cost function is that it encodes the relative importance of each weight and bias; that is, which of these changes is going to have the most impact.

$$
C(x, y) = \frac{3}{2} x^2 + \frac{1}{2} y^2
$$
$$
\begin{align}
    -\nabla C (1, 1) = \begin{bmatrix}
           3 \\
		   1
         \end{bmatrix}
  \end{align}
$$

then again, this is just another way to be thinking abt direction. to take a simpler example, if you have some function with two variables as an input and you compute that its gradient at some particular point comes out as (3, 1); then on the one hand you can interpret that as saying that when you're standing at that input, moving along this direction increases the function most quickly(direction of steepest ascent).

That when you graph the function above the plane of input points, that vector is what's giving you te straight uphill direction.

But another way to read that is to say that changes to the first variable(in the function case, ${\frac{3}{2}x^2}$) have three times the importance as changes to the second variable(${\frac{1}{2}y^2}$); that, at least in the neighborhood of the relevant input, nudging the x value yields more benefits.


### Analyzing the Network
before, hoped that the network would have the first hidden layer recognize stroke patterns, then piece it together into loops and longer lines in the second hidden layer, then pieced together to recognize digits as the output.

actually, this isn't what this particular network does at all.

remember that the weights of the connections from all of the neurons in the first layer to a given neuron in the second layer can be visualized as a given pixel pattern that the second layer neuron is picking up on.

when we do that for the weights associated with these transitions from the first layer to the next, instead of picking up on isolated little edges here and there, they look (almost) random; just put some very loose patterns in the middle there.

it would seem that in the unfathomably large 13,000 dimensional space of possible weights and biases, our network found itself a happy little local minimum that, despite successfully classifying most images, doesn't exactly pick up on the patterns that we might have hoped for.

![[what second layer neutrons look for.png]]

and even worse is when you input a random image into the neural network. If the system was smart, you might expect it to either feel uncertain maybe; not really activating any of those 10 output neurons or activating them all evenly.

But instead, it confidently gives you some nonsense answer as if it feels as sure that this random noise is a 5 as it does that an actual image of a 5 is a 5. Phrased differently, even if this network can recognize digits pretty well, it has no idea how to draw them.

A lot of this is because it's such a tightly constrained training setup. Put yourself in the network's shoes here from its point of view. The entire universe consists of nothing but clearly defined unmoving digits centered in a tiny grid; and its cost function just never gave it any incentive to be anything but utterly confident in its decisions.

So, the splitting the numbers and piecing them together strategy isn't meant to be the end goal, but instead, a starting point. 

Frankly, this is old technology, called "Multilayer perceptron"; the kind researched in the 80s and 90s. However, you do need to understand it before you can understand more detailed modern variants(i.e. Convolutional NN), and it clearly is capable of solving some interesting problems.

### More Info
A paper took one of these particularly deep neural networks that's really good at image recognition and instead of training it on a properly labeled dataset, it shuffled all of the labels around before training.

Obviously, the testing accuracy here was going to be no better than random since everything's just randomly labeled, but it was still able to achieve the same *training* accuracy as you would on a properly labeled dataset.

Basically, the millions of weights for this particular network were enough for it to just memorize the random data, which kind of raises the question for whether minimizing this cost function actually corresponds to any sort of structure in the image?

[The First Paper](https://arxiv.org/abs/1611.03530)
[A Closer Look at Memorization in Deep Networks](https://arxiv.org/abs/1706.05394)

It memorizes the entire dataset of what the correct classification is and so half a year later, at ICML 2017, there was not exactly a rebuttal; paper that addressed some aspects of "Actually, these networks are doing something a little bit smarter than that." If you look at the accuracy curve, if you were just training on a random data set, its curve sort of went down very slowly in almost a linear fashion; so you're really struggling to find that local minima of the right weights that would get you that accuracy, whereas if you're actually training on a structured dataset, one that has the right labels, you fiddle around a bit in the beginning, but then you kind of dropped very fast to get to that accuracy level. 

And so in some sense it was easier to find that local maxima and so what was also interesting about that is that it brings into light [another paper](https://arxiv.org/abs/1412.0233) from another few years ago, which has a lot more simplifications abt the network layers, but one of the results was saying how if you look at the optimization landscape, the local minima that these networks tend to learn are actually of (roughly) equal quality.

So, in some sense if your dataset is structured, you should be able to find that much more easily.