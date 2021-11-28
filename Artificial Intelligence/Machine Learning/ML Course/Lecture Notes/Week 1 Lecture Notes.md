## Introduction to ML
### What is Machine Learning?
two definitions of ML are offered; Arthur Samuel described it as "the field of study that gives computers the ability to learn w/o being explicitly programmed." This is an older, informal definition.

Tom Mitchell provides a more modern definition: "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

i.e. playing checkers.

E = the experience of playing many games of checkers

T = the task of playing checkers

P = the probability that the program will win the next game

in general, any ML problem can be assigned to one of two broad classifications: supervised learning, or unsupervised learning.

##### Supervised Learning
in supervised learning, the dataset is given and already know that the correct output should look like, having the idea that there is a relationship between the input and the output.

supervised learning problems are categorized into "**regression**" and "**classification**" problems. In a regression problem, we are trying to predict results within a continuous output, meaning that we are trying to map input variables to some continuous function.
In a classification problem, we are instead trying to predict results in a discrete output. In other words, we are trying to map input variables into discrete categories.

Here is a description on **Continuous** and **Discrete** data.

**Example 1:**
Given data about the size of houses on the real estate market, try to predict their price.
Price as a function of size is a continuous output, so this is a **regression** problem.

could turn this example into a classification problem by instead making the output abt whether the house "sells for more or less than the asking price." Here the houses are being classified based on price into two discrete categories.

**Example 2:**
(a) Regression - Given a picture of Male/Female, have to predict their age on the basis of given picture.

(b) Classification - Given a picture of Male/Female, have to predict whether they are in High school, College, Graduate Age. 
Another example for Classification - Banks have to decide whether or not to give a loan to someone on the basis of their credit history.

##### Unsupervised Learning
unsupervised learning, on the other hand, allows the user to approach problems with little or no idea of what the results should look like. Can derive structure from data where don't necessarily know the effect of the variables.

can derive this structure by clustering the data based on relationships among the variables in the data - assuming there are some number of groups called **K Clusters**, but don't know wher they are. To help this, can use the **k-means clustering** algorithm -> simple; all it needs is a way to compare observations, a way to guess how many clusters exist in the data, and a way to calculate averages for each cluster it predicts.

Calculate mean by adding up all datapoints in a cluster & dividing by the total number of points.

1. AI will predict(which points should be clustered together)
2. AI will learn, update beliefs to agree with observation of the world <- corrects by calculating new averages

correction = **learning step**: repeat process, starting w/ new prediction step(create new labels based on preset random ones)

based on the preset-random lables that had calculated new averages, take the points closest to them and change them to that label, and calculate new averages again, so can repeat again: predict, learn, predict, learn by moving the averages. -> from datapoints get meaningful abstraction

finding meaningful patterns more abstract than just determining individual pixe,s is called **Representation Learning**. This happens both in supervised & unsupervised learning models, so can do it w/ or w/o labels to find patterns in the world: i.e. individual lines and curves inside a number-recognition program.

**autoencoder**: type of neural network which uses the same basic principles of weights and biases to process inputs, pass data onto hidden neruon layers, and finally to a prediction output layer.

with unsupervised learning there is no feedback based on the prediction results, i.e. there is no one to correct the machine/you.

**Example:**

**Clustering**: take a collection of 1000 essays written on the US Economy, and find a way to automatically group these essays into a small number that are somehow similar or related by different variables such as word frequency, sentence length, page count, and so on.

**Non-clustering**: The "**Cocktail Party Algorithm**", which can find structure in messy data(such as the identification of individual voices and music from a mesh of sounds at a [cocktail party](https://en.wikipedia.org/wiki/Cocktail_party_effect)).

There is a third kind of learning called **Reinforcement Learning**. This is somewhat between the first two kinds.

i.e. give the user a million coins and tells them that there are 3 categories to sort them in, but don't specify which are the categories, nor the standard weights of any.

## Linear Regression with One Variable
![](https://miro.medium.com/max/3480/1*dm6ZaX5fuSmuVvM4Ds-vcg.jpeg)
[Linear Regression](https://medium.datadriveninvestor.com/linear-regression-hypothesis-function-cost-function-and-gradient-descent-part-1-6cd865552923)
[Intro to Logistic Regression](https://towardsdatascience.com/introduction-to-logistic-regression-66248243c148)
### Model Representation
recall that in *regression problems*, are taking input variables and trying to fit the output onto a *continuous* expected result function.

linear regression with one variable is also known as "univariate linear regression".

univariate linear regression is used when want to predict a **single output** value y from a **single input** value x. Doing **supervised learning** here, so that means should already have an idea abt what the input/output cause and effect should be.

In practice, **m** = Number of training examples.

### The Hypothesis Function
how to represent hypothesis h, given an input and to eject an output.
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/H6qTdZmYEeaagxL7xdFKxA_2f0f671110e8f7446bb2b5b2f75a8874_Screenshot-2016-10-23-20.14.58.png?expiry=1616630400000&hmac=zWvJMHtzJBKYZ-6LB-Xj56raRicK307W_518YDqDke8)
the hypothesis function has the general form:
$$
{\hat{y}}​=h_{θ}​(x)=θ_{0}​+θ_{1}​x
$$
shorthand: just write ${h(x)}$
going to predict that y is a linear function of x. what the function is doing is that it's predicting that y is some straight line function of x.

![Linear Regression (Univariate Linear Regression) | by Subash Basnet | Bajra  Technologies Blog](https://miro.medium.com/max/2732/1*_YZQmKSrXbdanRU1cAJ68w.png)

note that this is like the equation of a straight line. Give to ${h_{0}(x)}$ values for ${θ_{0}}$ and ${θ_{1}}$ to get the estimated output ${y}$. In other words, we are trying to create a function called ${h_{θ}}$ that is trying to map the input data(the x's) to the output data(the y's).

i.e. suppose have the following set of training data:

input x | output y
:----------------|-------------:
0 | 4
1 | 7
2 | 7
3 | 8

now we can make a random guess abt the ${h_{0}}$ function: ${θ_{0} = 2}$ and ${θ_{1} = 2}$. The hypothesis function becomes ${h_{θ}(x) = 2 + 2x}$.

so for input 1 to the hypothesis, y will be 4. This is off by 3. Note that will be trying out various values of ${θ_{0}}$ and ${θ_{1}}$ to try to find values which provide the best possible "fit" or the most representative "straight line" through the datapoints mapped on the x-y plane.

## Cost Function
[The Derivative of Cost Function for Logistic Regression](https://medium.com/analytics-vidhya/derivative-of-log-loss-function-for-logistic-regression-9b832f025c2d)
[Cost Function](https://medium.com/analytics-vidhya/cost-function-explained-in-less-than-5-minutes-c5d8a44b918c)
![](https://miro.medium.com/max/1800/0*MJ4EJ3I79E6PFUO4.gif)
[Cost Function for Beginners](https://towardsdatascience.com/machine-leaning-cost-function-and-gradient-descend-75821535b2ef)
it is possible to measure the accuracy of the hypothesis function by using a **cost function**. This takes the average(different type of average) of all the results of the hypothesis with inputs from x's compared to the actual output y's.

${θ_{i}}$'s are the parameters of the model. How to choose the parameters depends on what hypothesis function you want.

How to come up with the parameters?
Idea: Choose ${θ_{0}}$, ${θ_{1}}$ so that ${h_{θ}(x)}$ is close to ${y}$ for the training examples ${(x, y)}$.

sole a minimization problem: minimize the two parameters. Want ${(h_{θ}(x) - y)^2}$ to be small.

${(x^{(i)}, y^{(i)})}$ represents the ith training example.

want to sum over the training set of the square difference between prediction and the actual number. sum of training set, sum of i = one through m of the difference of the squared error/squared difference between predicted value and the actual value with m = #(size of training set).
$$
\sum\limits_{i = 1}^{m}(h_{θ}(x^{(i)}) - y^{(i)})^2
$$

note that the hash sign represents the size of the training set.

to make math easier, going to look at we are 1/m times so let's try to minimize the average minimize 1/2m.
Putting the 2 at the constant 1/2 in front may make the math easier & return the same values.

the notation of ${θ_{0}}$ and ${θ_{1}}$ is that will find the values of theta 0 and theta 1 that causes this expression to be minimized, and the expression depends on the theta 0 and theta 1.

Closing the problem as, find the values of theta zero and theta 1 so that the average, 1 over the 2m, times the sum of square errors between the predictions on the training set minus the actual values of the houses on the training set is minimized. This'll be the overall objective function for linear regression.

[Cost Function + Gradient Descent](https://towardsdatascience.com/machine-learning-fundamentals-via-linear-regression-41a5d11f5220)

$$
J(θ_{0}, θ_{1}) = \frac{1}{2m} \sum\limits_{i=1}^m (\hat{y}_{i} - y_{i})^2 = \frac{1}{2m} \sum\limits_{i=1}^m (h_{θ}(x_{i}) - y_{i})^2
$$
to break this equation apart, it is ${\frac{1}{2}\bar{x}}$ where ${\bar{x}}$ is the mean of the squares of ${h_{θ}(x_{i}) - y_{i}}$, or the difference between the **predicted** value and the **actual** value.

this function is otherwise called the **"Squared Error function"**, or **"Mean Squared Error"**. The mean is halved(${\frac{1}{2m}}$) as a convenience for the computation of the **[gradient descent](https://builtin.com/data-science/gradient-descent)**, as the derivative term of the square function will cancel out the ${\frac{1}{2}}$ term.

now we are able to concretely measure the accuracy of the predictor function against the correct results that are given so that new results can be predicted that we don't have.

if try to think of it in visual terms, the training data set is scattered on the x-y plane. We are trying to make a straight line(defined by ${h_{θ}(x)}$) which passes through this scattered set of data. The objective is to get the best possible line, which will be such so that the average squared vertical distances of the scattered points from the line will be the least. In the best case, the line should pass through all the points of the training data set. In such a case the value of ${J(θ_{0}, θ_{1})}$ will be 0.

![Descending into ML: Linear Regression | Machine Learning Crash Course](https://developers.google.com/machine-learning/crash-course/images/CricketLine.svg)
![](https://miro.medium.com/max/1200/1*PQ8tdohapfm-YHlrRIRuOA.gif)
(epochs = iterations)

in order to better visualize J, going to start with a simplified hypothesis function, like ${h_{θ}(x) = θ_{1}x}$(think of this as setting parameter ${θ_{0}}$ to 0). So only one parameter is here: ${θ_{1}}$.

Now, cost function is similar to before:
$$
J(θ_{1}) = \frac{1}{2m} \sum\limits_{i=1}^{m}(h_{θ}(x^{(i)}) - y^{(i)})^{2}
$$
except for the fact that ${h_{θ}(x^{(i)})}$ is just equal to ${θ_{1}x^{(i)}}$. And there's only one parameter, ${θ_{1}}$, so the objective here is to minimize ${J(θ_{1})}$ rather than ${J(θ_{0}, θ_{1})}$.

What this pictures, what this means is that if ${θ_{0} = 0}$ , that corresponds to choosing only a hypothesis function that passes through the origin. Using this simplified definition of hypothesizing the cost function, let's try to understand the cost function concept better.

It turns out that there are 2 key functions want to understand. First is the hypothesis, second is cost.

Hypothesis, or ${h_{θ}(x)}$: for fixed ${θ_{1}}$, this is a function of x.

Cost, or ${J(θ_{1})}$: function of the parameter ${θ_{1}}$.

Now, we want to find out what ${J(θ_{1})}$ would be equal to:
$$
J(θ_{1}) = \frac{1}{2m} \sum\limits_{i=1}^{m}(h_{θ}(x^{(i)}) - y^{(i)})^{2}
$$

to simplify further, based on the notion that ${h_{θ}(x^{(i)}) = θ_{1}x^{(i)}}$:
$$
\frac{1}{2m} \sum\limits_{i = 1}^{m}(θ_{1}x^{(i)} - y^{(i)})^{2} = \frac{1}{2m}(0^{2} + 0^{2} + 0^{2}) = 0^{2}
$$

for plotting the cost function, the terms here equals zero: the training examples, (1, 1) (2, 2) (3, 3). if ${θ_{1}}$ is equal to 1 then ${h_{θ}(x^{(i)})}$ is equal to ${y^{(i)}}$ exactly, so the terms are equal to zero. know that ${J(θ_{1})}$ is equal to zero. 

We can now plot the cost function, with the point ${J(1) = 0}$, since the x-axis is labeled with ${θ_{1}}$.

![](https://img-blog.csdnimg.cn/20191031235933878.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Vkd2FyZF93YW5nMQ==,size_16,color_FFFFFF,t_70)

${θ_{1}}$ can take on a range of different values. Right? So ${θ_{1}}$ can take on the negative values, zero and positive values. So, what if ${θ_{1} = 0.5}$? Let's go ahead and plot that.

![](https://img-blog.csdnimg.cn/20191101231712466.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Vkd2FyZF93YW5nMQ==,size_16,color_FFFFFF,t_70)

I'm now going to set ${θ_{1} = 0.5}$, and in that case, my hypothesis looks like this. As a line with slope equals to 0.5. And, let's compute ${J(0.5)}$. So, that is going to be ${\frac{1}{2m}}$ of my usual cost function. It turns out that the cost function is going to be the sum of square values of the height of this line, plus the sum of square of the height of that line, plus the sum of square of the height of that line, right? Because just this vertical distance, that's the difference between ${y^{(i)}}$ and the predicted value ${h_{θ}(x^{(i)})}$. So, the first example is going to be ${(0.5*1-1)^{2}}$. For my second example, I get ${(0.5*2-2)^{2}}$, because my hypothesis predicted one, but the actual housing price was two. And finally, plus ${(0.5*3-3)^{2}}$. And so that's equal to ${1/(2*3)(3.5)≈ 0.58}$. So now we know ${J(0.5)}$ is about 0.58. Let's go and plot that. So, we plot that which is maybe about over there. Now, let's do one more. How about if ${θ _{1}=0}$, what is ${J(0)}$ equal to?

![](https://img-blog.csdnimg.cn/20191103205106873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Vkd2FyZF93YW5nMQ==,size_16,color_FFFFFF,t_70)

It turns out if ${θ_{1}=0}$, ${h_{θ }(x)}$ is just equal to 0, you know, this flat line, that just goes horizontally like that. And so, measuring the errors. We have that just ${J(0)=1/(2*m)*(1^{2}+2^{2}+3^{2})=1/6*14\approx 2.3}$. So, let's go ahead and plot that as well. So, it ends up with a value around 2.3. And of course, we can keep on doing this for other values of ${θ_{1}}$. It turns out that you can have negative for other values of ${θ_{1}}$ as well. So if ${θ_{1}}$ is negative, then ${h_{θ}(x)}$ would be equal to say ${h_{\theta }(x)=-0.5x}$, then ${\theta _{1}=-0.5}$, and so that corresponds to a hypothesis with a slope of -0.5. And you can actually keep on computing these errors. This turns out to be, you know, for -0.5, it turns out to have really high error. It works out to be something, like, 5.25 and so on. And for different values of ${θ_{1}}$, you can compute these things. And it turns out that you computed range of values, you get something like that. And by computing the range of values, you can actually slowly create out what this function ${J(θ)}$ looks like. And that's what ${J(θ)}$ is. To recap, for each value of ${θ_{1}}$, right? Each value of !${θ_{1}}$ corresponds to a different hypothesis, or to a different straight line fit on the left. And for each value of ${θ_{1}}$, we could then derive a different a different value of ${J(θ_{1})}$. And for example, ${θ_{1} = 1}$ corresponds to this straight line (in cyan) straight through the data. Whereas ${θ_{1} = 0.5}$, and this point shown in magenta, corresponded to maybe that line (in magenta). And ${θ_{1} = 0}$, which is shown in blue, that corresponds to this horizontal line (in blue). So, for each value of ${θ_{1}}$, we wound up with a different value of ${J(\theta _{1})}$. And then we could use this to trace out this plot on the right. Now you remember the optimization objective for our learning algorithm is we want to choose the value of ${\theta _{1}}$, that minimizes ${J(\theta _{1})}$. This (${\overset{minimize}{\theta _{1}} J(\theta _{1})}$) was our objective function for the linear regression. Well, looking at this curve, the value that minimizes ${J(\theta _{1})}$ is ${\theta _{1}=1}$. And low and behold, that is indeed the best possible straight line fit throughout data, by setting ${\theta _{1}=1}$. And just for this particular training set, we actually end up fitting it perfectly. And that's why minimizing ${J(\theta _{1})}$ corresponds to finding a straight line that fits the data well. So, to wrap up, in this video (article), we looked at some plots to understand the cost function. To do so, we simplified the algorithm, so that it only had one parameter ${\theta _{1}}$. And we set the parameter ${\theta _{0}=0}$. In the next video (article), we'll go back to the original problem formulation, and look at some visualizations involving both ${\theta _{0}}$ and ${\theta _{1}}$. That is without setting ${\theta _{0}=0}$. And hopefully that will give you an even better sense of what the cost function J is doing in the original linear regression.

![5 Concepts You Should Know About Gradient Descent and Cost Function -  KDnuggets](https://miro.medium.com/max/1400/1*tQTcGTLZqnI5rp3JYO_4NA.png)

## ML: Gradient Descent
[Gradient Descent in Linear Regression]()https://www.geeksforgeeks.org/gradient-descent-in-linear-regression/)
So now there is the hypothesis function and we have a way of measuring how well it fits into the data. Now we need to estimate the parameters in the hypothesis function. That's where gradient descent comes in.

imagine that we graph the hypothesis function based on its fields ${θ_{0}}$ and ${θ_{1}}$(actually we are graphing the cost function as a function of the parameter estimates). This can be kind of confusing; we are moving up to a higher level of **abstraction**. We are not graphing x and y itself, but the parameter range of the hypothesis function and the cost resulting from selecting a particular set of parameters.

put ${θ_{0}}$ on the x axis and ${θ_{1}}$ on the y axis, with the cost function on the vertical z axis. The points on the graph will be the result of the cost function using the hypothesis with those specific theta parameters.

we will know that it was a success when the cost function is at the very bottom of the pits in the graph, i.e. when the value is the minimum.

the way we do this is by taking the **derivative**(the tangential line to a function) of the cost function. The **slope of the tangent** is the **derivative** at that point and it will give us a direction to move towards. We make steps down the cost function in the direction with the **steepest descent**, and the size of each step is determined by the parameter **α**, which is called the **learning rate**.

The gradient descent algorithm is:

repeat until **[convergence](https://docs.paperspace.com/machine-learning/wiki/convergence#:~:text=A%20machine%20learning%20model%20reaches,will%20not%20improve%20the%20model.)**:
$$
θ_{j} := θ_{j} - α\frac{∂}{∂θ_{j}} J(θ_{0}, θ_{1})
$$
where
	${j = 0, 1}$ represents the **[feature index number](https://en.wikipedia.org/wiki/Feature_(machine_learning))**.
	
Intuitively, this could be thought of as:

repeat until convergence:

${θ_{j} := θ_{j} - α}$\[Slope of tangent aka derivative in j dimension]


**Gradient Descent for Linear Regression**

When specifically applied to the case of **linear regression**, a new form of the gradient descent equation can be derived. We can substitute the actual cost function and the actual hypothesis function and modify the equation to:

$$
repeat \hspace{0.2cm} until \hspace{0.2cm} convergence:\hspace{0.2cm}\{
$$
$$
θ_{0} := θ_{0} - α \frac{1}{m}\sum\limits_{i=1}^m(h_{θ}(x_{i}) - y_{i})
$$
$$
θ_{1} := θ_{1} - α \frac{1}{m}\sum\limits_{i=1}^m((h_{θ}(x_{i}) - y_{i})x_{i})
$$
$$
\hspace{0.2cm}\}
$$
where m is the size of the training set, ${θ{0}}$ a constant that will be changing simultaneously with ${θ_{1}}$; and that for ${θ_{1}}$ we are multiplying ${x_{i}}$ at the end due to the derivative.

the point of all this is that if we start with a guess for the hypothesis and then repeatedly apply these gradient descent equations, the hypothesis will become more and more accurate.

Here is a **[Gradient Descent for Linear Regression: visual worked example](https://www.youtube.com/watch?v=WnqQrPNYz5Q)** video to help visualize the improvement of the hypothesis as the error function reduces.

## Matrices and Vectors
Matrices are 2-dimensional arrays:
$$
[\hspace{0.2cm}a\hspace{0.5cm}b\hspace{0.5cm}cd\hspace{0.5cm}e\hspace{0.5cm}fg\hspace{0.5cm}h\hspace{0.5cm}ij\hspace{0.5cm}k\hspace{0.5cm}l\hspace{0.2cm}]
$$

The above matrix has four rows and three columns, so it's a 4 x 3 matrix.

A vector is a matrix with one column and many rows:
$$
[\hspace{0.2cm}wxyz\hspace{0.2cm}]
$$

So vectors are a subset of matrices. The above vector is a 4 x 1 matrix.


**Notation and terms:**

- ${A_{ij}}$ refers to the element in the ith row and jth column of matrix A.
- A vector with 'n' rows is referred to as an 'n'-dimensional vector
- ${v_{i}}$ refers to the element in the ith row of the vector
- In generall, all the vectors and matrices(in ML) will be 1-indexed. Note that for some programming languages, the arrays are 0-indexed.
- Matrices are usually denoted by uppercase names while vectors are lowercase
- "Scalar" means that an object is a single value, not a vector or matrix
- ${\rm I\!R}$ refers to the set of scalar real numbers
- ${\rm I\!R^n}$ refers to the set of n-dimensional vectors of real numbers

## Addition and Scalar Multiplication
Addition and subtraction are **element-wise**, so you simply add or subtract each corresponding element:
$$
[\hspace{0.2cm}a\hspace{0.5cm}bc\hspace{0.5cm}d\hspace{0.2cm}] + [\hspace{0.2cm}w\hspace{0.5cm}xy\hspace{0.5cm}z\hspace{0.2cm}] = [\hspace{0.2cm}a + w\hspace{0.5cm}b + xc + y\hspace{0.5cm}d + z\hspace{0.2cm}]
$$
to add or subtract two matrices, their dimensions must be **the same**.

in scalar multiplication, we simply multiply every element by the scalar value:
$$
[\hspace{0.2cm}a\hspace{0.5cm}bc\hspace{0.5cm}d\hspace{0.2cm}] * x = [\hspace{0.2cm}a * x\hspace{0.5cm}b * xc * x\hspace{0.5cm}d * x\hspace{0.2cm}]
$$

## Matrix-Vector Multiplication
We map the column of the vector onto each row of the matrix, multiplying each element and summing the result.
$$
[\hspace{0.2cm}a\hspace{0.5cm}bc\hspace{0.5cm}de\hspace{0.5cm}f\hspace{0.2cm}] * [\hspace{0.2cm}xy\hspace{0.2cm}] = [\hspace{0.2cm}a * x + b * yc * x + d * ye * x + f * y\hspace{0.2cm}]
$$
the result is a **vector**. The vector must be the **second** term of the multiplication. The number of **columns** of the matrix must be equal to the number or **rows** of the vector.

an **m x n matrix** multiplied by an **n x 1 vector** results in an **m x 1 vector**.

## Matrix-Matrix Multiplication
We multiply two matrices by breaking it into several vector multiplications and concatenating the result.
$$
[\hspace{0.2cm}a\hspace{0.5cm}bc\hspace{0.5cm}de\hspace{0.5cm}f\hspace{0.2cm}]*[\hspace{0.2cm}w\hspace{0.5cm}xy\hspace{0.5cm}z\hspace{0.2cm}] =
$$
$$[\hspace{0.2cm}a*w+b*y\hspace{0.5cm}a*x+b*zc*w+d*y\hspace{0.5cm}c*x+d*ze*w+f*y\hspace{0.5cm}e*x+f*z\hspace{0.2cm}]
$$
An **m x n matrix** multiplied by an **n x o matrix** results in an **m x o matrix**. In the above example, a 3 x 2 matrix times a 2 x 2 matrix resulted in a 3 x 2 matrix.

to multiply two matrices, the number of **columns** of the first matrix must equal the number of **rows** of the second matrix.

## Matrix Multiplication Properties
- Not commutative. ${A*B \neq B*A}$
- Associative. ${(A*B)*C = A*(B*C)}$

the **identity matrix**, when multiplied by any matrix of the same dimensions, results in the original matrix. It's just like multiplying numbers by 1. The identity matrix simply has 1's on the diagonal(upper left to lower right diagonal) and 0's elsewhere.
$$
[\hspace{0.2cm}1\hspace{0.5cm}0\hspace{0.5cm}00\hspace{0.5cm}1\hspace{0.5cm}00\hspace{0.5cm}0\hspace{0.5cm}1\hspace{0.2cm}]
$$
When multiplying the identity matrix after some matrix (A\*I), the square identity matrix should match the other matrix's **columns**. When multiplying the identity matrix before some other matrix(I\*A), the square identity matrix should match the other matrix's **rows**.

## Inverse and Transpose
the **inverse** of a matrix A is denoted A-1. Multiplying by the inverse results in the identity matrix.

a non square matrix doesn't have an inverse matrix. We can compute inverses of matrices in octave with the pinv(A) function \[1] and in matlab with the inv(A) function. Matrices that don't have an inverse are *singular* or *degenerate*.

the **transposition** of a matrix is like rotating the matrix 90° in clockwise direction and then reversing it. We can compute transposition of matrices in matlab with the transpose(A) function or A':
$$
A = [\hspace{0.2cm}a\hspace{0.5cm}bc\hspace{0.5cm}de\hspace{0.5cm}f\hspace{0.2cm}]\
$$
$$
A^T = [\hspace{0.2cm}a\hspace{0.5cm}c\hspace{0.5cm}eb\hspace{0.5cm}d\hspace{0.5cm}f\hspace{0.2cm}]
$$
in other words:
$$
A_{ij} = A_{ij}^T