# Basics of Backpropogation
![Backpropagation - Wikipedia](https://upload.wikimedia.org/wikipedia/commons/0/00/Multi-Layer_Neural_Network-Vector-Blank.svg)
One thing to keep in mind from before is:

since visualizing the direction in a 13,000 dimension gradient vector is practically impossible, there is a different way to express it;
the magnitude of each component here is telling you how sensitive the cost function is to each weight and bias.

i.e. let's say you go through the process and you compute the negative gradient, and the component associated with the weight on on one edge comes out to be 3.2, while the component associated with another edge comes out as 0.1.

The way this would be interpreted is that the cost of the 3.2-yielding function is 32 times more sensitive to changes in that first weight. So if that value would be nudged just a bit, it's going to cause some change to the cost, and the said change is 32 times greater than what the same nudge to the second weight would give.


### Intuitive Walkthrough example
Because the cost function involves averaging a certain cost per example over all the tens of thousands of training examples, the way that we adjust the weights and biases for a single gradient descent step also depends on every single example...

..., or rather, in principle, it should, but for computational effeciency there will be a little trick later on to keep you from needing to hid every single example for every single step.


For now, let's focus all of our attention onto one single case: an image of a 2. What effect should this one training example have on how the weights and biases get adjusted?

Let's say that we're at a point where the network isn't well trained yet, so the activations in the output are going to look pretty random.

Now, we can't directly change those activations; we only have influences on the weights and biases. But it is helpful to keep track of which adjustments we wish should take place to that output layer.

And since we want the network to classify the image as a 2, we want that third value(2) to get nudged up, while all of the others get nudged down.

Moreover, the sizes of these nudges should be proportional to how far away each current value is from its target value.

For example, the increase to that number 2 neuron's activation is, in a sense, more important than the decrease to the number 8 neuron, which could already be pretty close to where it should be.


So, zooming in *further*, let's just focus on this one neuron, the one whose activation we wish to increase.

(assume the 2 neuron has a value of 0.2)

remember, that activation is defined as a certain **weighted-sum** of all of the activations in the previous layer, plus a bias, which is all then plugged into either a sigmoid function, or a ReLU.

$$
0.2 = σ(w_{0}a_{0} + w_{1}a_{1} + ... + w_{n-1}a_{n-1} + b)
$$

so, there are three different avenues that can team up together to help increase the activation:

you can increase the bias, you can increase the weights, and you can **change** the activations from the previous layer.

Focusing just on how the *weights* should be adjusted, notice how the weights actually have differing levels of influence:

The connections from with the brightest neurons from the preceding layer have the biggest effect, since those weights are multiplied by larger activation values.

So, if you were to increase one of those weights, it actually has a stronger influence on the ultimate cost function than increasing the weights of connections with dimmer neurons(at least as far as this one training example is concerned).

Remember when we talked abt gradient descent; we don't just care abt whether each component should get nudged up or down, we care abt which ones have the most benefit to the network's accuracy.

This is at least somewhat reminiscent of a theory in neuroscience, for how biological networks of neurons learn: the Hebbian theory - often summed up in the phrase "neurons that fire together wire together."

Here, the biggest increase to weights, the biggest strengthening of connections, happens between neurons which are the most active, and the ones which we wish to become more active.

In a sense, the neurons that are firing while seeing a 2(piecing together patterns), get more strongly linked to those firing when thinking abt a 2(the output).


The third way we can help increase this neuron's activation is by changing all the activations in the previous layer; namely, if everything connected to that digit 2 neuron with a positive weight got brighter, and if anything connected with a negative weight got dimmer, then that digit two neuron would become more active. And, similar to the weight changes, you're going to get the most benefit out of that by **seeking changes that are proportional to the size of the corresponding weights**.

Now, of course, we can't directly influence those activations; we only have control over the weights and biases. But just as with the last layer, it's helpful to just keep note of what those desired changes are.

But keep in mind; zooming out one step here, this is only what that digit 2 output neuron wants. Remember, we also want all of the other neurons in the last layer to become less active, and each of those other output neurons has its own thoughts about what should happen to that second-to-last layer.

So, the **desire of this digit 2** neuron is added together with the desires of **all the other output neurons** for what should happen to this second-to-last layer.

Again, in proportion to the corresponding weights, and in proportion to how much each of those neurons need to change.

This is where the idea of **propogating backwards** comes in.

By adding together all of these desired effects, you basically get a list of nudges that you want to happen to the second-to-last layer.

Now, once you have those, you can recursively apply the same process to the relevant weights and biases that determine those values, repeating the same process that was walked through and moving backwards through the network.


And zooming out a bit further, remember that this is all just how a *single training example* wishes to nudge each one of those weights and biases. If we only listen to what that 2 wanted, the network would ultimately be incentivized just to classify all images as a 2.

So what you do is go through the same backprop routine for every other training example, recording how each of them would like to change the weights and the biases, and you **average** together those desired changes.

The resulting collection of the averaged nudges to each weight and bias is, loosely speaking, the negative gradient of the cost function referenced before, or at least something proportional to it.
$$
\begin{align}
    -\nabla C (w_{1}, w_{2}, ... w_{13,001}) = \begin{bmatrix}
           -0.08 \\
           0.12 \\
		   -0.06\\
           \vdots \\
           0.04
         \end{bmatrix}
  \end{align}
$$

"Loosely speaking" is only used because we have yet to get quantitively precise about those nudges.

### Stochastic Gradient Descent
By practice, it takes computers an extremely long time to add up the influence of every single training example, every single gradient descent step. So, here's what's commonly done instead:

1. You randomly shuffle your training data, and then divide it into mini-batches; let's say, each one having 100 training examples.
2. Then, you compute a (gradient descent) step according to the mini-batch. <- using backprop
		This isn't going to be the actual gradient of the cost function, which depends on all of the training data, not this tiny subset; so it's not the most efficient step.
3. Even though it isn't entirely efficient, it does speed up the program and gives you a pretty good approx.

If this were to be plotted, the trajectory of the network under the relevant cost surface, it would be a little more like a drunk man stumbling aimlessly down a hill, but taking quick steps, rather than a carefully calculated man determining the exact downhill direction of each step, before taking a very slow and exact step down.

This technique is referred to as "stochastic gradient descent".


Review:
Backpropogation is the algorithm for determining how a single training example would like to nudge the weights and biases, not just in terms of whether to go up or down, but in terms of what relative proportions to those changes cause the most rapid decrease to the cost.

A true gradient descent step would involve using all the datasets and average all the desired changes. But that's computationally slow; so we split the data into mini-batch and do the process repeatedly going through all of the mini-batches and making these adjustments. You will converge towards a local minimum of the cost function; which is to say, the network will end up doing a really good job on the training examples.

So with that said, every line of code that would go into implementing **backprop** actually corresponds with something that you have now seen, at least in informal terms.



# Backpropogation Calculus
start off with an extremely simple network: one where each layer has a single neuron in it, and there are 4 layers.

this particular network is determined by 3 weights and 3 biases, and the goal is to understand how sensitive the cost function is to these variables.
$$
C(w_{1}, b_{1}, w_{2}, b_{2}, w_{3}, b_{3})
$$

That way, we known which adjustments to these terms is going to cause the most efficient *decrease* to the cost function.

We're going to focus on the connection btwn the last two neurons. Let's label the activation of that last neuron a with a superscript L(${a^{(L)}}$) indicating which layer it's in; so the activation of this previous neuron is ${a^{(L - 1)}}$(not exponents, just a way of indexing what we're talking abt, since subscripts are saved for different indices later on).

Let's say that the value we want this last activation to be for a given training example is ${y}$; i.e. it might be 0, or 1.

So, the cost of this simple network for a single training example is:
$$
C_{0}(...) = (a^{(L)} - y)^2
$$

note that ${C_{0}}$ is cost
i.e. ${(0.66 - 1.00)^2}$

as a reminder, this last activation is determined by a weight, which is going to be called ${w^{(L)}}$ and bias ${b^{(L)}}$:
$$
a^{(L)} = w^{(L)}a^{(L - 1)} + b^{(L)}
$$

after this, you pump it through some special nonlinear function such as the sigmoid or a ReLU.

$$
a^{(L)} = σ(w^{(L)}a^{(L - 1)} + b^{(L)})
$$

It's going to make things easier for us if we give a special name to this weighted sum, like z, with the same superscript as the relevant activations:
$$
z^{(L)} = w^{(L)}a^{(L - 1)} + b^{(L)}
$$
$$
a^{(L)} = σ(z^{(L)})
$$

So there are a lot of terms, and a way you might conceptualize this is that the weight, the previous activation, and the bias, all together are used to compute z, which in turn lets us compute a, which finally, along with the constant y, lets us compute the cost.

[![](https://mermaid.ink/img/eyJjb2RlIjoiZ3JhcGggVERcbiAgICBBW3deTF0gLS0-RChHbyBzaG9wcGluZylcbiAgICBCW2FeTC0xXSAtLT4gRHtMZXQgbWUgdGhpbmt9XG4gICAgQ1tiXkxdIC0tPkRbel5MXVxuICAgIEQgLS0-RVthXkxdXG4gICAgRSAtLT5HW0Nvc3RdXG4gICAgRlt5XSAtLT5HIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRlZmF1bHQifSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)](https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoiZ3JhcGggVERcbiAgICBBW3deTF0gLS0-RChHbyBzaG9wcGluZylcbiAgICBCW2FeTC0xXSAtLT4gRHtMZXQgbWUgdGhpbmt9XG4gICAgQ1tiXkxdIC0tPkRbel5MXVxuICAgIEQgLS0-RVthXkxdXG4gICAgRSAtLT5HW0Nvc3RdXG4gICAgRlt5XSAtLT5HIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRlZmF1bHQifSwidXBkYXRlRWRpdG9yIjpmYWxzZX0)

And of course, ${a^{(L - 1)}}$ is influenced by its own weight and bias, and such - but we're not going to focus on that right now.

Now, all of these are just numbers. And it can be nice to think of each one as having its own little number line. 

Our first goal is to understand how sensitive the cost function is to small changes in the weight function ${w^{(L)}}$. (${∂w^{(L)}}$) Or phrased differently, what is the **derivative** of ${C}$ with respect to ${w^{(L)}}$:
$$
\frac{∂C_{0}}{∂w^{(L)}}
$$

when you see this "**∂w**" term, think of it as meaning "some tiny nudge to w", like a change by 0.01. And think of this "**∂C**" term as meaning "whatever the resulting nudge to the cost is".
What we want is their ratio. 

Conceptually, this tiny nudge to ${w^{(L)}}$ causes some nudge to ${z^{(L)}}$(${∂z^{(L)}}$), which in turn causes some change to ${a^{(L)}}$(${∂a^{(L)}}$), which directly influences the cost(${∂C_{0}}$).
![[the chain rule.png]]
(note that ${a^{(L-1)}}$ is the second layer neuron, ${a^{(L)}}$ is the third layer neuron, and ${y}$ is the output)

So we break things up by first looking at the ratio of a tiny change to ${z^{(L)}}$ to the tiny change in ${w^{(L)}}$; that is, the derivative of ${z^{(L)}}$  with respect to ${w^{(L)}}$:
$$
\frac{∂C_{0}}{∂w^{(L)}} = \frac{∂z^{(L)}}{∂w^{(L)}}
$$

Likewise, you then consider the ratio of a change to ${a^{(L)}}$ to the tiny change in ${z^{(L)}}$ that caused it, as well as the ratio between the final nudge to ${C}$ and this intermediate nudge to ${a^{(L)}}$.
$$
\frac{∂C_{0}}{∂w^{(L)}} = \frac{∂z^{(L)}}{∂w^{(L)}} \frac{{∂a^{(L)}}}{∂z^{(L)}} \frac{∂C_{0}}{∂a^{(L)}}
$$

This right here is the **chain rule**, where multiplying together these three ratios gives us the sensitivity of ${C}$ to small changes in ${w^{(L)}}$.

### Computing Relevant Derivatives
the derivative of ${C}$ with respect to ${∂a^{(L)}}$ works out to be ${2(a^{(L)} - y)}$ based on the original cost equation ${C_{0} = (a^{(L)} - y)^2}$.

$$
\frac{∂C_{0}}{∂a^{(L)}} = 2(a^{(L)} - y)
$$

Notice, this means that its size is proportional to the difference between the network's output, and the thing we want it to be. So if that output was very different, even slight changes stand to have a big impact on the cost function.

The derivative of ${a^{(L)}}$ with respect to ${z^{(L)}}$ is just the derivative of the sigmoid function(${a^{(L)} = σ(z^{(L)})}$), or whatever nonlinearity you choose to use.
$$
\frac{{∂a^{(L)}}}{∂z^{(L)}} = σ'(z^{(L)})
$$

And the derivative of ${z^{(L)}}$ with respect to ${w^{(L)}}$ in this case comes out just to be ${a^{(L - 1)}}$ based on the equation ${z^{(L)} = w^{(L)}a^{(L - 1)} + b^{(L)}}$:

$$
\frac{∂z^{(L)}}{∂w^{(L)}} = a^{(L-1)}
$$

### What do Derivatives Mean?
In the case of the last derivative, the amount that a small nudge to this weight influences the last layer depends on how strong the previous neuron is(${a^{(L)}}$'s previous neuron is ${a^{(L-1)}}$, and the weight connection between them is ${∂w^{(L)}}$).

Remember, there is where that "neurons that fire together wire together" idea comes in. And all of this is the derivative with respect to ${w^{(L)}}$ only of the cost for a specific training example.

Since the full cost function involves averaging together all those costs across many training examples, its derivative requires averaging this expression over all training examples.
$$
\frac{∂C}{∂w^{(L)}} = \frac{1}{n}\sum\limits_{k=0}^{n-1}\frac{∂C_{k}}{∂w^{(L)}}
$$

And of course, that is just one component of the gradient vector, which itself is built up from the partial derivatives of the cost function with respect to all those weights and biases.

$$
\begin{align}
    \nabla C = \begin{bmatrix}
           \frac{∂C}{∂w^{(1)}} \\
           \frac{∂C}{∂b^{(1)}}\\
           \vdots \\
           \frac{∂C}{∂w^{(L)}}\\
		   \frac{∂C}{∂b^{(L)}}
         \end{bmatrix}
  \end{align}
$$

### Sensitivity to Weights/Biases
But even though it was just one of those partial derivatives we need, it's more than 50% of the work. The sensitivity to the bias, for example, is almost identical. we just need to change out the ${\frac{∂z^{(L)}}{∂w^{(L)}}}$ term for a ${\frac{∂z^{(L)}}{∂b^{(L)}}}$ .

And if you look at the relevant formula ${z^{(L)} = w^{(L)}a^{(L - 1)} + b^{(L)}}$, the derivative comes out to be 1:
$$
\frac{∂C_{0}}{∂b^{(L)}} = 1 * \frac{{∂a^{(L)}}}{∂z^{(L)}} \frac{∂C_{0}}{∂a^{(L)}} = 1 * σ'(z^{(L)})2(a^{(L)}-y)
$$

Also, this is where the idea of propagating backwards comes in:

you can see how sensitive the cost function is to the activation of the previous layer;

namely, this initial derivative in the chain rule expession, the sensitivity of z to the previous activation, comes out to be the weight ${w^{(L)}}$:
$$
\frac{∂C_{0}}{∂a^{(L-1)}} = \frac{∂z^{(L)}}{∂a^{(L - 1)}} \frac{{∂a^{(L)}}}{∂z^{(L)}} \frac{∂C_{0}}{∂a^{(L)}} = w^{(L)} σ'(z^{(L)})2(a^{(L)}-y)
$$

And again, even though we won't be able to directly influence that activation, it's helpful to keep track of bc now we can just keep iterating this chain rule idea backwards to see how sensitive the cost function is to previous weights and to previous biases.

### Layers With Additional Neurons
Though it may seem complicated, the overly simplified example above wouldn't be that different from the real deal with more neurons; just more indices to keep track of.

Rather than the activation of a given layer simply being ${a^{(L)}}$, it's also going to have a subscript indicating which neuron of that layer it is.
${a_{0}^{(L-1)}}$

${a_{0}^{(L)}}$

${a_{1}^{(L-1)}}$

${a_{1}^{(L)}}$

${a_{2}^{(L-1)}}$

i.e.
![The Math behind Neural Networks - Forward Propagation | Jason {osa-jima}](https://www.jasonosajima.com/images/nn_3.png)
![Forward Propagation – Learning with Machines](https://learningwithmachines.files.wordpress.com/2020/10/neural-net-lablled-2.png?w=1024)
![Neural networks: training with backpropagation.](https://www.jeremyjordan.me/content/images/2017/07/Screen-Shot-2017-07-17-at-11.13.18-AM.png)

let's go ahead and use the letter ${k}$ to index the layer ${(L-1)}$, and ${j}$ to index the layer ${(L)}$.

${a_{k}^{(L-1)}}$

${a_{j}^{(L)}}$

For the cost, again we look at what the desired output is, i.e. ${0.00}$ for ${y_{0}}$ and ${1.00}$ for ${y_{1}}$; but this time, we add up the squares of the differences between the last layer activations and the desired output:
$$
C_{0} = \sum\limits_{j=0}^{n_{L}-1} (a_{j}^{(L)} - y_{j})^2
$$

That is, you take a sum over ${(a_{j}^{(L)} - y_{j})^2}$.

Since there's a lot more weights, each one has to have a couple more indices to keep track of where it is.

So let's call the weight of the edge connecting the ${k}$th neuron to the ${j}$th neuron ${w_{jk}^{L}}$

Those indices might feel a little backwards at first, but it lines up with how you'd index the weight matrix that was talked about before:
$$
\begin{align}
    \begin{bmatrix}
           w_{0.0} & w_{0.1} & ... & w_{0.n}\\
           w_{1.0} & w_{1.1} & ... & w_{1.n}\\
           \vdots & \vdots & \ddots & \vdots\\
           w_{k.0} & w_{k.1} & ... & w_{k.n}
     \end{bmatrix}
	 \begin{bmatrix}
	 	a_{0}^{(0)}\\
		a_{1}^{(0)}\\
		\vdots\\
		a_{n}^{(0)}
	 \end{bmatrix}
  \end{align}
$$

Just as before, it's still nice to give a name to the relevant weighted sum, like ${z}$, so that the activation of the last layer is just the special function, like the sigmoid applied to z.
![[substitute function.png]]

I makes sense, because these are all essentially the same equations we had before in the one-neuron-per-layer case; it just looks a little more complicated.
![[original.png]]

Indeed, the chain-rule derivative expression describing how sensitive the cost is to a specific weight looks essentially the same.

![[Pasted image 20210319113635.png]]

What does change here though is the derivative of the cost with respect to one of the activations in the layer ${(L - 1)}$.

![[Pasted image 20210319113658.png]]

In this case, the difference is the neuron influences the cost function through multiple different paths; that is, on one hand, it influences ${a_{0}^{(L)}}$, which plays a role in the cost function.

![[Pasted image 20210319113738.png]]

But it also has an influence on ${a_{1}^{(L)}}$, which also plays a role in the cost function.

![[Pasted image 20210319113853.png]]

And you have to add those up.

That's practically it. Once you know how sensitive the cost function is to the activations in this second to last layer, you can just repeat the process for all the weights and biases feeding into that layer.

![[Pasted image 20210319114019.png]]