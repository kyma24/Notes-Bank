Hanoi: you have a collection of 3 pegs, and you have these disks of descending size(think of these disks having a hole in the middle, so that you can fit them onto a peg).

![Towers of Hanoi (article) | Algorithms | Khan Academy](https://cdn.kastatic.org/ka-perseus-images/5b5fb2670c9a185b2666637461e40c805fcc9ea5.png)

They all start up stacked up from biggest to smallest on one spindle, and the goal is to move the entire tower from one spindle to another. The rule is you can only move one disk at a time, and you can't move a bigger disk on top of a smaller disk.

i.e. your first move must involve moving disk 1, since any other disk has stuff on top of it that needs to get out of the way before it can move.

After that, can move disk 2, but it has to go on whatever peg doesn't currently have disk 1, since otherwise you'd be putting a bigger disk onto a smaller one, which isn't allowed.

Something interesting is that you can solve it just by counting up in binary and associating the rhythm of that counting with a certain rhythm of disc movements.

### Focus on Rhythm: Counting in Binary
The rhythm of counting begins by walking through all ten of the digits in base 10.

Then, having run out of digits, you express the next number, ten, with 2 digits: 1, 0. You say that 1 is in the tens place, since it's meant to encapsulate the group of 10 that you've already counted up to so far, while freeing the ones place to reset to zero.

The rhythm of counting repeats like this; counting up nine, rolling over to the tens place, counting up nine more, rolling over to the tens place, etc.

Until after repeating *that* process nine times, you roll over to a hundreds place; a digit that keeps track of how many groups of 100 you've hit, freeing up the other two digits to reset to zero.

In this way, the rhythm of counting is kind of self-similar: even if you zoom out to a larger scale, the process looks like doing something, rolling over, doing that same thing, rolling over, and repeating nine times before an even larger roll over.

In binary/base 2, you limit yourself to two digits: 0 and 1, commonly called 'bits', which is short for 'binary digits'.

The result is that when you're counting, you have to roll over all the time.
After counting 0, 1 you've already run out of bits, so you need to roll over to a two's place, writing '1 0'. Then, increment up to 1 1, which represents 3, and already you have to roll over again, and since there's a one in that two's place, that has to roll over as well, giving you 1 0 0 which represents one group of 2 squared plus 0 groups of two plus 0.

The pattern becomes more obvious:
Flip the last, roll over once. Flip the last, roll over twice. Flip the last, roll over once. Flip the last, roll over three times...

### Solve the Towers of Hanoi
You can start by counting from 0. Whenever you're only flipping that last bit from a 0 to a 1, move disk 1 **one** peg to the right. If it was already on the rightmost peg, you just loop it back to the first peg.

If in the binary counting you roll over once to the two's place, meaning you flip the last two bits, you move disk number 2 wherever you're forced to do so.

So after this, counting up to 1 1, that involves just flipping the last bit, so you move disk 1 again.

Then, when the binary counting rolls over twice to the four's place, move disk number 3, and the pattern continues. 

Flip the last, move disk 1, flip the last 2, move disk 2, flip the last, move disk 0.

And here, we're going to have to roll over thrice to the eight's place, and that corresponds to moving disk number 4.

![Data Structure & Algorithms - Tower of Hanoi - Tutorialspoint](https://www.tutorialspoint.com/data_structures_algorithms/images/tower_of_hanoi.gif)

It turns out, this solutions not only solves the Towers of Hanoi without problems, but it also does it in the most efficient way possible.

This solution's "proof" comes down to a recursive perspective.

So starting off, disc 4 needs 3 2 and 1 to get off in order to move. Just from disc 4's perspective, if you want to figure out how disc 4 is going to get over here, somehow disc 3 2 1 have to get to spindle B(the only way 4 can move).

Having done that, then we can move disk 4 there. And the disk 4 is ready, so you never need to move it again.

And in a sense, you now have a smaller version of the same problem:

Now you've got disc 1, 2 and 3 sitting on spindle B, we gotta get them to C. So the idea is that if I just focus on one disc, and I think what I'm going to have to do to get this disc to work, I can turn the bigger problem into something slightly smaller.

Basically, every disc has the same strategy: Everyone above me, get off, then I'm going to move, and okay everyone come back on.

```python
def solve_toh(n_disks):
	if n_disks == 0:
		return
	solve_toh(n_disks-1)
	move_disk(n_disks-1)
	solve_toh(n_disks-1)
```

![Tower of Hanoi: Solve and Optimize with Memoization | by Anisha Jain |  DataDrivenInvestor](https://miro.medium.com/max/2840/1*_0Vpiq0j6GkCGw0B0oZP8A.png)


So the one explanation to why this works is that the pattern you would use to generate these binary numbers has the exact same structure as the pattern you would use for towers of Hanoi, which is why if you look at the bits flipping, you're effectively reversing this process, the recursive algorithm for the Towers of Hanoi.

### Towers of Hanoi and Sierpinski
![Tower of Hanoi - Wikipedia](https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Tower_of_Hanoi_3-disk_graph_-_longest_path.svg/440px-Tower_of_Hanoi_3-disk_graph_-_longest_path.svg.png)

The problem variant is that you can think these disks are in a line; you're only allowed to move a disk from one spindle to an adjacent one. And so now the question is solve the towers of Hanoi.

It's more complicated, but it's still similar. If you want to move disc 4, you have to move everything above it. Now, you want to get the above tower of 3 2 and 1 and move it to peg C, then move disc 4 to B, then get the 3-based tower to peg A, hen move disc 4 to peg C, and then move the tower all the way back.

The smaller cases are basically the same, and this is, again, the most efficient solution.

Just as this pattern in the original problem is mirrored by counting in binary, the breakdown of this constrained problem is mirrored by counting in base 3, also known as ternary.

### Rhythm of Counting with Ternary
You start off by just counting through the ternary bits(trits): 0, 1, 2. Then you have to roll over to a second trit, which is in the threes place. By repeating this process, you can flip to 1 0 0, or ninth place.

The pattern becomes count to 22, roll over, count to 22, roll over, etc.

### Sierpinski
Apparently, this will not only solve the Towers of Hanoi; this will go through every single possible configuration of the disks. For each n number of disks, the total number of states the towers can be in is thus ${3^n}$.

Now, what we're going to do is represent each one of these configurations with a dot, a node in the graph of the Sierpinski's triangle. Note that this is ordered that the bottom left node is the start state.

Then, we say two different configurations are connected if you could move from one to the other with some legal Towers of Hanoi (unconstrained) move. When you go through and connect all of the configurations like this, the graph structure for Towers of Hanoi has this suspiciously familiar shape.

![Tower of Hanoi - Wikipedia](https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Tower_of_Hanoi_3-disk_graph_-_longest_path.svg/440px-Tower_of_Hanoi_3-disk_graph_-_longest_path.svg.png)

Now, zoom into the starting state. This node has all the disks on peg A, is going to be connected to the one on its lower left, which is the result of moving disk 1 to peg B. And both of those are connected to this one, which is the result of moving disk 1 to peg C. These three configs make up a little triangle in the graph. In fact, any config is going to be part of one of these trinagles somewhere in the graph. You just consider what happens as you freely move around disk 1 around the pegs.

Now, to understand how these triangular islands are interconnected, take a look at these two nodes. They differ only by a movement of disc number 2 from peg A to peg C, so they're going to be connected by an edge. This edge is going to be a bridge connecting all the "triangle islands" that are formed.

In fact, those two triangles, along with the other one(each in one corner), form kind of a meta-triangle when you consider all the movements of disc 2. <- Triforce Pattern

Each little clump of three nodes in the lowest left corner here represents a different position for disc number 1, and the Triforce Pattern as a whole represents all configurations you can get by moving around disks number 1 or 2.

And self-similarly, a movement of disc number 3 gives a bridge from one of the Triforce patterns to a new one.

And the three possible places where disc 2 can live give us these three separate Triforce patterns, each in a corner of the triangle, which are each connected by a little bridge.

The fact that there are only two nodes in one of these Triforce patterns that has an edge going out of the pattern itself is just a reflection of the fact that it's hard to move disc number 3. That only happens in those very special configurations where disc 1 and disc 2 are both out of the way.

![Hanoi vs Sierpiński](https://11011110.github.io/blog/assets/2020/hanoi-vs-sierpinski.svg)

As you consider more and more discs, this pattern continues. The graph structure for Towers of Hanoi configurations is one Sierpinski triangle.


What this ternary pattern is going to give us is a way to wander through the Sierpinski triangle graph and hit each node once and only once.