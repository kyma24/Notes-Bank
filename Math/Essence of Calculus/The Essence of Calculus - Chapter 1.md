Area of circle: ${πR^2}$
Why?
The deduction can lead to three sub-discoveries: integrals, derivatives, and the fact that they're opposites.

But let's start off simply. Let's say we have a circle with radius 3. trying to figure out area, so try to cut up circle in a way.

You come across one pattern: trying to cut a circle into many concentric rings. This should seem promising bc it respects the symmetry of the circle.

Take one of the rings with some inner radius 0 < r < 3. If can find a nice expression for the area of rings like this one & add it up, then might lead to the understanding of full circle area.

Maybe start by straightening out that circle, and try to figure out what the shape is. For simplicity, just approximate as a rectangle. The width of that rectangle is just the circumference of the original ring, which is 2πr.

![Calculus proof for the area of a circle - Mathematics Stack Exchange](https://i.stack.imgur.com/sTePn.gif)

Now, what's the thickness? Well, it depends on how thinly you cut up the circle. Let's call it ${dr}$, for a tiny difference in the radius from one ring to the next.

Now you've broken up the area of the circle into many rings. We can plot the values of each ${r}$ on a number line that stretches from 0 to just under 3. The spacing between each point will be the width of each ring. A nice way to think about the rectangles approximating the area is to stack them all in their corresponding spots vertically to form an ascending graph that looks somewhat like this, minus the first and last bar:
![Essence of Calculus – Pierre-Yves Vandenbussche](https://lh3.googleusercontent.com/proxy/R7k9KLTVWsJqxhqHthlx8k8YKi9hz_a_C2d3Pok_isQfWFAlGHg4sxspe2as19Z5wBvGEQ6pOItP5IOuUhHrNtcA6gjbfQN7TDAeT0YYDC0XnsLxVmbXx5jZgA)

A nice way to think abt this setup is to draw the graph of 2πr, which is a straight line that has a slope 2π. Each of the rectangles extends up to the line so it just barely touches it. As ${dr}$ gets smaller, the approximation gets more accurate.

After decreasing ${dr}$ to an infinitesimally small value, what you'll notice is that it's going to form an area under the graph of ${2πr}$, a right triangle that has the base of 3 and the height of ${2π\cdot 3}$. This works out to be ${πR^2}$.

This example really cuts deep into what calculus really is about.

- sum = aggregate area of the rectangles

Imagine you were to figure out the area under some other function, such as a parabola. You can fix the starting point, and make the endpoint of the area section vary. The function ${A(x)}$ to find the area underneath the curve in that location is called an **integral** of the function.

Something to notice: when you slightly change ${x}$ by some tiny nudge called ${dx}$, look at the change in area represented with a sliver in the graph that's going to be called ${dA}$. That sliver can be pretty well approximated with a rectangle, with its height as ${x^2}$ and its width as ${dx}$. As you lessen the value of ${dx}$, the more that sliver looks like an actual rectangle.

This gives an interesting way of how the integral function ${A(x)}$ is related to ${x^2}$. A change to the output A, or ${dA}$, is about equal to ${x^2}$, where ${x}$ is whatever input you started at, times ${dx}$.

Or rearrange this to ${\frac{dA}{dx}≈x^2}$; the tiny change in ${A}$ to the tiny change in ${x}$ that caused it, is approximately what ${x^2}$ is at that point.

We still don't know what the function ${A(x)}$ is, but we do know a property that this mystery function must have, e.g. between two points ${x-3}$ and ${x-3.001}$, for instance:
$$
\frac{A(3.001) - A(3)}{0.001} ≈ x^2
$$

This property is true at all inputs.

Any function defined as the area under some graph also has this property.

Here, we're stumbling upon another big idea in calculus: derivatives. Derivatives are whatever value this ratio approaches as ${dx}$ gets smaller and smaller. It roughly measures how sensitive a function is to small changes in its input.

This back and forth between integrals and derivatives where the derivative of a function for the area under the graph gives you back the function defining the graph itself is called the "Fundamental theorem of calculus", which shows how derivatives and integrals are opposites of each other.