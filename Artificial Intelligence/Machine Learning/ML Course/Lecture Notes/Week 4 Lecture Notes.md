## ML: Neural Networks: Representation
## Non-linear Hypotheses
Performing linear regression with a complex set of data with many features is very unwieldy. Say you wanted to create a hypothesis from three(3) features that included all the quadratic terms:
$$
g(\theta_{0} + \theta_{1}x_{1}^{2} + \theta_{2}x_{1}x_{2} + \theta_{3}x_{1}x_{3} + \theta_{4}x_{2}^{2} + \theta_{5}x_{2}x_{3} + \theta_{6}x_{3}^{2})
$$

That gives us 6 features. The exact way to calculate how many features for all polynomial terms is the combination function with repitition: ${\frac{(n+r-1)!}{r!(n-1)!}}$. In this case we are taking all two-element combinations of three features: ${\frac{(3+2-1)!}{(2!\cdot (3-1)!)} = \frac{4!}{4} = 6}$.

For 100 features, if we wanted to make them quadratic we would get ${\frac{(100+2-1)!}{(2\cdot (100-1)!)} = 5050}$ resulting new features.

We can approximate the growth of the number of new features we get with all quadratic terms with ${\mathcal{O}(n^2/2)}$. And if you wanted to include all cubic terms in the hypothesis, the features would grow asymptotically at ${\mathcal{O}(n^{3})}$. There are very steep growths, so as the number of the features increase, the number of quadratic or cubic features increase very rapidly and becomes quickly impractical.

Example: let the training set be a collection of 50 x 50 pixel black-and-white photographs, and the goal will be to classify which are photos of cars. The feature set size is then n = 2500 if we compare every pair of pixels.

Now let's say we need to make a quadratic hypothesis function. With quadratic features the growth is ${\mathcal{O}(n^2/2)}$. So the total features will be around ${2500^{2}/2 = 3125000}$, which is very impractical.

Neural networks offer an alternative way to perform machine learning when we have complex hypotheses with many features.

## Neurons and the Brain
Neural networks are limited imitations of how the brain works. They have had a big recent resurgence because of advances in computer hardware.

There is evidence that the brain uses only one "learning algorithm" for all its different functions. Scientists have tried cutting(in an animal brain) the connection between the ears and the auditory cortex and rewiring the optical nerve with the auditory cortext to find that the auditory cortex literally learns to see.

This principle is called "neuroplasticity" and has many examples and experimental evidence.

## Model Representation I
Let's examine how we will represent a hypothesis function using neural networks.

At a very simple level, neurons are basically computational units that take input(**dendrites**) as electrical input(called "spikes") that are channeled to outputs(**axons**).

In the model, the dendrites are like the input features ${x_{1} ... x_{n}}$, and the output is the result of the hypothesis function:

In this model the x0 input node is sometimes called the "bias unit". It is always equal to 1.

In neural networks, we use the same logistic function as in classification: ${\frac{1}{1+e^{-\theta^{T}x}}$. In neural networks however, we sometimes call it a sigmoid(logistic) **activation** function.

The "theta" parameters are sometimes instead called "weights" in the neural networks model.

Visually, a simplistic representation looks like:
$$
[x_{0}x_{1}x_{2}] → [ ] → h_{\theta}(x)
$$

The input nodes(layer 1) go into another node(layer 2), and are outputted as the hypothesis function.

The first layer is called the "input layer" and the final layer the "output layer", which gives the final value computed on the hypothesis.

We can have intermediate layers of nodes between the input and output layers called the "hidden layer".

We label these intermediate or "hidden" layer nodes ${a_{0}^{2}...a_{n}^{2}}$ and call them "activation units."
$$
a_{i}^{(j)} = "activation"\hspace{0.2cm}of\hspace{0.2cm}unit\hspace{0.2cm}i\hspace{0.2cm}in\hspace{0.2cm}layer\hspace{0.2cm}j
$$
$$
Θ^{(j)} = matrix\hspace{0.2cm}of\hspace{0.2cm}weights\hspace{0.2cm}controlling\hspace{0.2cm}function\hspace{0.2cm}mapping\hspace{0.2cm}from\hspace{0.2cm}layer\hspace{0.2cm}j\hspace{0.2cm}to\hspace{0.2cm}layer\hspace{0.2cm}j + 1
$$

If we had one hidden layer, it would look visually something like:
$$
[x_{0}x_{1}x_{2}x_{3}] → [a_{1}^{(2)}a_{2}^{(2)}a_{3}^{(2)}] → h_{\theta}(x)
$$

The values for each of the "activation" nodes is obtained as follows:
$$
\hspace{2cm}a_{1}^{(2)} = g(Θ_{10}^{(1)}x_{0} + Θ_{11}^{(1)}x_{1} + Θ_{12}^{(1)}x_{2} + Θ_{13}^{(1)}x_{3})
$$
$$
\hspace{2cm}a_{2}^{(2)} = g(Θ_{20}^{(1)}x_{0} + Θ_{21}^{(1)}x_{1} + Θ_{22}^{(1)}x_{2} + Θ_{23}^{(1)}x_{3})
$$
$$
\hspace{2cm}a_{3}^{(2)} = g(Θ_{30}^{(1)}x_{0} + Θ_{31}^{(1)}x_{1} + Θ_{32}^{(1)}x_{2} + Θ_{33}^{(1)}x_{3})
$$
$$
h_{Θ}(x) = a_{1}^{(3)} = g(Θ_{10}^{(2)}a_{0}^{(2)} + Θ_{11}^{(2)}a_{1}^{(2)} + Θ_{12}^{(2)}a_{2}^{(2)} + Θ_{13}^{(2)}a_{3}^{(2)})
$$

This is saying that we compute the activation nodes by using a 3x4 matrix of parameters. We apply each row of the parameters to the inputs to obtain the value for one activation node. The hypothesis output is the logistic function applied to the sum of the values of the activation nodes, which have been multiplied by yet another parameter matrix ${Θ^{(2)}}$ containing the weights for the second layer of nodes.

Each layer gets its own matrix of weights, ${Θ^{(j)}}$.

The dimensions of these matrices of weights is determined as follows:
$$
If\hspace{0.2cm}network\hspace{0.2cm}has\hspace{0.2cm}s_{j}\hspace{0.2cm}units\hspace{0.2cm}in\hspace{0.2cm}layer\hspace{0.2cm}j\hspace{0.2cm}and\hspace{0.2cm}s_{j}+1\hspace{0.2cm}units\hspace{0.2cm}in\hspace{0.2cm}layer\hspace{0.2cm}j+1,\hspace{0.2cm}then\hspace{0.2cm}Θ^{(j)}\hspace{0.2cm}will\hspace{0.2cm}be\hspace{0.2cm}\hspace{0.2cm}dimension\hspace{0.2cm}s_{j}+1​×(s_{j}​+1).
$$

The +1 comes from the additoin in ${Θ^{(j)}}$ of the "bias nodes", x_{0} and ${Θ_{0}^{(j)}$. In other words, the output nodes won't include the bias nodes while the inputs will.

Example: layer 1 has 2 input nodes and layer 2 has 4 activation nodes. Dimension of ${Θ^{(1)}}$ is going to be 4x3 where ${s_{j} = 2}$ and ${s_{j+1} = 4}$, so ${s_{j+1}×(s_{j}+1) = 4 × 3}$

## Model Representaiton II
In this section we'll do a vectorized implementation of the above functions. We're going to define a new variable ${z_{k}^{(j)}}$ that encompasses the parameters inside the g function. In the previous example, if we replaced the variable z for all the parameters we would get:
$$
a_{1}^{(2)} = g(z_{1}^{(2)})
$$
$$
a_{2}^{(2)} = g(z_{2}^{(2)})
$$
$$
a_{3}^{(2)} = g(z_{3}^{(2)})
$$

In other words, for layer j=2 and node k, the variable z will be:
$$
z_{k}^{(2)} = Θ_{k,0}^{(1)}x_{0} + Θ_{k,1}^{(1)}x_{1} + ... + Θ_{k,n}^{(1)}x_{n}
$$

The vector representation of x and ${z^{j}}$ is:
$$
x = \begin{bmatrix}x_{0}\\x_{1}\\...\\x_{n}\end{bmatrix} z^{(j)} = \begin{bmatrix}z_{1}^{(j)}\\z_{2}^{(j)}\\...\\z_{n}^{(j)}\end{bmatrix}
$$

Setting ${x = a^{(1)}}$, we can rewrite the equation as:
$$
z^{(j)} = Θ^{(j-1)}a^{(j-1)}
$$

We are multiplying the matrix ${Θ^{(j-1)}}$ with dimensions ${s_{j} × (n+1)}$(where ${s_{j}}$ is the number of the activation nodes) by the vector ${a^{(j-1)}}$ with height (n+1). This gives us the vector ${z^{(j)}}$ with height ${s_{j}}$.

Now we can get a vector of the activation nodes for layer j as follows:
$$
a^{(j)} = g(z^{(j)})
$$

Where the function g can be applied element-wise to the vector ${z^{(j)}}$.

We can then add a bias unit(equal to 1) to layer j after we have computed ${a^{(j)}}$. This will be element ${a_{0}^{(j)}}$ and will be equal to 1.

To compute the final hypothesis, first compute another z vector:
$$
z^{(j+1)} = Θ^{(j)}a^{(j)}
$$

We get this final z vector by multiplying the next theta matrix after ${Θ^{(j-1)}}$ with the values of all the activation nodes we just got.

The last theta matrix ${Θ^{(j)}}$ will only have **one row** so that the result is a single number.

We then get the final result with:
$$
h_{Θ}(x) = a^{(j+1)} = g(z^{(j+1)})
$$

Notice that in this **last step**, between layer j and layer j+1, we are doing **exactly the same thing** as we did in logistic regression.

Adding all these intermediate layers in neural networks allows us to more elegantly produce interesing and more complex non-linear hypotheses.

## Examples and Intuitions I
A simple example of applying neural networks is by predicting ${x_{1}}$ AND ${x_{2}}$, which is the logical 'and' operator and is only true if both ${x_{1}}$ and ${x_{2}}$ are 1.

The graph of the functions will look like:
$$
\begin{bmatrix}x_{0}\\x_{1}\\x_{2}\end{bmatrix} → [g(z^{(2)})] → h_{Θ}(x)
$$

Remember that ${x_{0}}$ is the bias variable and is always 1.

Let's set the first theta matrix as:
$$
Θ^{(1)} = [-30\hspace{0.3cm}20\hspace{0.3cm}20]
$$

This will cause the output of the hypothesis to only be positive if both ${x_{1}}$ and ${x_{2}}$ are 1. In other words:
$$
h_{Θ}(x) = g(-30 + 20x_{1} + 20x_{2})
$$
$$

$$
$$
x_{1} = 0\hspace{0.2cm}and\hspace{0.2cm}x_{2} = 0\hspace{0.2cm}then\hspace{0.2cm}g(-30) ≈ 0
$$
$$
x_{1} = 0\hspace{0.2cm}and\hspace{0.2cm}x_{2} = 1\hspace{0.2cm}then\hspace{0.2cm}g(-10)≈0
$$
$$
x_{1} = 1\hspace{0.2cm}and\hspace{0.2cm}x_{2} = 0\hspace{0.2cm}then\hspace{0.2cm}g(-10) ≈ 0
$$
$$
x_{1} = 1\hspace{0.2cm}and\hspace{0.2cm}x_{2} = 1\hspace{0.2cm}then\hspace{0.2cm}g(10)≈1
$$

So we have constructed one of the fundamental operations in computers by using a small neural network rather than an actual AND gate. Neural networks can also be used to simulate all the other logic gates.

## Examples and Intuitions II
The ${Θ(1)}$ matrices for AND, NOR, and OR are:
$$
AND:
$$
$$
Θ^{(1)} = [-30\hspace{0.3cm}20\hspace{0.3cm}20]
$$
$$
NOR:
$$
$$
Θ^{(1)} = [10\hspace{0.3cm}-20\hspace{0.3cm}-20]
$$
$$
OR:
$$
$$
Θ^{(1)} = [-10\hspace{0.3cm}20\hspace{0.3cm}20]
$$

We can combine these to get the XNOR logical operator(which gives 1 if ${x_{1}}$ and ${x_{2}}$ are both 0 or both 1).
$$
\begin{bmatrix}x_{0}\\x_{1}\\x_{2}\end{bmatrix} → \begin{bmatrix}a_{1}^{(2)}\\a_{2}^{(2)}\end{bmatrix} → [a^{(3)}] → h_{Θ}(x)
$$

For the transition between the first and second layer, we'll use a ${Θ(1)}$ matrix that combines the values for AND and NOR:
$$
Θ^{(1)} = [-30\hspace{0.3cm}20\hspace{0.3cm}2010\hspace{0.3cm}-20\hspace{0.3cm}-20]
$$

For the trainsition between the second and third layer, we'll use a ${Θ(2)}$ matrix that uses the value for OR:
$$
Θ^{(2)} = [-10\hspace{0.3cm}20\hspace{0.3cm}20]
$$

Let's write out the values for all the nodes:
$$
a^{(2)} = g(Θ^{(1)}\cdot x)
$$
$$
a^{(3)} = g(Θ^{(2)}\cdot a^{(2)})
$$
$$
h_{Θ}(x) = a^{(3)}
$$

And there we have the XNOR operator using two hidden layers.

## Multiclass Classification
To classify data into multiple classes, we let the hypothesis function return a vector of values. Say we wanted to classify the data into one of the four final resulting classes:
$$
\begin{bmatrix}x_{0}\\x_{1}\\x_{2}\\...\\x_{n}\end{bmatrix} → \begin{bmatrix}a_{0}^{(2)}\\a_{1}^{(2)}\\a_{2}^{(2)}\\...\end{bmatrix} → \begin{bmatrix}a_{0}^{(3)}\\a_{1}^{(3)}\\a_{2}^{(3)}\\...\end{bmatrix} → ... → \begin{bmatrix}h_{Θ}(x)_{1}\\h_{Θ}(x)_{2}\\h_{Θ}(x)_{3}\\h_{Θ}(x)_{4}\end{bmatrix}
$$

The final layer of nodes, when multiplied by the theta matrix, will result in another vector, on which we will apply the g() logistic function to get a vector of hypothesis values.

The resulting hypothesis for one set of inputs may look like:
$$
h_{Θ}(x) = [0010]
$$

In which case the resulting class is the third one down, or ${h_{Θ}(x)_{3}}$.

We can define the set of resulting classes as y:
$$
y^{(i)} = \begin{bmatrix}1\\0\\0\\0\end{bmatrix}, \begin{bmatrix}0\\1\\0\\0\end{bmatrix}, \begin{bmatrix}0\\0\\1\\0\end{bmatrix}, \begin{bmatrix}0\\0\\0\\1\end{bmatrix},
$$

The final value of the hypothesis for a set of inputs will be one of the elements in y.