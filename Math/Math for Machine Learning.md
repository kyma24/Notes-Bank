# Linear Algebra
- part of math which is used the most in ML
- helps in optimizing data
- perform operations on the data

### Scalars
= value
scalars are just values that represent something

suppose have laptop on sale; its price is 50,000 <- scalar value of laptop

buying a laptop and accessories is the addition of the price.
50,000 + 5000 = 55,000
(can perform any operation on scalars)

buying a laptop at 50% discout
50,000/2 = 25,000

A quantity which does not depend on direction is called a **scalar** quantity. **Vector** quantities have two characteristics, a magnitude and a direction. **Scalar** quantities have only a magnitude. When comparing two **vector** quantities of the same type, you have to compare both the magnitude and the direction.
![Scalars and Vectors](https://www.grc.nasa.gov/www/k-12/airplane/Images/vectors.jpg)
![Vector and Scalar - Definition, Vector Addition and Subtraction,  Differences, Solved Problems](https://cdn1.byjus.com/wp-content/uploads/2019/06/scalar-and-vector.png)

two definitions in CS:
1. **Scalar** is a single number or value.

2. In Perl 5 and above and most programming languages a **scalar** is a single value that is not an array. A scalar may be string, integer, or a floating-point. For example, "my $value="example";" is an example of a scalar in Perl, where $value is equal to the string 'example'.

## Vectors
- people in CS can interpret vectors as a list of numbers that represent smth
- people in Physics consider vectors to be a scalar with a direction and it is independent of the plane.
- people in Math take vectors to be a combination of both & generalize

some definitions:
1. In [computer programming](https://www.computerhope.com/jargon/p/programming.htm), a **vector** is either a [pointer](https://www.computerhope.com/jargon/p/pointer.htm) or an [array](https://www.computerhope.com/jargon/a/array.htm) with only one dimension.

2. In mathematics, a **vector** is a quantity with both a magnitude and direction.

if someone tells you that something is moving at 5 mph, that would only be a magnitude. Need to specify direction to make it a vector quantity.

By adding a direction, like East, to 5 mph, we get 5mph due East, which turns into velocity, or a vector.

One way to represent this velocity/vector is to use an arrow all the way to point 5 on the X-axis, pointing East.

It doesn't matter where the vectors starts; it could start at (0, 1) and still be the same vector.

how to represent a vector: make it a letter with a small arrow on top. Use two numbers to represent how much the vector moves in two dimensions. Because the previous one wasn't moving in the vertical direction, it would only be v(with an arrow on top) = (5, 0)
this can also be represented in a matrix, with 5 on top and 0 on the bottom.

Now, have a vector a, specified with (3, 4) or \[5 0] in a matrix.

### Real Coordinate Space
usually represented as something like lR^2, or two-dimensional real coordinate space. This is all possible real-valued 2-tuples.

a tuple is an ordered list of numbers, so a 2-tuple is an ordered list of 2 numbers. the matrices that represent vectors (i.e. \[5 0]) are also 2-tuples. so all real-valued 2-tuples would just be the values are real numbers.

the lR^2 notation isn't the only way to express this. It could also be lR^3, or the 3D real coordinate space, i.e. vector x = \[0 0 0\] or b = \[-1 5 3\]

if make a vector with any imaginary number in the matrix, then it is not a real-value tuple.

there is no limit to the number of dimensions, though it may get harder to visualize.

usually represented with lRn for however many dimensions needed/wanted.


### Vector Addition (Dot Product)
- it is the total work achieved through both vectors in a quantified form:
![Vector Addition (solutions, examples, videos)](https://www.onlinemathlearning.com/image-files/add-vectors.png)

### Scalar Multiplication
when a vector is multiplied with a scalar, it either grows or shrinks.
positive or negative scalars either grow or shrink the vector
![Scalar Multiplication of Vectors (examples, solutions, videos, worksheets,  activities)](https://www.onlinemathlearning.com/image-files/multiply-vector-scalar.png)

given the vector a = \[2 1], we want to multiply it by a scalar, such as 3.
this is essentially the same thing as saying 3 * \[2 1].

First instinct thought is multiply each element in the matrix by 3, distributing the scalar to the elements.

this essentially scales the vector up and grew it by 3(explaining the name "scalar"). The scalar only changed the magnitude in this case, but didn't change the direction.

however, when multiplying by a negative number, i.e. -1 * a, would multiply each of the components by -1, which turns it into \[-2 -1]. If starting at the origin, would flip the direction. The magnitude didn't change bc multiplied by -**1**, but inverted the direction of the vector. If doing -2, then it would scale the -1 vector by 2.

### Projection
the shadow a vector places on the other vector
can help in analyzing features of unknown vector
![Vector Projections - Mathonline](http://mathonline.wdfiles.com/local--files/vector-projections/Screen%20Shot%202014-12-14%20at%2012.42.18%20PM.png)

## Matrices
composition of numbers, symbols, or expressions in rectangular array
use matrices to convert expressions of the vector forms to arrays
they make operations easier as that is what we work with on computers.
![How to Understand the Basics of Matrices: 12 Steps (with Pictures)](https://www.wikihow.com/images/thumb/1/1f/Matrix-examples.png/728px-Matrix-examples.png)
![Types Of Matrices (video lessons, examples and solutions)](https://www.onlinemathlearning.com/image-files/types-of-matrices.png)

### Matrix Addition
adding corresponding elements of the 2 matrices
both matrices need to be of same **order** to work: the number of rows and the number of columns
![Matrix addition & subtraction (article) | Khan Academy](https://cdn.kastatic.org/googleusercontent/1zwnERArTuwdXjBNj_s0PNa1oE58dMWqy_NTPUW2o0a2FtFbk1SAYRdHRTiLAR5FjEaN9-pdCqZscJ0qkPYiW8rk)

### Matrix Subtraction
subtract corresponding elements in the operation
both matrices need to be of same order, again
![Matrices](https://www.mathsisfun.com/algebra/images/matrix-subtraction.gif)

### Matrix Multiplication
multiplying rows of Matrix 1 with the columns of Matrix 2.
the rows of Matrix 1 need to be equal to column of Matrix 2 for it to work
![Week Ending 2/15/13 - Cortez J](http://www.mathsisfun.com/algebra/images/matrix-multiply-order.gif)
![How to Multiply Matrices](https://www.mathsisfun.com/algebra/images/matrix-multiply-c.svg)

### Transpose
interchanging rows and columns of a matrix
can be used to flip the dimensions
(if working with pictures, can analyze more info when flip dimensions)
![How to transpose a matrix in Java? Example Tutorial | Java67](https://2.bp.blogspot.com/-8LzbJv0zB3A/WAzRQbxP5eI/AAAAAAAAHYU/MEqPV8JxtLMCSGSQ-0UKZSYlUN3jALZaQCLcB/w1200-h630-p-k-no-nu/Java%2BProgram%2Bto%2BTranspose%2Ba%2BMatrix%2B.png)

### Determinant of Matrix
scalar value of matrix
gives you the product of **Eigen Values** of the matrix
![The determinant of a 3 x 3 matrix (General & Shortcut Method) | StudyPug](https://dcvp84mxptlac.cloudfront.net/diagrams2/equation-5-shortcut-method-to-obtain-the-determinant-of-a-3x3-matrix.png)
![Determinant of 2x2 Matrix - ChiliMath](https://www.chilimath.com/wp-content/uploads/2018/12/A1-solution-1.png)
+ [Calculating determinant of matrix using NumPy](https://www.geeksforgeeks.org/how-to-calculate-the-determinant-of-a-matrix-using-numpy/)

### Inverse of Matrix
matrix when ultiplied with inverse gives an **Identity Matrix**
inverse helps apply transformations efficiently
some matrices don't have an inverse, which means that the info they hold isn't reliable and very noisy.
(vector comes in other direction)
![Inverse Matrix - Methods, Formulas & Solved Examples of 2x2 and 3x3 matrices](https://cdn1.byjus.com/wp-content/uploads/2018/04/inverse-matrix-3.jpg)
![Inverse of a 2x2 Matrix - ChiliMath](https://www.chilimath.com/wp-content/uploads/2017/03/ex1_sol1.gif)

## Vector as Matrix
- vectors can be easily translated to matrix
- make it easy to apply operations on the data
- well-known operations like scaling, rotation, and shearing
![Matrix Representation of 2D Transformation - javatpoint](https://static.javatpoint.com/tutorial/computer-graphics/images/matrix-representation-of-2d-transformation.png)
![Coordinate Transformations](https://lahosken.san-francisco.ca.us/manual/geos/Graphics/Environment/Environment_9_matrixStandard.gif)

### Scaling
![2 d transformations by amit kumar (maimt)](https://image.slidesharecdn.com/2dtransformationsbyamitkumarmaimt-110929052806-phpapp01/95/2-d-transformations-by-amit-kumar-maimt-14-728.jpg?cb=1317275105)
![2 D Transformations](https://image.slidesharecdn.com/2dtransformations-1209392936282615-8/95/2-d-transformations-22-728.jpg?cb=1209367951)

- matrices can help solve equations and obtain solutions
- there are 2 ways of solving:
	- row echelon method
	- inverse method