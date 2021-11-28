question: how does velocity depend on a distance vs. time function
-> velocity @ single moment doesn't make sense: doesn't move at all(paradox of derivative)
-> need to compare two separate values to find the velocity at a certain point in time

${\frac{ds}{dt}}$ = tiny change in distance over tiny change in time -> think of as slope of two very close pts on graph(${\frac{rise}{run}}$) -> velocity = function of time.

to make derivative function:

choose small value for ${dt}$, like 0.01. Now compute the function ${s}$ at ${t + dt}$, minus the value of the function at ${t}$(difference in distance traveled between t and t+dt). Divide distance by the change in time ${dt}$, which gives the velocity function, also the derivation of the derivative.
$$
\frac{ds}{dt}(t) = \frac{s(t+dt) - s(t)}{dt}
$$

^ instead of one set value, ${dt}$ becomes the ratio of as it approaches 0: the slope of the line of points ${dt}$ and ${ds}$ on the function ${s(t)}$ slowly approaches the slope of the tangent line to the function.

therefore, the derivative isn't the rise-over-run slope of two points near each other on the graph; it's equal to the slope of a line **tangent** to the graph at a single point.

