## Input:
```python
'''
 The 24 Game
 
 Given any four digits in the range 1 to 9, which may have repetitions,
 Using just the +, -, *, and / operators; and the possible use of
 brackets, (), show how to make an answer of 24.
 
 An answer of "q" will quit the game.
 An answer of "!" will generate a new set of four digits.
 Otherwise you are repeatedly asked for an expression until it evaluates to 24
 
 Note: you cannot form multiple digit numbers from the supplied digits,
 so an answer of 12+12 when given 1, 2, 2, and 1 would not be allowed.
 
'''
 
from __future__ import division, print_function
import random, ast, re
import sys
 
if sys.version_info[0] < 3: input = raw_input
 
def choose4():
    'four random digits >0 as characters'
    return [str(random.randint(1,9)) for i in range(4)]
 
def welcome(digits):
    print (__doc__)
    print ("Your four digits: " + ' '.join(digits))
 
def check(answer, digits):
    allowed = set('() +-*/\t'+''.join(digits))
    ok = all(ch in allowed for ch in answer) and \
         all(digits.count(dig) == answer.count(dig) for dig in set(digits)) \
         and not re.search('\d\d', answer)
    if ok:
        try:
            ast.parse(answer)
        except:
            ok = False
    return ok
 
def main():    
    digits = choose4()
    welcome(digits)
    trial = 0
    answer = ''
    chk = ans = False
    while not (chk and ans == 24):
        trial +=1
        answer = input("Expression %i: " % trial)
        chk = check(answer, digits)
        if answer.lower() == 'q':
            break
        if answer == '!':
            digits = choose4()
            print ("New digits:", ' '.join(digits))
            continue
        if not chk:
            print ("The input '%s' was wonky!" % answer)
        else:
            ans = eval(answer)
            print (" = ", ans)
            if ans == 24:
                print ("Thats right!")
    print ("Thank you and goodbye")   
 
if __name__ == '__main__': main() 
```

## Output:
```python
 The 24 Game

 Given any four digits in the range 1 to 9, which may have repetitions,
 Using just the +, -, *, and / operators; and the possible use of
 brackets, (), show how to make an answer of 24.

 An answer of "q" will quit the game.
 An answer of "!" will generate a new set of four digits.

 Note: you cannot form multiple digit numbers from the supplied digits,
 so an answer of 12+12 when given 1, 2, 2, and 1 would not be allowed.


Your four digits: 3 2 4 6
Expression 1: (3 - 1)*(6*4)
The input '(3 - 1)*(6*4)' was wonky!
Expression 2: (3 - 2) * 6 * 4
 =  24
That's right!
Thank you and goodbye.
```

## Alternative
```python
import random, re
chars = ["(",")","/","+","-","*"]  
while True:
    charsandints, ints = [], []
    for x in range(4):
        ints.append(str(random.randrange(1,10)))
    charsandints = chars + ints
    print("Numbers are:", ints)
    guess = raw_input("Enter your guess:")
    if guess.lower() == "q":
        break
    elif guess.lower() == "|":
        pass
    else:
        flag = True
        for a in guess:
            if a not in charsandints or guess.count(a) > charsandints.count(a):
                flag = False
        if re.search("\d\d", guess):
            print("You cannot combine digits.")
            break
        if flag:
            print("Your result is: ", eval(guess))
            if eval(guess) == 24:
                print("You won")
                break
            else:
                print("You lost")
                break
        else:
            print("You cannot use anthing other than", charsandints)
            break
print("Thanks for playing")
```

[Code for Solving](https://theconfused.me/blog/solving-the-24-game/)

### Solving the 24 Game
Problem: given 4 numbers, one has to try to make 24 using the 4 basic operations & using each number once and only once.

Sometimes will be 4-number combos that can't make 24. One example is **\[3, 9, 4, 10\]**. irl, might just consider the cards before giving up and agreeing that it's impossible, but this is incredibly arbitrary; might very well pass over combinations that are actually possible but no one could see, like **\[1, 5, 5, 5, \]**.

### Instictive approach
First instict was to construct all possible expressions that are possible within the four numbers and check whether any of them equal 24, or any other number you choose. It is easy to permute the numbers and operations, but the main difficulty lies in the placement of brackets.

For four numbers, the possible positions of brackets are still iterable, though just barely, and makes the code look very ugly. For example, the first solution above that uses this principle; it specifies all the possible bracket insertion indices in an arithmetic expression string using the following code snippet:
```python
brackets = ( [()] + [(x,y)
                     for x in range(0, exprlen, 2)
                     for y in range(x+4, exprlen+2, 2)
                     if (x,y) != (0,exprlen+1)]
             + [(0, 3+1, 4+2, 7+3)] ) # double brackets case
```

The empty tuple is the case w/ no brackets, the list comprehension after that generates all possible combinations of open brackets(variable x) and close brackets(variable y), and the third list is the indices of the brackets in the double bracket case, as in **(5 + 3) \* (1 + 2)**.

The major limitation of this soln is that it only works for four numbers, where it is easy to reason about the bracket placements. To make it work for more than 4 numbers, one would have to take into account double and triple brackets, nested brackets, and many more. In retrospect it might be possible to algorithmically generate possible bracket placements, possibly with some kind of recursive algorithm, but at that point it just felt paralyzingly messy.

### A recursive approach
Realized that to make it work for more numbers than four, would have to take a different approach. A strategy used when playing a game can be implemented in the code.

Don't think abt bracket placement when playing game, neither do you try to construct all possible expressions from the four numbers and evaluate them one-by-one to see if they give the desired answer. Instead, given four numbers, what I would do mentally is this: would try to combine pairs of numbers and reduce them, until there are two numbers remaining, and check if there is any way these two numbers evaluate to 24.

for example, if we started with **\[1, 2, 3, 4\]**, this is roughly the thought process that occurs:
```
[1, 2, 3, 4] --> [1, 6, 4] --> [1, 24] --> 24 --> success!
```

As such, it becomes apparent that this is a recursive solution: solving for n numbers is the same as choosing to combine 2 numbers and solving for the remaining n-1 numbers.

After this, writing the algorithm isn't difficult. For a given list of numbers, I iterate through all possible pairs that can be generated from the list. For each pair, I go through the possible values that can be produced from the pair by using the 4 operators. For each value, I generate a list with one less element than the previous, and call the function again.

This contains two nested for loops, and might blow up for a large input array. But practically the 24 game is usually played with 4 numbers, and the algorithm does reasonably well with a list of similar order of magnitude.

The resulting python code looks like this, with the main solver logic in **solve()**:
```python
import itertools

def solve(numbers, goal=24, expr=[]):
    if expr == []:
        expr = [str(n) for n in numbers]
    if len(numbers) == 1:
        if numbers[0] == goal:
            return numbers[0]
        else:
            return False
    if len(numbers) == 2:
        answers, answer_exps = combinetwo(numbers[0], numbers[1])
        for i,answer in enumerate(answers):
            if answer == goal:
                return convert_expr_to_string(expr[0], expr[1], answer_exps[i])
        return False

    pairs = set(itertools.combinations(numbers, 2))
    for pair in pairs:
        possible_values, possible_expr = combinetwo(*pair)
        for counter, value in enumerate(possible_values):
            expression = possible_expr[counter]
            a_index = numbers.index(pair[0])
            b_index = numbers.index(pair[1])
            if a_index == b_index:
                b_index = numbers.index(pair[1], a_index + 1);

            expr_string = convert_expr_to_string(expr[a_index], expr[b_index], expression)
            newlist = numbers[:]
            newexpr = expr[:]
            
            # replace the two numbers with the combined result
            a_index = newlist.index(pair[0])
            newlist.pop(a_index)
            b_index = newlist.index(pair[1])
            newlist.pop(b_index)
            newlist.append(value)

            # order matters
            newexpr.pop(a_index)
            newexpr.pop(b_index)
            newexpr.append(expr_string)
            result = solve(newlist, goal, newexpr)
            if result:
                return remove_redundant_brackets(result)
            else:
                continue

def convert_expr_to_string(a, b, expr):
    temp = [a, b]
    result = '(' + str(temp[expr[0]]) + ')' + str(expr[1]) + '(' + str(temp[expr[2]]) + ')'
    return result

def combinetwo(a, b):
    result = [a + b, a * b]
    expr = [(0, '+', 1), (0, '*', 1)]
    if b > a:
        result.append(b-a)
        expr.append((1, '-', 0))
    else:
        result.append(a-b)
        expr.append((0, '-', 1))
    if b != 0:
        result.append(a / b)
        expr.append((0, '/', 1))
    if a != 0:
        result.append(b / a)
        expr.append((1, '/', 0))
    return result, expr

def remove_redundant_brackets(expr):
    stack = []
    # indices to be deleted
    indices = []
    for i, ch in enumerate(expr):
        if ch == '(':
            stack.append(i)
        if ch == ')':
            last_bracket_index = stack.pop()
            enclosed = expr[last_bracket_index + 1:i]
            if enclosed.isdigit():
                indices.append(i)
                indices.append(last_bracket_index)
    return "".join([char for idx, char in enumerate(expr) if idx not in indices])
```

An example usage looks like this:
```python
>>> solve([1, 5, 5, 5], goal=24)
'5*5(-(1/5))'
```

Of course you can pass in any goal and a list of arbitrary length. Currently, it should return nothing if there is no solution.

[Page that's implemented in JS](https://theconfused.me/get24)