## Linear Regression with Multiple Variables
Linear regression w/ multiple variables is also known as "multivariate linear regression".

We now introduce notation for equations where we can have any number of input variables.

${x_{j}^{(i)} = }$ value of feature ${j}$ in the ${i^{th}}$ training example

${x^{(i)} = }$ the column vector of all the feature inputs of the ${i^{th}}$ training example

${m = }$ the number of training examples

${n = |x^{(i)}|; }$  (the number of features)


Now define the **multivariate form** of the hypothesis function as follows, accommodating these multiple features:
$$
h_{θ}(x) = [\hspace{0.2cm}θ_{0}\hspace{0.5cm}θ_{1}\hspace{0.5cm}...\hspace{0.5cm}θ_{n}\hspace{0.2cm}]\begin{bmatrix} x_{0} \\ x_{1} \\ \vdots \\ x_{n} \end{bmatrix} = θ^{T}x
$$

This is a vectorization of the hypothesis function for 1 training example. Note that for convenience reasons, ${x_{0}^{(i)} = 1}$ is assumed for ${(i ∈ 1, ..., m)}$

\[**Note**: So that we can do matrix operations with theta and x, we will set ${x_{0}^{(i)} = 1}$, for all values of ${i}$. This makes the two vectors 'theta' and ${x_{(i)}}$ match each other element-wise(that is, have the same number of elements: ${n + 1}$)]


The training examples are stored in X row-wise, like such:
$$
X = \begin{bmatrix} x_{0}^{(1)} & x_{1}^{(1)} \\ x_{0}^{(2)} & x_{1}^{(2)} \\ x_{0} ^{(3)} & x_{1}^{(3)}\end{bmatrix}, θ = \begin{bmatrix} θ_{0} \\ θ_{1}\end{bmatrix}
$$

You can calculate the hypothesis as a column vector of size (m x 1) with:
$$
h_{θ}(X) = Xθ
$$

**Note: For the rest of these notes, and other lecture notes, X will represent a matrix of training examples ${x_{(i)}}$ stored row-wise.**

### Cost Function
For the parameter vector θ (of type ${\rm I\!R^{n+1}}$ or in ${\rm I\!R^{(n+1)\times1}}$), the cost function is:
$$
J(θ) = \frac{1}{2m}\sum\limits_{i=1}^{m}(h_{θ}(x^{(i)}) - y^{(i)})^{2}
$$

the vectorized version is:
$$
J(θ) = \frac{1}{2m}(Xθ - \overrightarrow{y})^{T}(Xθ - \overrightarrow{y})
$$

Where ${\overrightarrow{y}}$ denotes the vector of all y values.

### Gradient Descent for Multiple Variables
The gradient descent equation itself is generally the same form; we just have to repeat it for the 'n' features:
$$
repeat\hspace{0.2cm}until\hspace{0.2cm}convergence:\hspace{0.2cm} \{
$$
$$
θ_{0} := θ_{0} - α\frac{1}{m}\sum\limits_{i=1}^{m}(h_{θ}(x^{(i)})-y^{(i)})\cdot x_{0}^{(i)}
$$
$$
θ_{1} := θ_{1} - α\frac{1}{m}\sum\limits_{i=1}^{m}(h_{θ}(x^{(i)})-y^{(i)})\cdot x_{1}^{(i)}
$$
$$
θ_{2} := θ_{2} - α\frac{1}{m}\sum\limits_{i=1}^{m}(h_{θ}(x^{(i)})-y^{(i)})\cdot x_{2}^{(i)}
$$
$$
...
$$
$$
\}
$$

In other words:
$$
repeat\hspace{0.2cm}until\hspace{0.2cm}convergence:\hspace{0.2cm} \{
$$
$$
θ_{j} := θ_{j} - α\frac{1}{m}\sum\limits_{i=1}^{m}(h_{θ}(x^{(i)})-y^{(i)})\cdot x_{j}^{(i)}\hspace{1cm}for\hspace{0.2cm} j:=0..n
$$
$$
\}
$$

### Matrix Notation
The **Gradient Descent** rule can be expressed as:
$$
θ := θ - α∇ J(θ)
$$

Where ${∇ J(θ)}$ is a column vector of the form:
$$
∇ J(θ) = [\frac{∂J(θ)}{∂θ_{0}}\frac{∂J(θ)}{∂θ_{1}}\hspace{0.2cm}\vdots\hspace{0.2cm}\frac{∂J(θ)}{∂θ_{n}}]
$$

The j-th component of the gradient is the summation of the product of two terms:
$$
\frac{∂J(θ)}{∂θ_{j}}\hspace{1cm}= \frac{1}{m}\sum\limits_{i=1}^{m}(h_{θ}(x^{(i)}) - y^{(i)})\cdot x_{j}^{(i)}
$$
$$
\hspace{2.5cm}=\frac{1}{m}\sum\limits_{i=1}^{m}x_{j}^{(i)}\cdot (h_{θ}(x^{(i)}) - y^{(i)})
$$

Sometimes, the summation of the product of two terms can be expressed as the product of two vectors.

Here, ${x_{j}^{(i)}}$, for i = 1, ..., m, represents the m elements of the j-th column, ${\overrightarrow{x}_{j}}$, of the training set X.

The other term ${(h_{θ}(x^{(i)}) - y^{(i)})}$ is a vector of the deviations between the predictions ${h_{θ}(x^{(i)})}$ and the true values ${y^{(i)}}$. Rewriting ${\frac{∂J(θ)}{∂θ_{j}}}$, we have:
$$
\frac{∂J(θ)}{∂θ_{j}} \hspace{1cm} = \frac{1}{m}\overrightarrow{x}_{j}^{T}(Xθ - \overrightarrow{y})
$$
$$
∇ J(θ)\hspace{1cm} = \frac{1}{m}X^{T}(Xθ - \overrightarrow{y})
$$

Finally, the matrix notation(vectorized) of the Gradient Descent rule is:
$$
θ := θ - \frac{α}{m}X^{T}(Xθ - \overrightarrow{y})
$$

## Feature Normalization
We can speed up gradient descent by having each of the input values in roughly the same range. This is because θ will descend quickly on small ranges and slowly on large ranges, and so will oscillate inefficiently down to the optimum when the variables are very uneven.

The way to prevent this is to modify the ranges of the input variables so that they are all roughly the same. Ideally:
$$
-1 \le x_{(i)} \le 1
$$
or
$$
-0.5 \le x_{(i)} \le 0.5
$$

These aren't exact requirements; we are only trying to speed things up. The goal is to get all input variables into roughly one of these ranges, take or give a few.

Two techniques to help with this are called **feature scaling** and **mean normalization**. Feature scaling involves dividing the input values by the range(i.e. the maximum value minus the minimum value) of the input variable, resulting in a new range of just 1. Mean normalization involves subtracting the average value for an input variable from the values for that input variable, resulting in a new average value for the input variable of just zero. To implement both of these techniques, adjust your input values as shown in this formula:
$$
x_{i} := \frac{x_{i} - μ_{i}}{s_{i}}
$$
Where ${μ_{i}}$ is the **average** of all the values for feature ${(i)}$ and ${s_{i}}$ is the range of values (max - min), or ${s_{i}}$ is the standard deviation.

Note that dividing by the range, or dividing by the standard deviation, give different results.

Example: ${x_{i}}$ is housing prices with range of 100 to 2000, with a mean value of 1000. Then,
$$
x_{i} := \frac{price - 1000}{1900}
$$

## Gradient Descent Tips
**Debugging Gradient Descent.** Make a plot with *number of iterations* on the x-axis. Now plot the cost function, J(θ) over the number of iterations of gradient descent. if J(θ) every increases, then you probably need to decrease α.

**Automatic convergence test.** Delcare convergence if J(θ) decreases by less than E in one iteration, where E is some small value such as 10-3. However in practice it's difficult to choose this threshold value.

It has been proven that if learning rate α is sufficiently small, then J(θ) will decrease on every iteration. It is suggested to decrease α by multiples of 3.

## Features and Polynomial Regression
We can improve the features and the form of the hypothesis function in a couple different ways.

We can **combine** multiple features into one. For example, we can combine ${x_{1}}$ and ${x_{2}}$ into a new feature ${x_{3}}$ by taking ${x_{1}\cdot x_{2}}$.

### Polynomial Regression
the hypothesis function doesn't need to be linear/a straight line if that does not fit the data well.

We can **change the behavior or curve** of the hypothesis function by making it a quadratic, cubic or square root function(or any other form).

i.e. if the hypothesis function is ${h_{θ}(x) = θ_{0} + θ_{1}x_{1}}$ then we can create additional features based on ${x_{1}}$, to get the quadratic function ${h_{θ}(x) = θ_{0} + θ_{1}x_{1} + θ_{2}x_{1}^{2}}$ or the cubic function ${h_{θ}(x) = θ_{0} + θ_{1}x_{1} + θ_{2}x_{1}^{2} + θ_{3}x_{1}^{3}}$.

In the cubic version, we have created new features ${x_{2}}$ and ${x_{3}}$ where ${x_{2} = x_{1}^{2}}$ and ${x_{3} = x_{1}^{3}}$.

To make it a square root function, we could do: ${h_{θ}(x) = θ_{0} + θ_{1}x_{1} + θ_{2}\sqrt{x_{1}}}$

One important thing to keep in mind is, if you choose your features this way then feature scaling becomes very important.

e.g. if ${x_{1}}$ has a range 1 - 1000 then the range of ${x_{1}^{2}}$ becomes 1 - 1000000 and that of ${x_{1}^{3}}$ becomes 1 - 1000000000.

## Normal Equation
The **"Normal Equation"** is a method of finding the optimum theta **without iteration**.
$$
θ = (X^{T} X)^{-1} X^{T}y
$$
There is **no need** to do feature scaling with the normal equation.

Mathematical proof of the Normal Equation requires knowledge of [linear algebra](https://en.wikipedia.org/wiki/Linear_least_squares_(mathematics)) and is fairly involved, so no need to worry about the [details](http://eli.thegreenplace.net/2014/derivation-of-the-normal-equation-for-linear-regression).

The following is a comparison of gradient descent and the normal equation:

Gradient Descent | Normal Equation
------------ | ------------
Need to choose alpha | No need to choose alpha
Needs many iterations | No need to iterate
O(${kn^{2}}$) | O(${n^{3}}$), need to calculate inverse of ${X^{T}X}$
Works well when n is large | Slow if n is very large

With the normal equation, computing the inversion has complexity ${O(n^{3})}$. So if we have a very large number of features, the normal equation will be slow. In practice, when n exceeds 10,000 it might be a good time to go from a normal solution to an iterative process.

### Normal Equation Noninvertibility
When implementing the normal equation in **octave** we want to use the 'pinv' function rather than 'inv'.

${X^{T}X}$ may be **noninvertible**. The common causes are:
- Redundant features, where two features are very closely related(i.e. they are linearly dependent)
- Too many features(e.g. m ≤ n). In this case, delete some features or use "regularization"
Solutions to the above problems include deleting a feature that is linearly dependent with another or deleting one or more features when there are too many.

## ML: Octave Tutorial
## Basic Operations
```matlab
%% Change Octave prompt  
PS1('>> ');
%% Change working directory in windows example:
cd 'c:/path/to/desired/directory name'
%% Note that it uses normal slashes and does not use escape characters for the empty spaces.

%% elementary operations
5+6
3-2
5*8
1/2
2^6
1 == 2 % false
1 ~= 2 % true.  note, not "!="
1 && 0
1 || 0
xor(1,0)


%% variable assignment
a = 3; % semicolon suppresses output
b = 'hi';
c = 3>=1;

% Displaying them:
a = pi
disp(a)
disp(sprintf('2 decimals: %0.2f', a))
disp(sprintf('6 decimals: %0.6f', a))
format long
a
format short
a


%%  vectors and matrices
A = [1 2; 3 4; 5 6]

v = [1 2 3]
v = [1; 2; 3]
v = 1:0.1:2   % from 1 to 2, with stepsize of 0.1. Useful for plot axes
v = 1:6       % from 1 to 6, assumes stepsize of 1 (row vector)

C = 2*ones(2,3) % same as C = [2 2 2; 2 2 2]
w = ones(1,3)   % 1x3 vector of ones
w = zeros(1,3)
w = rand(1,3) % drawn from a uniform distribution 
w = randn(1,3)% drawn from a normal distribution (mean=0, var=1)
w = -6 + sqrt(10)*(randn(1,10000));  % (mean = -6, var = 10) - note: add the semicolon
hist(w)    % plot histogram using 10 bins (default)
hist(w,50) % plot histogram using 50 bins
% note: if hist() crashes, try "graphics_toolkit('gnu_plot')" 

I = eye(4)   % 4x4 identity matrix

% help function
help eye
help rand
help help
```

## Moving Data Around
*Data files used in this section:* [featuresX.dat](https://raw.githubusercontent.com/tansaku/py-coursera/master/featuresX.dat), [priceY.dat](https://raw.githubusercontent.com/tansaku/py-coursera/master/priceY.dat)
```matlab
%% dimensions
sz = size(A) % 1x2 matrix: [(number of rows) (number of columns)]
size(A,1) % number of rows
size(A,2) % number of cols
length(v) % size of longest dimension


%% loading data
pwd   % show current directory (current path)
cd 'C:\Users\ang\Octave files'  % change directory 
ls    % list files in current directory 
load q1y.dat   % alternatively, load('q1y.dat')
load q1x.dat
who   % list variables in workspace
whos  % list variables in workspace (detailed view) 
clear q1y      % clear command without any args clears all vars
v = q1x(1:10); % first 10 elements of q1x (counts down the columns)
save hello.mat v;  % save variable v into file hello.mat
save hello.txt v -ascii; % save as ascii
% fopen, fread, fprintf, fscanf also work  [[not needed in class]]

%% indexing
A(3,2)  % indexing is (row,col)
A(2,:)  % get the 2nd row. 
        % ":" means every element along that dimension
A(:,2)  % get the 2nd col
A([1 3],:) % print all  the elements of rows 1 and 3

A(:,2) = [10; 11; 12]     % change second column
A = [A, [100; 101; 102]]; % append column vec
A(:) % Select all elements as a column vector.

% Putting data together 
A = [1 2; 3 4; 5 6]
B = [11 12; 13 14; 15 16] % same dims as A
C = [A B]  % concatenating A and B matrices side by side
C = [A, B] % concatenating A and B matrices side by side
C = [A; B] % Concatenating A and B top and bottom
```

## Computing on Data
```matlab
%% initialize variables
A = [1 2;3 4;5 6]
B = [11 12;13 14;15 16]
C = [1 1;2 2]
v = [1;2;3]

%% matrix operations
A * C  % matrix multiplication
A .* B % element-wise multiplication
% A .* C  or A * B gives error - wrong dimensions
A .^ 2 % element-wise square of each element in A
1./v   % element-wise reciprocal
log(v)  % functions like this operate element-wise on vecs or matrices 
exp(v)
abs(v)

-v  % -1*v

v + ones(length(v), 1)  
% v + 1  % same

A'  % matrix transpose

%% misc useful functions

% max  (or min)
a = [1 15 2 0.5]
val = max(a)
[val,ind] = max(a) % val -  maximum element of the vector a and index - index value where maximum occur
val = max(A) % if A is matrix, returns max from each column

% compare values in a matrix & find
a < 3 % checks which values in a are less than 3
find(a < 3) % gives location of elements less than 3
A = magic(3) % generates a magic matrix - not much used in ML algorithms
[r,c] = find(A>=7)  % row, column indices for values matching comparison

% sum, prod
sum(a)
prod(a)
floor(a) % or ceil(a)
max(rand(3),rand(3))
max(A,[],1) -  maximum along columns(defaults to columns - max(A,[]))
max(A,[],2) - maximum along rows
A = magic(9)
sum(A,1)
sum(A,2)
sum(sum( A .* eye(9) ))
sum(sum( A .* flipud(eye(9)) ))


% Matrix inverse (pseudo-inverse)
pinv(A)        % inv(A'*A)*A'
```

## Plotting Data
```matlab
%% plotting
t = [0:0.01:0.98];
y1 = sin(2*pi*4*t); 
plot(t,y1);
y2 = cos(2*pi*4*t);
hold on;  % "hold off" to turn off
plot(t,y2,'r');
xlabel('time');
ylabel('value');
legend('sin','cos');
title('my plot');
print -dpng 'myPlot.png'
close;           % or,  "close all" to close all figs
figure(1); plot(t, y1);
figure(2); plot(t, y2);
figure(2), clf;  % can specify the figure number
subplot(1,2,1);  % Divide plot into 1x2 grid, access 1st element
plot(t,y1);
subplot(1,2,2);  % Divide plot into 1x2 grid, access 2nd element
plot(t,y2);
axis([0.5 1 -1 1]);  % change axis scale

%% display a matrix (or image) 
figure;
imagesc(magic(15)), colorbar, colormap gray;
% comma-chaining function calls.  
a=1,b=2,c=3
a=1;b=2;c=3;
```

## Control statements: for, while, if statements
```matlab
v = zeros(10,1);
for i=1:10, 
    v(i) = 2^i;
end;
% Can also use "break" and "continue" inside for and while loops to control execution.

i = 1;
while i <= 5,
  v(i) = 100; 
  i = i+1;
end

i = 1;
while true, 
  v(i) = 999; 
  i = i+1;
  if i == 6,
    break;
  end;
end

if v(1)==1,
  disp('The value is one!');
elseif v(1)==2,
  disp('The value is two!');
else
  disp('The value is not one or two!');
end
```

## Functions
To create a function, type the function code in a text editor(e.g. gedit or notepad), and save the file as "functionName.m"

Example function:
```matlab
function y = squareThisNumber(x)

y = x^2
```

To call the function in Octave, do either:
1) Navigate to the directory of the functionName.m file and call the function:
	```matlab
	% Navigate to directory:
	cd /path/to/function
	
	% Call the function:
	functionName(args)
	```
2) Add the directory of the function to the load path and save it:
	```matlab
	% To add the path for the current session of Octave:
	addpath('/path/to/function/')
	
	% To rememer the path for future sessions of Octave, after executing addpath above, also do:
	savepath
	```

Octave's functions can return more than one value:
```matlab
function [y1, y2] = squareandCubeThisNo(x)
y1 = x^2
y2 = x^3
```

Call the above function this way:
```matlab
[a, b] = squareandCubeThisNo(x)
```

## Vectorization
Vectorization is the process of taking code that relies on **loops** and converting it into **matrix operations**. It is more efficient, more elegant, and more concise.

As an example, let's compute the prediction from a hypothesis. Theta is the vector of fields for the hypothesis and x is a vector of variables.

With loops:
```matlab
prediction = 0.0;
for j = 1:n+1,
	prediction += theta(j) * x(j);
end;
```

With vectorization:
```matlab
prediction = theta' * x;
```

If you recall the definition of multiplying vectors, you'll see that this one operation does the element-wise multiplication and overall sum in a very concise notation.