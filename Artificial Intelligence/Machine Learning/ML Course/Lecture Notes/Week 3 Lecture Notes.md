## Logistic Regression
now we are switching from regression problems to **classification problems**; "logistic regression" is named that way for historical reasons and is actually an approach to classification problems, not regression problems.

## Binary Classification
Instead of the output vector y being a continuous range of values, it will only be 0 or 1.
$$
y∈{0,1}
$$
Where 0 is usually taken as the "negative class" and 1 as the "positive class", but you are free to assign any representation to it.

We're only doing two classes for now, called a "Binary Classification Problem".

One method is to use linear regression and map all predictions greater than 0.5 as a 1 and all less than 0.5 as a 0. This method doesn't work well bc classification is not actually a linear function.

###### Hypothesis Representation
Our hypothesis should satisfy:
$$
0≤h_{θ}​(x)≤1
$$

Our new form uses the "sigmoid function", also called the "logistic function":
$$
h_{θ}(x)=g(θ^{T}x)
$$
$$
z=θ^{T}x
$$
$$
g(z)=\frac{1}{1+e^{−z}}
$$
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/1WFqZHntEead-BJkoDOYOw_2413fbec8ff9fa1f19aaf78265b8a33b_Logistic_function.png?expiry=1617580800000&hmac=XDRVnn5VbUdSgkTXhRf3jkfH5mL9_pu9FDqq-hWCtPU)

The function g(z), shown here, maps any real number to the (0, 1) interval, making it useful for transforming an arbitrary-valued function into a function better suited for classification.
(try playing with [interactive plot of sigmoid function]([https://www.desmos.com/calculator/bgontvxotm](https://www.desmos.com/calculator/bgontvxotm)))

We start with the old hypothesis(linear regression), except that we want to restrict the range to 0 and 1. This is accomplished by plugging ${θ^{T}x}$ into the Logistic Function.

${h_{θ}}$ will give us the **probability** that the output is 1. For example, ${h_{θ}(x) = 0.7}$ gives us the probability of 70% that the output is 1.
$$
h_{θ}(x) = P(y = 1|x;θ) = 1 − P(y = 0|x;θ)
$$
$$
P(y=0|x;θ)+P(y=1|x;θ)=1
$$
The probability that the prediction is 0 is just the complement of the porbability that it is 1(e.g. if probability that it is 1 is 70%, then the probability that it is 0 is 30%).

## Decision Boundary
In order to get the discrete 0 or 1 classification, we can translate the output of the hypothesis function as follows:
$$
h_{θ}(x)≥0.5 → y =1
$$
$$
h_{θ}(x)<0.5→y=0
$$

The way the logistic function g behaves is that when its input is greater than or equal to zero, its output is greater than or equal to 0.5:
$$
g(z)≥0.5
$$
$$
when \hspace{0.2cm} z≥0
$$

Remember -
$$
z=0,e^{0}=1 ⇒ g(z)=1/2
$$
$$
z→∞,e^{−∞}→0⇒g(z)=1
$$
$$
z→−∞,e^{∞}→∞⇒g(z)=0
$$

So if the input to g is ${\theta^T X}$, then that means:
$$
h_{θ}(x)=g(θ^{T}x)≥0.5
$$
$$
when \hspace{0.2cm} θ^{T}x≥0
$$

From these statements we can now say:
$$
θ^{T}x≥0⇒y=1
$$
$$
θ^{T}x<0⇒y=0
$$

The **decision boundary** is the line that separates the area where y = 0 and where y = 1. It is created by the hypothesis function.

**Example:**
$$
θ = \begin{bmatrix}5\\-1\\0\end{bmatrix}
$$
$$
y = 1\hspace{0.2cm}if\hspace{0.2cm}5 + (-1)x_{1} + 0x_{2} ≥ 0
$$
$$
5 - x_{1} ≥ 0
$$
$$
-x_{1} ≥ -5
$$
$$
x_{1}≤5
$$

In this case, the decision boundary is a straight vertical line placed on the graph where ${x_{1} = 5}$, and everything to the left of that denotes y = 1, while everything to the right denotes y = 0.

Again, the input to the sigmoid function g(z) (e.g. ${\theta^T X}$) doesn't need to be linear, and could be a function that describes a circle (e.g. ${z = \theta_{0} + \theta_{1}x^{2}_{1} + \theta_{2}x^{2}_{2}}$) or any shape to fit the data.

## Cost Function
We can't use the same cost function that we use for linear regression because the Logistic Function will cause the output to be wavy, causing many local optima. In other words, it won't be a convex function.

Instead, the cost function for logistic regression looks like:
$$
J(\theta) = \frac{1}{m} \sum\limits_{i=1}^{m} Cost(h_{\theta}(x^{(i)}), y^{(i)})
$$
$$
Cost(h_{\theta}(x), y) = -log(h_{\theta}(x)) \hspace{2cm} if\hspace{0.2cm}y = 1
$$
$$
Cost(h_{\theta}(x), y) = -log(1 - h_{\theta}(x))\hspace{1.2cm}if \hspace{0.2cm} y = 0
$$
![[Pasted image 20210404190531.png]]

The more the hypothesis is off from y, the larger the cost function output. If the hypothesis is equal to y, the the cost is 0:
$$
Cost(h_{\theta}(x), y) = 0 \hspace{0.2cm} if \hspace{0.2cm} h_{\theta}(x) = y
$$
$$
Cost(h_{\theta}(x), y) → ∞ \hspace{0.2cm} if \hspace{0.2cm} y = 0 \hspace{0.2cm}and\hspace{0.2cm} h_{\theta}(x) → 1
$$
$$
Cost(h_{\theta}(x), y) → ∞ \hspace{0.2cm} if \hspace{0.2cm} y = 1 \hspace{0.2cm}and\hspace{0.2cm} h_{\theta}(x) → 0
$$

If the correct answer 'y' is 0, then the cost function will be 0 if the hypothesis function also outputs 0. If the hypothesis approaches 1, then the cost function will approach infinity.

if the correct answer 'y' is 1, then the cost function will be 0 if the hypothesis function outputs 1. If the hypothesis approaches 0, then the cost function will approach infinity.

Note that writing the cost function in this way guarantees that J(${\theta}$) is convex for logistic regression.

## Simplified Cost Function and Gradient Descent
We can compress the cost function's two conditional cases into one case:
$$
Cost(h_{\theta}(x), y) = -y\hspace{0.2cm}log(h_{\theta}(x)) - (1 - y)log(1 - h_{\theta}(x))
$$

Notice that when y is equal to 1, then the second term ${(1 - y)log(1 - h_{\theta}(x))}$ will be zero and won't affect the result. If y is equl to 0, then the first term ${-y\hspace{0.2cm}log(h_{\theta}(x))}$ will be zero and won't affect the result.

We can fully write out the entire cost function as follows:
$$
J(\theta) = -\frac{1}{m} \sum\limits_{i=1}^{m}[y^{(i)}\hspace{0.2cm}log(h_{\theta}(x^{(i)})) + (1 - y^{(i)}) log(1 - h_{\theta}(x^{(i)}))]
$$

A vectorized implementation is:
$$
h = g(X\theta)
$$
$$
J(\theta) = \frac{1}{m}\cdot(-y^{T} \hspace{0.2cm}log(h) - (1 - y)^{T}\hspace{0.2cm}log(1 - h))
$$

### Gradient Descent
Remember that the general form of gradient descent is:
$$
Repeat\hspace{0.2cm} \{
$$
$$
\theta_{j} := \theta_{j} - α\frac{∂}{∂\theta_{j}}J(\theta)
$$
$$
\}
$$

We can work out the derivative part using calculus to get:
$$
Repeat\hspace{0.2cm}\{
$$
$$
\theta_{j} := \theta_{j} - \frac{α}{m} \sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})x_{j}^{(i)}
$$
$$
\}
$$

Notice that this algorithm is identical to the one we used in linear regression. We still have to simultaneously update all values in theta.

A vectorized implementation is:
$$
\theta := \theta - \frac{α}{m} X^{T}(g(X\theta) - \overrightarrow{y})
$$

### Partial derivative of ${J(\theta)}$
First calculate derivative of sigmoid function(it will be useful while finding partial derivative of J(\theta)):
$$
σ(x)^{′} = (\frac{1}{1 + e^{-x}})^{′} = \frac{-(1 + e^{-x})^{′}}{(1 + e^{-x})^{2}} = \frac{-1^{′} - (e^{-x})^{′}}{(1 + e^{-x})^{2}} = \frac{0 - (-x)^{′}(e^{-x})}{(1 + e^{-x})^{2}} = \frac{-(-1)(e^{-x})}{(1 + e^{-x})^{2}} = \frac{e^{-x}}{(1 + e^{-x})^{2}}
$$
$$
\hspace{1cm}=(\frac{1}{1 + e^{-x}})(\frac{e^{-x}}{1 + e^{-x}}) = σ(x)(\frac{+1-1+e^{-x}}{1 + e^{-x}}) = σ(x)(\frac{1+e^{-x}}{1+e^{-x}} - \frac{1}{1 + e^{-x}}) = σ(x)(1 - σ(x))
$$

Now we are ready to find out the resulting partial derivative:
$$
\frac{∂}{∂\theta_{j}}J(\theta) = \frac{∂}{∂\theta_{j}} \frac{-1}{m}\sum\limits_{i=1}^{m}[y^{(i)}log(h_{\theta}(x^{(i)})) + (1 - y^{(i)})log(1 - h_{\theta}(x^{(i)}))]
$$
$$
\hspace{1.8cm}=-\frac{1}{m}\sum\limits_{i=1}{m}[y^{(i)}\frac{∂}{∂\theta_{j}}\hspace{0.1cm}log(h_{\theta}(x^{(i)})) + (1 - y^{(i)})\frac{∂}{∂\theta_{j}}\hspace{0.1cm}log(1 - h_{\theta}(x^{(i)}))]
$$
(continued: too lazy to write whole thing in latex)
↓
![[full equation derivation.png]]

The vectorized version;
$$
∇ J(\theta) = \frac{1}{m}\cdot X^{T}\cdot (g(X\cdot\theta)-\overrightarrow{y})
$$

## Advanced Optimization
"Conjugate gradient", "BFGS" and "L-BFGS" are more sophisticated, faster ways to optimize θ that can be used instead of gradient descent. Andrew Ng suggests not to write these more sophisticated algorithms yourself(unless you are an expert in numerical computing) but use the libraries instead, as they're already tested and highly optimized. Octave provides them.

We first need to provide a function that evaluates the following two functions for a given input value θ:
$$
J(\theta)
$$
$$
\frac{∂}{∂\theta_{j}}J(\theta)
$$

We can write a single function that returns both of these:
```matlab
function [jVal, gradient] = costFunction(theta)
	jVal = [...code to compute J(theta)...];
	gradient = [...code to compute derivative of J(theta)...];
end
```

Then we can use octave's "fminunc()" optimization algorithm along with the "optimset()" function that creates an object containing the options we want to send to "fminunc()". (Note: the value for MaxIter should be an integer, not a character string)
```matlab
options = optimset('GradObj', 'on', 'MaxIter', 100);
	initialTheta = zeros(2, 1);
	[optTheta, functionVal, exitFlag] = fminunc(@costFunction, initialTheta, options);
```

We give to the function "fminunc()" the cost function, the initial vector of theta values, and the "options" object that was created beforehand.

## Multiclass Classification: One-vs-all
Now we will approach the classification of data in more than two categories. Instead of y = {0, 1} we will expand the definition so that y = {0, 1, ...n}.

In this case we divide the problem into n + 1(+1 because the index starts at 0) binary classification problems; in each one, we predict the probability that 'y' is a member of one of the classes.
$$
y ∈ {0, 1, ..., n}
$$
$$
h_{\theta}^{(0)}(x) = P(y=0|x;\theta)
$$
$$
h_{\theta}^{(1)}(x) = P(y=1|x;\theta)
$$
$$
...
$$
$$
h_{\theta}^{(n)}(x) = P(y=n|x;\theta)
$$
$$
prediction = \underset{i}{max}(h_{\theta}^{(i)}(x))
$$

We are basically choosing one class and then lumping all the others into a single second class. We do this repeatedly, applying binary logistic regression to each case, and then use the hypothesis that returned the highest value as the prediction.

## ML: Regularization
### The Problem of Overfitting
Regularization is designed to address the problem of overfitting.

High bias or underfitting is when the form of the hypothesis function h maps poorly to the trend of the data. It is usually caused by a function that is too simple or uses too few features. e.g. if we take ${h_{\theta}(x) = \theta_{0} + \theta_{1}x_{1} + \theta_{2}x_{2}}$ then we are making an initial assumption that a linear model will fit the training data well and will be able to generalize but that may not be the case.

At the other extreme, overfitting or high variance is caused by a hypothesis function that fits the available data but doesn't generalize well to predict new data. It is usually caused by a complicated function that creates a lot of unecessary curves and angles unrelated to the data.

This terminology is applied to both linear and logistic regression. There are two main options to address the issue of overfitting:

1) Reduce the number of features:
	a) Manually select which features to keep
	b) Use a model selection algorithm
2) Regularization
Keep all the features, but reduce the parameters ${\theta_{j}}$.

Regularization works well when we have a lot of slightly useful features.

## Cost Function
If we have overfitting from the hypothesis function, we can reduce the weight that some of the terms in the function carry by increasing their cost.

Say we wanted to make the following function more quadratic:
$$
\theta_{0} + \theta_{1}x + \theta_{2}x^{2} + \theta_{3}x^{3} + \theta_{4}x^{4}
$$

We'll want to eliminate the influence of ${\theta_{3}x^{3}}$ and ${\theta_{4}x^{4}}$. Without actually getting rid of these features or changing the form of the hypothesis, we can instead modify the **cost function**:
$$
min_{\theta}\hspace{0.2cm}\frac{1}{2m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})^{2} + 1000\cdot \theta_{3}^{2} + 1000\cdot \theta_{4}^{2}
$$

We've added two extra terms at the end to inflate the cost of ${\theta_{3}}$ and ${\theta_{4}}$. Now, in order for the cost function to get close to zero, we will have to reduce the values of ${\theta_{3}}$ and ${\theta_{4}}$ to near zero. This will in turn greatly reduce the values of ${\theta_{3}x^{3}}$ and ${\theta_{4}x^{4}}$ in the hypothesis function.

We could also regularize all of the theta parameters in a single summation:
$$
min_{\theta}\frac{1}{2m} [\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})^{2} + λ\sum\limits_{j=1}^{n} \theta_{j}^{2}]
$$

The λ, or lambda, is the **regularization parameter**. It determines how much the costs of the theta parameters are inflated. You can visualize the effect of regularization in the [interactive plot](https://www.desmos.com/calculator/1hexc8ntqp).

Using the above cost function with the extra summation, we can smooth the output of the hypothesis function to reduce overfitting. If lambda is chosen to be too large, it may smooth out the function too much and cause underfitting.

## Regularized Linear Regression
We can apply regularization to both linear regression and logistic regression. We will approach linear regression first.

### Gradient Descent
We will modify the gradient descent function to separate out ${\theta_{0}}$ from the rest of the parameters because we don't want to penalize ${\theta_{0}}$.
$$
Repeat\hspace{0.2cm}\{
$$
$$
\theta_{0} := \theta_{0} - α\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})x_{0}^{(i)}
$$
$$
\theta_{j} := \theta_{j} - α [(\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})x_{j}^{(i)}) + \frac{λ}{m}\theta_{j}]\hspace{1.5cm}j ∈ \{1, 2...n\}
$$
$$
\}
$$

The term ${\frac{λ}{m}\theta_{j}}$ performs the regularization.

With some manipulation the update rule can also be represented as:
$$
\theta_{j} := \theta_{j}(1 - α\frac{λ}{m}) - α\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})x_{j}^{(i)}
$$

The first term in the above equation, ${1 - α\frac{λ}{m}}$ will always be less than 1. Intuitively you can see as reducing the value of ${\theta_{j}}$ by some amount on every update.

Notice that the second term is not exactly the same as it was before.

### Normal Equation
Now let's approach regularization using the alternate method of the non-iterative normal equation.

To add in regularization, the equation is the same as the original, except that we add another term inside the parentheses:
![[altered normal equation.png]]

L is a matrix with 0 at the top left and 1's down the diagona. with 0's everywhere else. It should have dimension (n+1) × (n+1). Intuitively, this is the identity matrix(though we aren't including ${x_{0}}$), multiplied with a single real number λ.

Recal lthat if m ≤ n, then ${X^{T}X}$ is non-invertible. However, when we add the term ${λ\cdot L}$, then ${X^{T}X + λ\cdot L}$ becomes invertible.

## Regularized Logistic Regression
We can regularize logistic regression in a similar way that we regularize linear regression. Let's start with the cost function.

### Cost Function
Recall that the cost function for logistic regression was:
$$
J(\theta) = -\frac{1}{m}\sum\limits_{i=1}^{m} [y^{(i)}\hspace{0.2cm}log(h_{\theta}(x^{(i)})) + (1-y^{(i)})\hspace{0.2cm}log(1-h_{\theta}(x^{(i)}))]
$$

We can regularize this equation by adding a term to the end:
$$
J(\theta) = -\frac{1}{m}\sum\limits_{i=1}^{m} [y^{(i)}\hspace{0.2cm}log(h_{\theta}(x^{(i)})) + (1-y^{(i)})\hspace{0.2cm}log(1-h_{\theta}(x^{(i)}))] + \frac{λ}{2m}\sum\limits_{j=1}^{n}\theta_{j}^{2}
$$

**Note Well:** The second sum, ${\sum\limits_{j=1}^{n}\theta_{j}^{2}}$ **means to explicity exclude** the bias term, ${\theta_{0}}$. i.e. the ${\theta}$ vector is indexed from 0 to n(holding n+1 values, ${\theta_{0}}$ through ${\theta_{n}}$), and this sum explicitly skips ${\theta_{0}}$, by running frum 1 to n, skipping 0.

### Gradient Descent
Just like with linear regression, we want to **separately** update ${\theta_{0}}$ and the rest of the parameters because we don't want to regularize ${\theta_{0}}$.
$$
Repeat\hspace{0.2cm}\{
$$
$$
\theta_{0} := \theta_{0} - α\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})x_{0}^{(i)}
$$
$$
\theta_{j} := \theta_{j} - α[(\frac{1}{m}\sum\limits_{i=1}^{m}(h_{\theta}(x^{(i)}) - y^{(i)})x_{j}^{(i)}) + \frac{  
λ}{m}\theta_{j}]\hspace{1.5cm}j∈ \{1, 2...n\}
$$
$$
\}
$$

This is identical to the gradient descent function presented for linear regression.

## Initial Ones Feature Vector
### Constant Feature
As it turns out it is crucial to add a constant feature to the pool of features before starting any training of the machine. Normally that feature is just a set of ones for all the training examples.

Concretely, if X is the feature matrix then ${X_{0}}$ is a vector with ones.

Below are some insights to explain the reason for this constant feature. The first part draws some analogies from electrical engineering concept, the second looks at understanding the ones vector by using a simple machine learning concept.

### Electrical Engineering
From electrical engineering, in particular signal processing, this can be explained as DC and AC.

The initial feature vector X without the constant term captures the dynamics of the model. That means those features particularly record changes in the output y - in other words changing some feature ${X_{i}}$ where ${i\neq 0}$ will have a change on the output y. AC is normally made out of many components or harmonics; hence we also have many features(yet we have one DC term).

The constant feature represents the DC component. In control engineering this can also be the steady state.

Interestingly removing the DC term is easily done by differentiating the signal - or simply taking a difference between consecutive points of a discrete signal(it should be noted that at this point the analogy is implying time-based signals - so this will also make sense for machine learning application with a time bases - e.g. forecasting stock exchange trends).

Another interesting note: if you were to play an AC+DC signal as well as an AC only signal where both AC components are the same then they would sound exactly the same. That is because we only hear changes in signals and Δ(AC+DC)=Δ(AC).

### Housing price example
Suppose you design a machine which predicts the price of a house based on some features. In this case what does the ones vector help with?

Let's assume a simple model which has features that are directly proportional to the expected price i.e. if feature Xi increases so that the expected price y will also increase. So as an example we could have two features: namely the size of the house in \[m2\], and the number of rooms.

When training the machine you will start by prepending a ones vector ${X_{0}}$. You may then find after training that the weight for the initial features of ones is some value θ0. As it turns, when applying the hypothesis function ${h_{\theta}(X)}$ - in the case of the initial feature - you will just be multiplying by a constant(most probably θ0 if you aren't applying any other functions such as sigmoids). This constant(let's say it's ${\theta_{0}}$ for argument's sake) is the DC term. It is a constant that doesn't change.

But what does it mean for this example? Well, let's suppose that someone knows that you have a working model for housing prices. It turns out that for this example, if they ask you how much money they can expect if they sell the house you can say that they need at least θ0 dollars(or rands) before you even use the learning machine. As with the above analogy, your constant θ0 is somewhat of a steady state where all your inputs are zeros. Concretely, this is the price of a house with no rooms which takes up no space.

However this explanation has some holes because if you have some features which decrease the price e.g. age, then the DC term may not be an absolute minimum of the price. This is because the age may make the price go even lower.

Theoretically if you were to train a machine without a ones vector ${f_{AC}(X)}$, its output may not match the output of a machine which had a ones vector ${f_{DC}(X)}$. However, ${f_{AC}(X)}$ may have exactly the same trend as ${f_{DC}(X)}$ i.e. if you were to plot both the machine's output you would find that they may look exactly the same except that it seems one output has just been shifted(by a constant). With reference to the housing price problem: suppose you make predictions on two houses ${house_{A}}$ and ${house_{B}}$ using both machines. It turns out while the outputs from the two machines would be different, the difference between houseA and houseB's predictions according to both machines would be exactly the same. Realistically, that means a machine trained without the ones vector ${f_{A}C}$ could actually be very useful if you have just one benchmark point. This is because you can find out the missing constant by simply taking a difference between the machine's prediction and an actual price - then when making predictions you simply add that constant to what even output you get. That is: if ${house_{benchmark}}$ is your benchmark then the DC component is simply ${price(house_{benchmark}) - f_{AC}(features(house_{benchmark}))}$.

A more simple and crude way of putting it is that the DC component of the model represents the inherent bias of the model. The other features then cause tension in order to move away from that bias position.

### A simpler approach
A "bias" feature is simply a way to move the "best fit" learned vector to better fit the data. For example, consider a learning problem with a single feature ${X_{1}}$. The formula without the ${X_{0}}$ feature is just ${theta_{1}*X_{1} = y}$. This is graphed as a line that always passes through the origin, with slope y/theta. The ${x_{0}}$ term allows the line to pass through a different point on the y axis. This will almost always give a better fit. Not all best fit lines go through the origin (0, 0).