normal Δ -> handling 2D cases(2 variables, ${f(x)}$ and ${x}$)
$$
f'(x) = \frac{d}{dx} f(x) = \frac{f(x + Δx) - f(x)}{(x + Δx) - x} = \frac{f(x + Δx) - f(x)}{Δx}
$$

partial ∂ -> handling 3D cases(more than 2 variables)
$$
\frac{∂}{∂x} f(x, y, z) = \frac{f(x + Δx, y, z) - f(x, y, z)}{Δx}
$$
always **focus on one variable**.
in this case, the focus is on x. It can become y or z or f(x, y, z) as well.

w.r.t -> with respect to

With respect to three-dimensional graphs, you can picture the partial derivative ${\frac{∂f}{∂x}}$ by slicing the graph of ${f}$ with a plane representing a constant ${y}$ value and measuring the slope of the resulting curve along the cut.
    

![Intersecting y=0 plane with the graph](https://cdn.kastatic.org/ka-perseus-images/cfa052fd6e96274894ff46cc33a8302a92e1c078.png)

### What is a Partial Derivative?
ordinary derivative: ${\frac{df}{dx}}$
The notation for the derivative can be interpreted as follows:
- Interpret ${dx}$ as "a very tiny change in ${x}$"
- Interpret ${df}$ as "a very tiny change in the output of ${f}$", where it is understood that this tiny change is whatever results from the tiny change ${dx}$ to the input.

when applying to the graph of ${f}$, you can interpret this "ratio" ${\frac{df}{dx}}$ as the rise-over-run slope of the graph of ${f}$, which depends on the point where you started.
  
![Interpretation of $\\dfrac{df}{dx}$ in a single variable function.](https://cdn.kastatic.org/ka-perseus-graphie/a7e8b9b2b478569541a7ff9e90ebab6a68539a1e.svg)

### How does this work for multivariable functions?
Consider some function with a two-dimensional input and a one-dimensional output.
$$
f(x, y) = x^{2} - 2xy
$$
We could write the same expression, ${\frac{df}{dx}}$, and interpret it the same way:
- ${dx}$ can still represent a tiny change in the variable ${x}$, which is now just one component of the input
- ${df}$ can still represent the resulting change to the output of the function ${f(x, y)}$
However, this ignores the fact that there is another input variable ${y}$. The input space now has multiple dimensions, so we can change the input in many directions other than the ${x}$-direction. For example, what about changing ${y}$ slightly by some small value ${dy}$? Now if we re-interpret ${df}$ to represent the tiny change to the function that this ${dy}$ shift brings about, we would have a different derivative ${\frac{df}{dy}}$.

![Indication that the input of a multivariable function can change in many directions.](https://cdn.kastatic.org/ka-perseus-images/16558e3743e958f98bdd4b33851e0db2969d9e81.png)

Neither one of these derivatives tells the full story of how our function ${f(x, y)}$ changes when its input changes slightly, so we call them **partial derivatives**. To emphasize the difference, *we no longer use the letter ${d}$ to indicate tiny chnages, but instead introduce a new symbol ∂* to do the trick, writing each partial derivative as ${\frac{∂f}{∂x}}$, ${\frac{∂f}{∂y}}$, etc.

the symbol ${\frac{∂f}{∂x}}$ is read out loud by saying "the partial derivative of ${f}$ with respect to ${x}$".

### Computing a Partial Derivative
consider this function:
$$
f(x, y) = x^{2}y^{3}
$$

suppose you were asked to evaluate ${\frac{∂f}{∂x}}$, the partial derivative with respect to ${x}$, at the input ${(3, 2)}$.

This works very similarly to the ordinary derivative.

The question is asking about the rate at which the output of ${f}$ changes as we nudge the ${x}$-component of the input slightly, perhaps moving from ${(3, 2)}$ to ${(3.01, 2)}$.

Since we only care about movement in the ${x}$-direction, we might as well treat the ${y}$-value as a constant. In fact, we can just plug in ${y = 2}$ ahead of time before computing any derivatives:
$$
f(x, 2) = x^{2}(2)^{3} = 8x^{2}
$$

Now, asking how ${f}$ changes in response to a small shift in ${x}$ is just an ordinary, single-variable derivative.

### Computin without pre-evaluating ${y}$
Now suppose you are asked to find ${\frac{∂f}{∂x}}$, but I didn't ask you to evaluate it at a specific point. In other words, you should give me a new multivariable function which takes *any* point ${(x, y)}$ as its input and tells me what the rate of change of ${f}$ near that point is as we move purely in the ${x}$-direction.

You can start the same way, treating the ${y}$ value as a constant. However, this time, you can't plug in an actual constant value, like ${y = 2}$. Instead, *pretend* that ${y}$ is a constant and take the derivative:
$$
\frac{d}{dx} f(x, y) = \frac{d}{dx}(x^{2}y^{3}) = 2xy^{3}
$$

or rather, since to emphasize that this is a multivariable function, we use the symbol ${∂}$ instead of ${d}$:
$$
\frac{∂}{∂x} f(x, y) = \frac{∂}{∂x}(x^{2}y^{3}) = 2xy^{3}
$$

You can plug in ${(3, 2)}$ to see that the same result is achieved.

Technically, ${\frac{d}{dx}}$ and ${\frac{∂}{∂x}}$ are the same operation; they don't really have a difference. The only thing is that it's just meant to clarify what type of function is being differentiated.