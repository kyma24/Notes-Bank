Recursion: method of solving problems that involves breaking a problem down into smaller and smaller subproblems until you get a small enough problem that can be solved trivially. Usually involves a function calling itself.

### Calculating the Sum of a List of Numbers
Here is the code of how we would do this without recursion:
```python
def listSum(numList):
	theSum = 0
	for i in numList:
		theSum = theSum + i
	return theSum

print(listSum([1,3,5,7,9]))
```

Now, pretend that you don't have `while` loops or `for` loops. How would you complete the sum of a list of numbers? If you were a mathematician you might start by recalling that addition is a function that is defined for two parameters, a pair of numbers. To redefine the problem for adding a list to adding pairs of numbers, we could rewrite the list as a fully parenthesized expression:
$$
((((1 + 3) + 5) + 7) + 9)
$$

We can also parenthesize the expression the other way around,
$$
(1 + (3 + (5 + (7 + 9))))
$$

Notice that the innermost set of parentheses, ${(7 + 9)}$, is a problem that we can solve without a loop or any special constructs. In fact, we can use the following sequence of simplifications to compute a final sum.
$$
total = (1 + (3 + (5 + (7 + 9))))
$$
$$
\hspace{1cm}total = (1 + (3 + (5 + 16)))
$$
$$
\hspace{2cm}total = (1 + (3 + 21))
$$
$$
\hspace{3cm}total = (1 + 24)
$$
$$
\hspace{4cm}total = 25
$$

We can turn this into a Python program; start by restating the sum problem in terms of Python lists. We might say that the sum of the list `numList` is the sum of the first element of the list(`numList[0]`), and the sum of the numbers in the rest of the list(`numList[1:]`). To state it in a functional form:
$$
listSum(numList)\hspace{0.2cm}=\hspace{0.2cm}first(numList)\hspace{0.2cm}+\hspace{0.2cm}listSum(rest(numList))
$$

In this equation, ${first(numList)}$ returns the first element of the list and ${rest(numList)}$ returns a list of everything but the first element. This is easily expressed in Python below.
```python
def listSum(numList):
	if len(numList) == 1:
		return numList[0]
	else:
		return numList[0] + listSum(numList[1:])

print(listSum([1,3,5,7,9]))
```

There are a few key ideas in the code to look at. First, on the second line we're checking to see if the list is one element long. This check is crucial and is the escape clause from the function. The sum of a list of length 1 is trivial; it's just the number in the list. Second, on the fifth line the function calls itself. This is the reason why this function is recursive.

Below shows the series of **recursive calls** that are needed to sum the list ${[1,3,5,7,9]}$. Think of this series of calls as a series of simplifications; each time we make a recursive call, we're solving a smaller problem, until we reach the point where the problem can't get any smaller.
![image](https://runestone.academy/runestone/books/published/pythonds/_images/sumlistIn.png)

When we reach the point where the problem is as simple as it can get, we begin to piece together the solutions of each of the small problems until the initial problem is solved. Below shows the additions that are performed as `listSum` works its way backward through the series of calls. When `listSum` returns from the topmost problem, we have the solution to the whole problem.
![image](https://runestone.academy/runestone/books/published/pythonds/_images/sumlistOut.png)

### The Three Laws of Recursion
1. A recursive algorithm must have a **base case**
2. A recursive algorithm must change its state and move toward the base case
3. A recursive algorithm must call itself, recursively

Let's look at each one of these laws in more detail and see how it was used in the `listSum` algorithm. First, a base case is the condition that allows the algorithm to stop recursing. A base case is typically a problem that's small enough to solve directly. In the `listSum` algorithm the base case is a list of length 1.

To obey the second law, we must arrange for a change of state that moves the algorithm toward the base case. A change of state means that some data that the algorithm is using is modified. Usually the data that represents the problem gets smaller in some way. In the `listSum` algorithm the primary data structure is a list, so we must focus the state-changing efforst on the list. Since the base case is a list of length 1, a natural progression toward the base case is to shorten the list. This is exactly what happens in the fifth line of the code when we call `listSum` with a shorter list.

The final law is that the algorithm must call itself, which is pretty straightforward, so there's no need for an explanation.

### Converting an Integer to a String in Any Base
Suppose you want to convert an integer to a string in some base between binary and hexadecimal. For example, convert the iteger 10 to its string representation in decimal as "10", or to its string representation in binary as "1010". While there are many algorithms to solve this problem, including the algorithm used with stacks, the recursive formulation of the problem is very elegant.

Let's look at a concrete example using base 10 and the number 769. Suppose we have a sequence of characters corresponding to the first 10 digits, like `convString = "0123456789"`. It's easy to convert a number less than 10 to its string equivalent by looking it up in the sequence. For example, if the number is 9, then the string is `convString[9]` or `"9"`. If we can arrange to break up the number 769 into three single-digit numbers, 7, 6, and 9, then converting it to a string is simple. A number less than 10 sounds like a good base case.

Knowing what the base is suggests that the overall algorithm will involve three components:
1. Reduce the original number to a series of single-digit numbers
2. Convert the single digit-number to a string using a lookup
3. Concatenate the single-digit strings to gether to form the final result

The next step is to figure out how to change state and make progress toward the base case. Since we are working with an integer, let's consider what mathematical operations might reduce a number. The most likely candidates are division and subtraction. While subtraction might work, it's unclear what we should subtract from what. Integer division with remainders gives us a clear direction. Let's look at what happens if we divide a number by the base we're trying to convert it to.

Using integer division to divide 769 by 10, we get 76 with a remainder of 9. This gives us 2 good results. First, the remainder is a number less than our base that can be converted to a string immediately by lookup. Second, we get a number that's smaller than the original and moves us toward the base case of having a single number less than our base. Now the job is to convert 76 to its string representation. Again we'll use integer division plus remainder to get results of 7 and 6 respectively. FInally, we have reduced the problem to converting 7, which we can do easily since it satisfies the base case condition of ${n < base}$, where ${base = 10}$. The series of operations we have just performed is illustrated below. Notice that the numbers we want to remember are the remainder boxes along the right side of the diagram.

![image](https://runestone.academy/runestone/books/published/pythonds/_images/toStr.png)

Below shows the Python code that implements the algorithm outlined above for any base between 2 and 16.
```python
def toStr(n,base):
	convertString = "0123456789ABCDEF"
	if n < base:
		return convertString[n]
	else:
		return toStr(n//base,base) + convertString[n%base]
		
print(toStr(1453,16))
```

Notice that in the third line we check for the base case where `n` is less than the base we're converting to. When we detect the base case, we stop recursing and simply return the string from the `convertString` sequence. In the sixth line we satisfy both the second and third laws - by making the recursive call and by reducing the problem size - using division.

Let's trace the algorithm again; this time, we'll convert the number 10 to its base 2 string representation(`"1010"`).
![image](https://runestone.academy/runestone/books/published/pythonds/_images/toStrBase2.png)

Above shows that we get the results we're looking for, but it looks like the digits are in the wrong order. The algorithm works correctly because we make the recursive call first on the sixth line, then we add the string representation of the remainder. If we had reversed returning the `convertString` lookup and returning the `toStr` call, ther esulting string would be backward! but by delaying the concatenation operation until after the recursive call has returned, we get the result in the proper order(reminder of stacks).

### Stack Frames: Implementing Recursion
Suppose that instead of concatenating the result of the recursive call to `toStr` with the string form `convertString`, we modified the algorithm to push the strings into a stack instead of making the recursive call.(shown below; assumes that already have stack class written out)
```python
from pythonds.basic import Stack

rStack = Stack()

def toStr(n,base):
	convertString = "0123456789ABCDEF"
	while n > 0:
		if n < base:
			rStack.push(convertString[n])
		else:
			rStack.push(convertString[n % base])
		n = n // base
	res = ""
	while not rStack.isEmpty():
		res = res + str(rStack.pop())
	return res
	
print(toStr(1453,16))
```

Each time `toStr` is called, we push a character on the stack. Returning to the previous example we can see that after the fourth call to `toStr` the stack would look like below. Notice that now we can simply pop the characters off the stack and concatenate them into the final result, `"1010"`.
![../_images/recstack.png](https://runestone.academy/runestone/books/published/pythonds/_images/recstack.png)

The previous example gives us some insight into how Python implements a recursive function call. When a function is called in Python, a **stack frame** is allocated to handle the local variables of the function. When the function returns, the return value is left on top of the stack for the calling function to access. The picture below illustrates the call stack after the return statement on the fourth line.
![../_images/newcallstack.png](https://runestone.academy/runestone/books/published/pythonds/_images/newcallstack.png)

Notice that the call to `toStr(2//2,2)` leaves a return value of `"1"` on the stack. This return value is then used in place of the function call(`toStr(1,2)`) in the expression `"1" + convertString[2%2]`, which will leave the string `"10"` on the top of the stack. In this way, the Python call stack takes the place of the stack used explicitly in the code. In the list summing example, you can think of the return value on the stack taking the place of an accumulator variable.

The stack frames also provide a scope for the variables used by the function. Even though we are calling the same function over and over, each call creates a new scope for the variables that are local to the function.

### Visualizing Recursion
Will be using `turtle` do draw a picture that represents recursion.

Simple example: draw a spiral recursively. Code below shows how it's done: After importing the `turtle` module, create a turtle. When the turtle is created, also creates a new window as the canvas. Next, define the drawSpiral function. The base case for the simple function is when the length of the line we want to draw, as given by the `len` parameter, is reduced to zero or less. If the length of the line is longer than zero we instruct the turtle to go forward by `len` units and then turn right 90 degrees. The recursive step is when we call drawSpiral again w/ a reduced length. At the end of the code will notice that we call the function `myWin.exitonclick()`, which is a handy little method of the window that puts the turtle into a wait mode until you click inside the window, after which the program cleans up and exits.
```python
import turtle

myTurtle = turtle.Turtle()
myWin = turtle.Screen()

def drawSpiral(myTurtle, lineLen):
	if lineLen > 0:
		myTurtle.forward(lineLen)
		myTurtle.right(90)
		drawSpiral(myTurtle,lineLen-5)
		
drawSpiral(myTurtle,100)
myWin.exitonclick()
```

Next program: fractal tree.
Fractals come from a branch of math, and have much in common w/ recursion. The definition of a fractal is that when you look at it the fractal has the same basic shape no matter how much you magnify it. Some examples from nature are the coastlines of continents, snowflakes, mountains, and even trees/shrubs. The fractal nature of many of these natural phenomenon makes it possible for programmers to generate very realistic looking scenery for computer generated movies.

To understand how this is going to work it's helpful to think of how we might describe a tree using a fractal vocabulary. Remember that a fractal is something that looks the same at all different levels of magnification. If we translate this into trees and shrubs then we could say that even a small twig has the same shape and characteristics as a whole tree. Using this idea we could say that a *tree* is a trunk, with a smaller *tree* going off to the right and another smaller *tree* going off to the left. If you think of this definition recursively it means that we'll apply the recursive definition of a tree to both of the smaller left and right trees.

Translation to python code: the code shows how we can use the turtle to generate a fractal tree. Let's look at the code a bit more closely. You'll see that on lines 5 and 7 we are making a recursive call. On line 5 we make the recursive call right after the turtle turns to the right by 20 degrees; this is the right tree mentioned above. Then in line 7 the turtle makes another recursive call, but this time after turning left by 40 degrees. The reason the turtle must turn left by 40 degrees is that it needs to undo the original 20 degree turn to the right and then do an additional 20 degree turn to the left in order to draw the left tree. Also notice that each time we make a recursive call to `tree` we subtract some amount from the `branchLen` parameter; this is to make sure that the recursive trees get smaller and smaller. You should also recognize the initial `if` statement on line 2 as a check for the base case of `branchLen` getting too small.
```python
def tree(branchLen,t):
	if branchLen > 5:
		t.forward(branchLen)
		t.right(20)
		tree(branchLen-15,t)
		t.left(40)
		tree(branchLen-10,t)
		t.right(20)
		t.backward(branchLen)
```

Complete code:
```python
import turtle

def tree(branchLen,t):
	if branchLen > 5:
		t.forward(branchLen)
		t.right(20)
		tree(branchLen-15,t)
		t.left(40)
		tree(branchLen-15,t)
		t.right(20)
		t.backward(branchLen)

def main():
	t = turtle.Turtle()
	myWin = turtle.Screen()
	t.left(90)
	t.up()
	t.backward(100)
	t.down()
	t.color("green")
	tree(75,t)
	myWin.exitonclick()
	
main()
```

Notice how each branch point on the tree corresponds to a recursive call, and notice how the tree is drawn to the right all the way down to its shortest twig. You can see this below. Now, notice how the program works its way back up the trunk until the entire right side of the tree is drawn. You can see the right half of the tree in the second picture below. Then the left side of the tree is drawn, but not by going as far out to the left as possible. Rather, once again the entire right side of the left tree is drawn until we finally make our way out to the smallest twig on the left.
![../_images/tree1.png](https://runestone.academy/runestone/books/published/pythonds/_images/tree1.png)

![../_images/tree2.png](https://runestone.academy/runestone/books/published/pythonds/_images/tree2.png)

### Sierpinski Triangle
Another fractal that exhibits the property of self-similarity is the Sierpinsky Triangle. An example is shown below; the Sierpinski triangle illustrates a three-way recursive algorithm. The procedure for drawing a Sierpinski triangle by hand is simple; start with a single large triangle. Divide this large triangle into four new triangles by connecting the midpoint of each side. Ignoring the middle triangle that you just created, apply the same procedure to each of the three corner triangles. Each time you create a new set of triangles, you recursively apply this procedure to the three smaller corner triangles. You can continue to apply this procedure indefinitely.
![../_images/sierpinski.png](https://runestone.academy/runestone/books/published/pythonds/_images/sierpinski.png)

Because we can continue to apply the algorithm indefinitely, what is the base case? We'll see that the base case is set arbitrarily as the number of times we want to divide the triangle into pieces. Sometimes we call this number the "degree" of a fractal. Each time we make a recursive call, we subtract 1 from the degree until we reach 0. When we reach a degree of 0, we stop making recursive calls. The code that generated the Sierpinski Triangle above is shown in the code below.
```python
import turtle

def drawTriangle(points,color,myTurtle):
    myTurtle.fillcolor(color)
    myTurtle.up()
    myTurtle.goto(points[0][0],points[0][1])
    myTurtle.down()
    myTurtle.begin_fill()
    myTurtle.goto(points[1][0],points[1][1])
    myTurtle.goto(points[2][0],points[2][1])
    myTurtle.goto(points[0][0],points[0][1])
    myTurtle.end_fill()

def getMid(p1,p2):
    return ( (p1[0]+p2[0]) / 2, (p1[1] + p2[1]) / 2)

def sierpinski(points,degree,myTurtle):
    colormap = ['blue','red','green','white','yellow',
                'violet','orange']
    drawTriangle(points,colormap[degree],myTurtle)
    if degree > 0:
        sierpinski([points[0],
                        getMid(points[0], points[1]),
                        getMid(points[0], points[2])],
                   degree-1, myTurtle)
        sierpinski([points[1],
                        getMid(points[0], points[1]),
                        getMid(points[1], points[2])],
                   degree-1, myTurtle)
        sierpinski([points[2],
                        getMid(points[2], points[1]),
                        getMid(points[0], points[2])],
                   degree-1, myTurtle)

def main():
   myTurtle = turtle.Turtle()
   myWin = turtle.Screen()
   myPoints = [[-100,-50],[0,100],[100,-50]]
   sierpinski(myPoints,3,myTurtle)
   myWin.exitonclick()

main()
```

The program follows the ideas outlined above. The first thing `sierpinski`does is draw the outer triangle. Next, there are three recursive calls, one for each of the new corner triangles we get when we connect the midpoints. Once again we make use of the standard turtle module that comes with Python. You can learn about the details of the methods by using `help('turtle')` from the Python prompt.

Look at the code and think abt the order in which the triangles will be drawn. While the exact order of the corners depends on how the initial set is specified, let's assume that the cornders are ordered lower left, top, lower right. Because of the way the `sierpinski` function calls itself, `sierpinski` works its way to the smallest allowed triangle in the lower-left corner, and then begins to fill out the rest of the triangles working back. Then it fills in the triangles in the top corner by working toward the smallest, topmost triangle. Finally, it fills in the lower-right corner, working its way toward the smallest triangle in the lower right.

Sometimes it's helpful to think of a recursive algorithm in terms of a diagram of function calls. The picture below shows that the recursive calls are always made going to the left. The active functions are outlined in black, and the inactive function calls are in gray. The farther you go toward the bottom of the figure, the smaller the triangles. The function finishes drawing one level at a time; once it's finished w/ the bottom left it moves to the bottom middle, and so on.
![../_images/stCallTree.png](https://runestone.academy/runestone/books/published/pythonds/_images/stCallTree.png)

The `sierpinski` function relies heavily on the `getMid` function. `getMid` takes as arguments two endpoints and returns the point halfway between them. In addition, the code has a function that draws a filled triangle using the `begin_fill` and `end_fill` turtle methods.

### Exploring a Maze
We'll be looking at a problem that has relevance to the expanding world of robotics: How do you find your way out of a maze?
![../_images/maze.png](https://runestone.academy/runestone/books/published/pythonds/_images/maze.png)

To make it easier for us we'll assume that the maze is dividied up into "squares". Each square of the maze is either open or occupied by a section of wall. The turtle can only pass through the open squares of the maze. If the turtle bumps into a wall it must try a different direction. The turtle will require a systematic procedure to find its way out of the maze:
- From the starting position we'll first try going North one square and then recursively try the procedure from there
- If we aren't successful by trying a Northern path as the first step then we'll take a step to the South and recursively repeat the procedure.
- If South doesn't work then we'll try a step to the West as the first step and recursively apply the procedure
- If North, South, and West haven't been successful then apply the procedure recursively from a position one step to the East
- If none of the directions work then there's no way to get out of the maze and we fail.

Even though it sounds easy, there are a few details to talk about. Suppose we take the first recursive step by going North. By following the procedure the next step would also be to the North. But if the North is blocked by a wall we must look at the next step of the procedure and try going to the South. Unfortunately that step to the south brings us right back to the starting place. if we apply the recursive procedure from there we'll just go back one step to the North and it'll be a deadloop. So, we must have a strategy to remember where we've been. In this case we'll assume that we have a bag of bread crumbs we can drop along our way. If we take a step in a certain direction and find that there is a bread crumb already on that square, we know that we should immediately back up and try the next direction in the procedure. As we'll see when we look at the code for the algorithm, backing up is as simple as returning from a recursive function call.

As we do for all recursive algorithms, let's review the base cases. Some of them may have already been guessed based on the description in the previous paragraph. In this algorithm, there are four base cases to consider:
1. The turtle has run into a wall. Since the square is occupied by a wall no further exploration can take place
2. The turtle has found a square that has already been explored. We don't want to continue exploring from this position or we'll get into a loop
3. We've found an outside edge, not occupied by a wall. In other words we've found an exit from the maze
4. We've explored a square unsuccessfully in all four directions

For the program to work we'll need to have a way to represent the maze. To make this even more interesting we're going to use the turtle module to draw and explore the maze so that we can watch this algorithm in action. The maze object'll provide the following methods for us to use in writing a search algorithm:
- `__init__` reads in a data file representing a maze, initializes the internal representation of the maze, and finds the starting position for the turtle.
- `drawMaze` draws the maze in a window on the screen
- `updatePosition` updates the internal representation of the maze and changes the position of the turtle in the window
- `isExit` checks to see if the current position is an exit from the maze.

The `Maze` class also overloads the index operator `[]` so that the algorithm can easily access the status of any particular square.

Let's examine the code for the search function which we call `searchFrom`. The code is shown below. Notice that this function takes three parameters: a maze object, the starting row, and the starting column. This is important bc as a recursive function the search logically starts again with each recursive call.
```python
def searchFrom(maze, startRow, startColumn):
    maze.updatePosition(startRow, startColumn)
   #  Check for base cases:
   #  1. We have run into an obstacle, return false
   if maze[startRow][startColumn] == OBSTACLE :
        return False
    #  2. We have found a square that has already been explored
    if maze[startRow][startColumn] == TRIED:
        return False
    # 3. Success, an outside edge not occupied by an obstacle
    if maze.isExit(startRow,startColumn):
        maze.updatePosition(startRow, startColumn, PART_OF_PATH)
        return True
    maze.updatePosition(startRow, startColumn, TRIED)

    # Otherwise, use logical short circuiting to try each
    # direction in turn (if needed)
    found = searchFrom(maze, startRow-1, startColumn) or \
            searchFrom(maze, startRow+1, startColumn) or \
            searchFrom(maze, startRow, startColumn-1) or \
            searchFrom(maze, startRow, startColumn+1)
    if found:
        maze.updatePosition(startRow, startColumn, PART_OF_PATH)
    else:
        maze.updatePosition(startRow, startColumn, DEAD_END)
    return found
```

As you looks through the algorithm you'll see that the first thing the code does(2nd line) is call `updatePosition`. This is simply to help visualize the algorithm so that you can watch exactly how the turtle explores its way through the maze. Next the algorithm checks for the first three of the four base cases: has the turtle run into a wall(5th line)? Has the turtle circled back to a square already explored(8th line)? Has the turtle found an exit(11th line)? If none of these conditions are true then we continue the search recursively.

You'll notice that in the recursive step there are four recursive calls to `searchFrom`. It's hard to predict how many of these recursive calls will be used since they are all connected by `or` statements. If the first call to `searchFrom` returns `True` then none of the last three calls would be needed. You can interpret this as meaning that a step to `(row-1,column)`(or North geographically) is on the path leading out of the maze. If there is not a good path leading out of the maze to the North and then the next recursive call is tried, this one to the South. If the South fails then try West, and finally East. If all four recursive calls return false then we have found a dead end.

The `__init__` method takes the name of a file as its only parameter. This file is a text file that represents a maze by using "+" characters for walls, spaces for open squares, and the letter "S" to indicate the starting position. Below is an example of a maze data file. The internal representation of the maze is a list of lists. Each row of the `mazelist`  instance variable is also a list. This secondary list contains one character per square using the characters described above. For the data file below the internal representation looks like the following:
```python
[ ['+','+','+','+',...,'+','+','+','+','+','+','+'],
  ['+',' ',' ',' ',...,' ',' ',' ','+',' ',' ',' '],
  ['+',' ','+',' ',...,'+','+',' ','+',' ','+','+'],
  ['+',' ','+',' ',...,' ',' ',' ','+',' ','+','+'],
  ['+','+','+',' ',...,'+','+',' ','+',' ',' ','+'],
  ['+',' ',' ',' ',...,'+','+',' ',' ',' ',' ','+'],
  ['+','+','+','+',...,'+','+','+','+','+',' ','+'],
  ['+',' ',' ',' ',...,'+','+',' ',' ','+',' ','+'],
  ['+',' ','+','+',...,' ',' ','+',' ',' ',' ','+'],
  ['+',' ',' ',' ',...,' ',' ','+',' ','+','+','+'],
  ['+','+','+','+',...,'+','+','+',' ','+','+','+']]
  ```
  
  The `drawMaze` method uses this internal representation to draw the initial view of the maze on the screen.
  
  Example Maze Data File
  ```python
  ++++++++++++++++++++++
+   +   ++ ++     +
+ +   +       +++ + ++
+ + +  ++  ++++   + ++
+++ ++++++    +++ +  +
+          ++  ++    +
+++++ ++++++   +++++ +
+     +   +++++++  + +
+ +++++++      S +   +
+                + +++
++++++++++++++++++ +++
```

The `updatePosition` method, as shown in the second code below uses the same internal representation to see if the turtle has run into a wall. It also updates the internal representation with a "." or "-" to indicate that the turtle has visited a particular square or if the square is part of a dead end. In addition, the `updatePosition` method uses two helper methods, `moveTurtle` and `dropBreadCrumb`, to update the view on the screen.

Finally, the `isExit` method uses the current position of the turtle for an exit condition. An exit condition is whenever the turtle has navigated to the edge of the maze, either row zero or column zero, or the far right column or the bottom row.
```python
class Maze:
    def __init__(self,mazeFileName):
        rowsInMaze = 0
        columnsInMaze = 0
        self.mazelist = []
        mazeFile = open(mazeFileName,'r')
        rowsInMaze = 0
        for line in mazeFile:
            rowList = []
            col = 0
            for ch in line[:-1]:
                rowList.append(ch)
                if ch == 'S':
                    self.startRow = rowsInMaze
                    self.startCol = col
                col = col + 1
            rowsInMaze = rowsInMaze + 1
            self.mazelist.append(rowList)
            columnsInMaze = len(rowList)

        self.rowsInMaze = rowsInMaze
        self.columnsInMaze = columnsInMaze
        self.xTranslate = -columnsInMaze/2
        self.yTranslate = rowsInMaze/2
        self.t = Turtle(shape='turtle')
        setup(width=600,height=600)
        setworldcoordinates(-(columnsInMaze-1)/2-.5,
                            -(rowsInMaze-1)/2-.5,
                            (columnsInMaze-1)/2+.5,
                            (rowsInMaze-1)/2+.5)
```

```python
def drawMaze(self):
    for y in range(self.rowsInMaze):
        for x in range(self.columnsInMaze):
            if self.mazelist[y][x] == OBSTACLE:
                self.drawCenteredBox(x+self.xTranslate,
                                     -y+self.yTranslate,
                                     'tan')
    self.t.color('black','blue')

def drawCenteredBox(self,x,y,color):
    tracer(0)
    self.t.up()
    self.t.goto(x-.5,y-.5)
    self.t.color('black',color)
    self.t.setheading(90)
    self.t.down()
    self.t.begin_fill()
    for i in range(4):
        self.t.forward(1)
        self.t.right(90)
    self.t.end_fill()
    update()
    tracer(1)

def moveTurtle(self,x,y):
    self.t.up()
    self.t.setheading(self.t.towards(x+self.xTranslate,
                                     -y+self.yTranslate))
    self.t.goto(x+self.xTranslate,-y+self.yTranslate)

def dropBreadcrumb(self,color):
    self.t.dot(color)

def updatePosition(self,row,col,val=None):
    if val:
        self.mazelist[row][col] = val
    self.moveTurtle(col,row)

    if val == PART_OF_PATH:
        color = 'green'
    elif val == OBSTACLE:
        color = 'red'
    elif val == TRIED:
        color = 'black'
    elif val == DEAD_END:
        color = 'red'
    else:
        color = None

    if color:
        self.dropBreadcrumb(color)
```

```python
def isExit(self,row,col):
     return (row == 0 or
             row == self.rowsInMaze-1 or
             col == 0 or
             col == self.columnsInMaze-1 )

def __getitem__(self,idx):
     return self.mazelist[idx]
```

The complete program is shown in the second listing below. This program uses the data file `maze2.txt` shown below. Note that is is a much more simple example file in that the exit is ver close to the starting position of the turtle.
```python
import turtle

PART_OF_PATH = 'O'
TRIED = '.'
OBSTACLE = '+'
DEAD_END = '-'

class Maze:
    def __init__(self,mazeFileName):
        rowsInMaze = 0
        columnsInMaze = 0
        self.mazelist = []
        mazeFile = open(mazeFileName,'r')
        rowsInMaze = 0
        for line in mazeFile:
            rowList = []
            col = 0
            for ch in line[:-1]:
                rowList.append(ch)
                if ch == 'S':
                    self.startRow = rowsInMaze
                    self.startCol = col
                col = col + 1
            rowsInMaze = rowsInMaze + 1
            self.mazelist.append(rowList)
            columnsInMaze = len(rowList)

        self.rowsInMaze = rowsInMaze
        self.columnsInMaze = columnsInMaze
        self.xTranslate = -columnsInMaze/2
        self.yTranslate = rowsInMaze/2
        self.t = turtle.Turtle()
        self.t.shape('turtle')
        self.wn = turtle.Screen()
        self.wn.setworldcoordinates(-(columnsInMaze-1)/2-.5,-(rowsInMaze-1)/2-.5,(columnsInMaze-1)/2+.5,(rowsInMaze-1)/2+.5)

    def drawMaze(self):
        self.t.speed(10)
        self.wn.tracer(0)
        for y in range(self.rowsInMaze):
            for x in range(self.columnsInMaze):
                if self.mazelist[y][x] == OBSTACLE:
                    self.drawCenteredBox(x+self.xTranslate,-y+self.yTranslate,'orange')
        self.t.color('black')
        self.t.fillcolor('blue')
        self.wn.update()
        self.wn.tracer(1)

    def drawCenteredBox(self,x,y,color):
        self.t.up()
        self.t.goto(x-.5,y-.5)
        self.t.color(color)
        self.t.fillcolor(color)
        self.t.setheading(90)
        self.t.down()
        self.t.begin_fill()
        for i in range(4):
            self.t.forward(1)
            self.t.right(90)
        self.t.end_fill()

    def moveTurtle(self,x,y):
        self.t.up()
        self.t.setheading(self.t.towards(x+self.xTranslate,-y+self.yTranslate))
        self.t.goto(x+self.xTranslate,-y+self.yTranslate)

    def dropBreadcrumb(self,color):
        self.t.dot(10,color)

    def updatePosition(self,row,col,val=None):
        if val:
            self.mazelist[row][col] = val
        self.moveTurtle(col,row)

        if val == PART_OF_PATH:
            color = 'green'
        elif val == OBSTACLE:
            color = 'red'
        elif val == TRIED:
            color = 'black'
        elif val == DEAD_END:
            color = 'red'
        else:
            color = None

        if color:
            self.dropBreadcrumb(color)

    def isExit(self,row,col):
        return (row == 0 or
                row == self.rowsInMaze-1 or
                col == 0 or
                col == self.columnsInMaze-1 )

    def __getitem__(self,idx):
        return self.mazelist[idx]


def searchFrom(maze, startRow, startColumn):
    # try each of four directions from this point until we find a way out.
    # base Case return values:
    #  1. We have run into an obstacle, return false
    maze.updatePosition(startRow, startColumn)
    if maze[startRow][startColumn] == OBSTACLE :
        return False
    #  2. We have found a square that has already been explored
    if maze[startRow][startColumn] == TRIED or maze[startRow][startColumn] == DEAD_END:
        return False
    # 3. We have found an outside edge not occupied by an obstacle
    if maze.isExit(startRow,startColumn):
        maze.updatePosition(startRow, startColumn, PART_OF_PATH)
        return True
    maze.updatePosition(startRow, startColumn, TRIED)
    # Otherwise, use logical short circuiting to try each direction
    # in turn (if needed)
    found = searchFrom(maze, startRow-1, startColumn) or \
            searchFrom(maze, startRow+1, startColumn) or \
            searchFrom(maze, startRow, startColumn-1) or \
            searchFrom(maze, startRow, startColumn+1)
    if found:
        maze.updatePosition(startRow, startColumn, PART_OF_PATH)
    else:
        maze.updatePosition(startRow, startColumn, DEAD_END)
    return found


myMaze = Maze('maze2.txt')
myMaze.drawMaze()
myMaze.updatePosition(myMaze.startRow,myMaze.startCol)

searchFrom(myMaze, myMaze.startRow, myMaze.startCol)
```

### Dynamic Programming
Many programs in CS are written to optimize some value: for example, finding the shortest path between two points, find the line that best fits a set of points, or find the smallest set of objects that satisfies some criteria. There are many strategies that computer scientists use to solve these problems. One of the goals here is to expose you to several different problem-solving strategies. **Dynamic programming** is one strategy for these types of optimization problems.

A classic example of an optimization problem involves making change using the fewest coins. Suppose you're a programmer for a vending machine manufacturer. Your company wants you to streamline effort by giving out the fewest possible coins in change for each transaction. Suppose a customer puts in a dollar bill and purchases an item for 37 cents. What's the smallest number of coins you can use to make change? The answer is six coins: two quarters, one dime, and three pennies. How did we arrive at that answer? We start with the largest coin in our arsenal(a quarter) and use as many of those as possible, then we go to the next lowest coin value and use as many of those as possible. This first approach is called a **greedy method** because we're trying to solve as big a piece of the problem as possible right away.

The greedy method works fine when using U.S. coins, but suppose that the company decides to deploy its vending machines in Lower Elbonia where, in addition to the usual 1, 5, 10, and 25 cent coins they also have a 21 cent coin. In this instance the greedy method fails to find the optimal solution for 63 cents in change. With the addition of the 21 cent coin the greedy method would still find the solution to be six coins. However, the optimal answer is three 21 cent pieces.

Let's look at a method where we could be sure that we would find the optimal answer to the problem. SInce this section is abt recursion, may have guessed that the answer is a recursive solution. Let's start with identifying the base case. If we're trying to make change for the same amt as the value of one of our coins, the answer is easy, one coin.

If the amount doesn't match we have several options. What we want is the minimum of a penny plus the number of coins needed to make change for the original amount minus a penny, or a nickel plus the number of coins needed to make change for the original amount minus five cents, or a dime plus the number of coins needed to make change for the original amount minus ten cents, and so on. So the number of coins needed to make change for the original amount can be computed according to the following:
$$
numCoins = min \begin{cases} 1+numCoins(originalamount-1)\\1+numCoins(originalamount-5)\\1+numCoins(originalamount-10)\\1+numCoins(originalamount-25)\end{cases}
$$

The algorithm for what we have just described is shown below. In the third line we're checking the base case; that is, we're trying to make change in the exact amount of one of our coins. If we don't have a coin equal to the amount of change, we make recursive calls for each different coin value less than the amount of change we're trying to make. The sixth line shows how we filter the list of coins to those less than the current value of change using a list comprehension. The recursive call also reduces the total amount of change we need to make by the value of the coin selected. The recursive call is made in line 7. Notice that on that same line we add 1 to the number of coins to account for the fact that we are using a coin. Just adding one is the same as if we had made a recursive call asking where we satisfy the base case condition immediately.
```python
def recMC(coinValueList,change):
	minCoins = change
	if change in coinValueList:
		return 1
	else:
		for i in [c for c in coinValueList if c <= change]:
			numCoins = 1 + recMC(coinValueList,change-i)
			if numCoins < minCoins:
				minCoins = numCoins
	return minCoins
	
print(recMC([1,5,10,25],63))
```

The trouble with the algorithm above is that it's extremely inefficient. In fact, it takes 67,716,925 recursive calls to find the optimal solution to the four coins, 63 cents problem. To understand the fatal flaw in the approack look at the figure below, which illustrates a small fraction of the 377 function calls needed to find the optimal set of coins to make changes for 26 cents.

Each node in the graph corresponds to a call to `recMC`. The label on the node indicates the amount of change for which we are computing the number of coins. The label on the arrow indicates the coint that we just used. By following the graph we can see the combination of coins that got us to any point in the graph. The main problem is that we're re-doing too many calculations. For example, the graph shows that the algorithm would recalculate the optimal number of coins to make change for 15 cents at least three times. Each fo these computations to find the optimal number of coins for 15 cents itself takes 52 function calls. Clearly we are wasting a lot of time and effort recalculating old results.
![image](https://runestone.academy/runestone/books/published/pythonds/_images/callTree.png)

The key to cutting down on the amount of work we do is to remember some of the past results so we can avoid recomputing results we already know. A simple solution is to store the results for the minimum number of coins in a table when we find them. Then, before we compute a new minimum, we first check the table to see if a result is already known. If there is already a result in the table, we use the value from the table rather than recomputing. Below is a modified algorithm to incoroporate the table-lookup scheme.
```python
 def recDC(coinValueList,change,knownResults):
    minCoins = change
    if change in coinValueList:
       knownResults[change] = 1
       return 1
    elif knownResults[change] > 0:
       return knownResults[change]
    else:
        for i in [c for c in coinValueList if c <= change]:
          numCoins = 1 + recDC(coinValueList, change-i,
                               knownResults)
          if numCoins < minCoins:
             minCoins = numCoins
             knownResults[change] = minCoins
    return minCoins

 print(recDC([1,5,10,25],63,[0]*64))
```

Notice that in line 6 we have added a test to see if the table contains the minimum number of coins for a certain amount of change. If it doesn't, we compute the minimum recursively and store the computed minimum in the table. Using this modified algorithm reduces the number of recursive calls we need to make for the four coin, 63 cent problem to 221 calls.

Although the algorithm above is correct, it looks and feels like a bit of a hack. Also, if we look at the `knownResults`1 lists we can see that there are some holes in the table. In fact the term for what we have done isn't dynamic programming but rather we've improved the performance of the program by using a technique known as "memorization", or more commonly called, "caching".

A truly dynamic programming algorithm will take a more systematic approach to the problem. The dynamic programming solution is going to start with making change for one cent and systematically work its way up to the amount of change we require. This guarantees us that at each step of the algorithm we already know the minimum number of coins needed to make change for any smaller amount.

Let's look at how we would fill in a table of minimum coins to use in making change for 11 cents. The picture below illustrates the process. We start with one cent. The only solution possible in one coin(a penny). The next row shows the minimum for one cent and two cents. Again, the only solution is two pennies. The fifth row is where things get interesting; now we have two options to consider, five pennies or one nickel. How do we decide which is best? We consult the table and see that the number of coins needed to make change for four cents is four, plus one more penny to make five, equals five coins. Or we can look at zero cents plus one more nickel to make five cents equals one coin. Since the minimum of one and five is one we store 1 in the table. Fast forward again to the end of the table and consider 11 cents. The second picture below shows three options that we have to consider:
1. A penny plus the minimum number of coins to make change for ${11-1=10}$ cents (1)
2. A nickel plus the minimum  number of coins to make change for ${11-5=6}$ cents (2)
3. A dime plus the minimum number of coins to make change for ${11-1=1}$ cent (1)

Either option 1 or 3 will give us a total of two coins which is the minimum number of coins for 11 cents.
![image](https://runestone.academy/runestone/books/published/pythonds/_images/changeTable.png)

![image](https://runestone.academy/runestone/books/published/pythonds/_images/elevenCents.png)

The listing below is a dynamic programming algorithm to solve our change-making problem. `dpMakeChange` takes three parameters: a list of valid coin values, the amount of change we want to make, and a list of the minimum number of coins needed to make each value. When the function is done `minCoins` will contain the solution for all values from 0 to the value of `change`.
```python
def dpMakeChange(coinValueList,change,minCoins):
	for cents in range(change+1):
		coinCount = cents
		for j in [c for c in coinValueList if c <= cents]:
			if minCoins[cents-j] + 1 < coinCount:
				coinCount = minCoins[cents-j]+1
		minCoins[cents] = coinCount
	return minCoins[change]
```

Note that `dpMakeChange` is not a recursive function, even though we started with a recursive solution to this problem. It's important to realize that just bc you can write a recursive solution to a problem doesn't mean that it's the best or most efficient solution. The bulk of the work in this function is done by the loop that starts on the fourth line. In this loop we consider using all possible coins to make change for the amount specified by `cents`. Like we did for the 11 cent example above, we remember the minimum value and store it in our `minCoins` list.

Although our making change algorithm does a good job of figuring out the minimum number of coins, it doesn't help us change since we don't keep track of the coins we use. We can easily extend `dpMakeChange` to keep track of the coins used by simply remembering the last coin we add for each entry in the `minCoins` table. If we know the last coin added, we can simply subtract the value of the coin to find a previous entry in the table that tells us the last coin we added to make that amount. We can keep tracing back through the table until we get to the beginning.

Below shows the `dpMakeChange` algorithm modified to keep track fo the coins used, along with a function `printCoins` that walks backward through the table to print out the value of each coin used. This shows the algorithm in action solving the problem for the ppl in Lower Elbonia. The first two lines of `main` set the amount to be converted and create the list of coins used. The next two lines create the lists we need to store the results. `coinsUsed` is a list of the coins used to make change, and `coinCount` is the minimum number of coins used to make change for the amount corresponding to the position in the list.

Notice that the coins we print out come directly from the `coinsUsed` array. For the first call we start at array position 63 and print 21. Then we take ${63-21=42}$ and look at the 42nd element of the list. Once again we find a 21 stored there. Finally, element 21 of the array also contains 21, giving us the three 21 cent pieces.
```python
def dpMakeChange(coinValueList,change,minCoins,coinsUsed):
   for cents in range(change+1):
      coinCount = cents
      newCoin = 1
      for j in [c for c in coinValueList if c <= cents]:
            if minCoins[cents-j] + 1 < coinCount:
               coinCount = minCoins[cents-j]+1
               newCoin = j
      minCoins[cents] = coinCount
      coinsUsed[cents] = newCoin
   return minCoins[change]

def printCoins(coinsUsed,change):
   coin = change
   while coin > 0:
      thisCoin = coinsUsed[coin]
      print(thisCoin)
      coin = coin - thisCoin

def main():
    amnt = 63
    clist = [1,5,10,21,25]
    coinsUsed = [0]*(amnt+1)
    coinCount = [0]*(amnt+1)

    print("Making change for",amnt,"requires")
    print(dpMakeChange(clist,amnt,coinCount,coinsUsed),"coins")
    print("They are:")
    printCoins(coinsUsed,amnt)
    print("The used list is as follows:")
    print(coinsUsed)

main()
```