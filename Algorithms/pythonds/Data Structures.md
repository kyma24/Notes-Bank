-   4.2. What are Linear Structures?
    
    Stacks, queues, deques, and lists are examples of data collections whose items are ordered depending on how they are added or removed. Once an item is added, it stays in that position relative to the other elements that came before and after it. These collections are often referred to as **linear data structures**.
    
    Linear structures can be thought of as having 2 ends. Sometimes these ends are referred to as the "left" and the "right" or in some cases the "front" and the "rear". Could also call them the "top" and the "bottom". The names given to the ends are not significant. What does distinguish linear structures from each other is they way in which the items are added and removed, in particular the location where these additions and removals occur.
    
    These variations are some of the most useful data structures in computer science. They appear in many algorithms and can be used to solve a variety of important problems.
    
-   4.3. What is a Stack?
    
    A **stack**(sometimes called a "push-down stack") is an ordered collection of items where the addition of new items and the removal of existing items always takes place at the same end. This end is commonly referred to as the "top". The end opposite to the top is known as the "base".
    
    The base of a stack is significant since items stored in the stack are closer to the base represent those that have been in the stack the longest. The most recently added item is the one that is in position to be removed first. This ordering principle is sometimes called **LIFO**, **last-in first-out**. It provides an ordering based on length of time in the collection. Newer items are near the top, while older items are near the base.
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/034f033d-ca25-4199-b19e-6c7f54e225c6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/034f033d-ca25-4199-b19e-6c7f54e225c6/Untitled.png)
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e69ca3e2-4319-427a-a372-aee941acebfe/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e69ca3e2-4319-427a-a372-aee941acebfe/Untitled.png)
    
    One of the most useful ideas related to stacks comes from the simple observation of items as they are added and then removed. Assume you start out with a clean desktop. Now place books one at a time on top of each other. You are constructing a stack. Consider what happens after you begin removing the books. The order that they are removed is exactly the reverse of the order that they were placed. Stacks are fundamentally important, as they can be used to reverse the order of items. The order of insertion is the reverse of the order of removal.
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1a1783cd-6a97-4ec0-bb22-ca323b114a6b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1a1783cd-6a97-4ec0-bb22-ca323b114a6b/Untitled.png)
    
    considering this reversal property, you can perhaps think of examples of stacks that occur when using your computer. For example, every web browser has a Back button. As you navigate from web page to web page, those pages are placed on a stack(actually the URLs). The current page that you are viewing is on the top and the first page you looked at is the base. If you click the Back button, you begin to move in reverse order through the pages.
    
-   4.4. The Stack Abstract Data Type
    
    The stack abstract data type is defined by the following structure and operations. A stack is structured as an ordered collection of items where items are added to and removed from the end called the "top". Stacks are ordered LIFO. The stack operations are given below.
    
    -   `Stack()` creates a new stack that is empty. It needs no parameters and returns an empty stack.
    -   `push(item)` adds a new item to the top of the stack. It needs the item and returns nothing.
    -   `pop()` removes the top item from the stack. It needs no parameters and returns the item. The stack is modified.
    -   `peek()` returns the top item from the stack but doesn't remove it. It needs no parameters. The stack is not modified.
    -   `isEmpty()` tests to see whether the stack is empty. It needs no parameters and returns a Boolean value.
    -   `size()` returns the number of items on the stack. It needs no parameters and returns an integer.
-   4.6. Simple Balanced Parentheses
    
    this function determines whether or not the parentheses are properly closed. Also assumes that a stack class is connected.
    
    ```python
    from pythonds.basic import Stack
    
    def parChecker(symbolString):
        s = Stack()
        balanced = True
        index = 0
        while index < len(symbolString) and balanced:
            symbol = symbolString[index]
            if symbol == "(":
                s.push(symbol)
            else:
                if s.isEmpty():
                    balanced = False
                else:
                    s.pop()
    
            index = index + 1
    
        if balanced and s.isEmpty():
            return True
        else:
            return False
    
    print(parChecker('((()))'))
    print(parChecker('(()'))
    ```
    
-   4.7. Balanced Symbols
    
    same as simple balanced parentheses, except in general instead.
    
    ```python
    from pythonds.basic import Stack
    
    def parChecker(symbolString):
        s = Stack()
        balanced = True
        index = 0
        while index < len(symbolString) and balanced:
            symbol = symbolString[index]
            if symbol in "([{":
                s.push(symbol)
            else:
                if s.isEmpty():
                    balanced = False
                else:
                    top = s.pop()
                    if not matches(top,symbol):
                           balanced = False
            index = index + 1
        if balanced and s.isEmpty():
            return True
        else:
            return False
    
    def matches(open,close):
        opens = "([{"
        closers = ")]}"
        return opens.index(open) == closers.index(close)
    
    print(parChecker('{({([][])}())}'))
    print(parChecker('[{()]'))
    ```
    
-   4.8. Converting Decimal Numbers to Binary Numbers
    
    Uses an algorithm called "Divide by 2" that uses a stack to keep track of the digits for the binary result.
    
    The Divide by 2 algorithm assumes that starts off with an integer greater than 0. A simple iteration then continually divides the decimal number by 2 and keeps track of the remainder. The first division by 2 gives information as to whether the value is even or odd. An even value will have a remainder of 0. It will have the digit 0 in the ones place. An odd value will have a remainder of 1 and will have the digit 1 in the ones place. We think about building the binary number as a sequence of digits; the first remainder we compute will actually be the last digit in the sequence. As shown below, we again see the reversal property that signals that a stack is likely to be the appropriate data structure for solving this problem.
    
    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1bd80e9d-ddd2-4a5c-82bb-d0e781988fed/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1bd80e9d-ddd2-4a5c-82bb-d0e781988fed/Untitled.png)
    
    The Python code in ActiveCode 1 implements the Divide by 2 algorithm. The function divideBy2 takes an argument that is a decimal number and repeatedly divides it by 2. The modulo operator extracts the remainder and then pushes it on the stack. After the division process reaches 0, a binary string is constructed. The binary digits are then popped from the stack one at a time and appended to the right-hand end of an empty string. The binary string is then returned.
    
    ```python
    from pythonds.basic import Stack
    
    def divideBy2(decNumber):
        remstack = Stack()
    
        while decNumber > 0:
            rem = decNumber % 2
            remstack.push(rem)
            decNumber = decNumber // 2
    
        binString = ""
        while not remstack.isEmpty():
            binString = binString + str(remstack.pop())
    
        return binString
    
    print(divideBy2(42))
    ```
    
    this code can easily be extended to perform the conversion for any base. In computer science it's common to use a number of different encodings.
    
    The function `divideby2` can be modified to accept not only a decimal value but also a base for the intended conversion. The "Divide by 2" idea is simply replaced with a more general "Divide by base". A new function called `baseConverter` takes a decimal number and any base between 2 and 16 as parameters. The remainders are still pushed onto the stack until the value being converted becomes 0. The same left-to0right string construction technique can be used with a slight change. Base 2 through base 10 numbers need a maximum of 10 digits, so the typical digit characters work fine. The problem is when we go beyond. We can no longer simply use the remainders, as they are themselves represented as two-digit decimal numbers. Instead we need to create a set of digits that can be used to represent those remainders beyond 9.
    
    ```python
    from pythonds.basic import Stack
    
    def baseConverter(decNumber,base):
        digits = "0123456789ABCDEF"
    
        remstack = Stack()
    
        while decNumber > 0:
            rem = decNumber % base
            remstack.push(rem)
            decNumber = decNumber // base
    
        newString = ""
        while not remstack.isEmpty():
            newString = newString + digits[remstack.pop()]
    
        return newString
    
    print(baseConverter(25,2))
    print(baseConverter(25,16))
	```
    
    a solution to this problem is to extend the digit set to include some alphabet characters for the 16 digits. To implement this, a digit string is created that stores the digits in their corresponding positions. 0 is at position 0, 1 is at position 1, A is at position 10, B is at position 11, and so on. When a remainder is removed from the stack, it can be used to index into the digit string and the correct resulting digit can be appended to the answer. i.e. if the remainder 13 is removed from the stack, the digit D is appended to the resulting string.
    
-   4.9. Infix, Prefix and Postfix Expressions
    
    when you write an arithmetic expression, the form of the expression provides you with information so that you can interpret it correctly. Like when multiplying B\*C, you know that it is multiplication since the multiplication operator \* appears between the two in the expression. This type of notation is referred to as **infix** since the operator is _in between_ the two operands that it is working on.
    
    Each operator has a **precedence** level. Operators of higher precedence are used before operators of lower precedence(PEMDAS). The only thing that can change that order is the presence of parentheses. The precedence order for arithmetic operators places multiplication and division over addition and subtraction. If two operators of equal precedence appear, then a left-to-right ordering or associativity is used.
    
    There are some other ways to express these expressions. Consider the infix expression A + B. What would happen if we moved the operator between the two operands? The resulting expression would be + A B. Likewise, we could move the operator to the end. We would get A B +.
    
    These changes to the position of the operator with respect to the operands create two new expression formats, **prefix** and **postfix**. Prefix expression notation requires that all operators precede the two operands that they work on. Postfix, on the other hand, requires that its operators come after the corresponding operands.
    
    A + B \* C would be written as + A \* B C in prefix. The multiplication operator comes immediately before the operands B and C, denoting that \* has precedence over +. The addition operator then appears before the A and the result of the multiplication.
    
    In postfix, the expression would be A B C \\* +. Again, the order of operations is preserved since the \\* appears immediately after the B and the C, denoting that \\* has precedence, with + coming after. Although the operators moved and now appear either before or after their respective operands, the order of te operands stayed exactly the same relative to one another.
    
Infix | Prefix | Postfix
-----|----------|---------
A + B | + A B | A B +
A + B * C | + A * B C | A B C * +
   Consider the infix expression (A + B) \* C. Recall that in this case, infix requires the parentheses to force the performance of the addition before the multiplication. However, when A + B was written in prefix, the addition operator was simply moved before the operands, + A B. The result of this operation becomes the first operand for the multiplication. The multiplication operator is moved in front of the entire expression, giving us \* + A B C. Likewise, in postfix A B + forces the addition to happen first. The multiplication can be done to that result and the remaining operand C. The proper postfix expression is then A B + C \*.
  
   The parentheses are removed because the operators are no longer ambiguous with respect to the operands that they work on. Only infix notation requires the additional symbols. The order of operations within prefix and postfix expressions is completely determined by the position of the operator and nothing else. In many ways, this makes infix the least desirable notation to use.
    
   Infix | Prefix | Postfix
	-------|-------|---------
(A + B) * C | * + A B C | A B + C *
    
-   4.9.1. Conversion of Infix Expressions to Prefix and Postfix
    
    So far, ad hoc(created/done for a specific purpose) methods have been used to convert between infix expressions and the equivalent prefix and postfix expression notations. As expected, there are algorithmic ways to perform this conversion that allows any expression of any complexity to be correctly transformed.
    
    First technique that will be considered uses the notion of a fully parenthesized expression that was discussed earlier. Recall that A + B \* C can be written as (A + (B \* C)) to show explicitly that the multiplication has precedence over the addition. On closer observation, however, it can be seen that each parenthesis pair also denotes the beginning and the end of an operand pair with the corresponding operator in the middle.
   
    Take note of the subexpression(B \* C)'s right parentheses; if we were to move the multiplication symbol to that position and remove the matching left parenthesis, giving us B C \*, we would in effect have converted the subexpression with postfix notation. If the addition operator were also moved to its corresponding right parenthesis position and the matching left parenthesis were removed, the complete postfix expression would result.
    
    ![../_images/moveright.png](https://runestone.academy/runestone/books/published/pythonds/_images/moveright.png)
    
    If the same thing is done but instead of moving the symbol to the position of the right parenthesis, we move it to the left, we get prefix notation. The position of the parenthesis pair is actually a clue to the final position of the enclosed operator.
    
    ![../_images/moveleft.png](https://runestone.academy/runestone/books/published/pythonds/_images/moveleft.png)
    
    So in order to convert an expression, no matter how complex, to either prefix or postfix notation, fully parenthesize the expression using the order of operations. Then move the enclosed operator to the position of either the left or right parenthesis depending on whether you want prefix or postfix notation.
    
    More complex expression: (A + B) \* C - (D - E) \* (F + G).
    
    ![../_images/complexmove.png](https://runestone.academy/runestone/books/published/pythonds/_images/complexmove.png)
    
-   4.9.2 General Infix-to-Postfix Conversion
    
   To develop algorithm to convert any infix expression to a postfix expression, will need to look closely at conversion process.
    
   Consider the expression A + B \* C. As shown, A B C \* + is the postfix equivalent. The operands A, B, and C stay in their relative positions. It is only the operators that change position. Look again at the operators of the infix expression. The first operator that appears from left to right is +. However, in the postfix expression, + is at the end since the next operator, \*, has precedence over addition. The order of operations in the original expression is reversed in the resulting postfix expression.
    
   As the expression is processed, the operators have to be saved somewhere since their corresponding right operands are not seen yet. Also, the order of these saved operators may need to be reversed due to their precedence. This is the case with the addition and the multiplication in this example. Since the addition operator comes before the multiplication operator and has lower precedence, it needs to appear after the multiplication operator is used. Because of this reversal of order, it makes sense to consider using a stack to keep the operators until they are needed.
    
   What abt (A + B) \* C? Recall that A B + C \* is the postfix equivalent. Again, processing this infix expression from left to right, + is seen first. In this case, when \* is seen, + as already been placed in the result expression because it has precedence over \* by virtue of the parentheses. Can now start to see how the conversion algorithm will work. When see a left parentheses, will save it to denote that another operator of high precedence will be coming. That operator will need to wait until the corresponding right parenthesis appears to denote its position. When that right parentheses does appear, the operator can be popped from the stack.
    
   As the infix expression is scanned from left to right, will use a stack to keep the operators. This will provide the reversal that we noted in the first example. The top of the stack will be the most recently saved operator. Whenever a new operator is read, will need to consider how that operator compares in precedence with the operators, if any, already on the stack.
    
   Assume the infix expression is a string of tokens delimited by spaces. The operator tokens are \*, /, +, and - along with the left and right parentheses, ( and ). The operand tokens are the single-character identifiers B, C, and so on. The following steps will produce a string of tokens in postfix order.
    
   1.  Create an empty stack called `opstack` for keeping operators. Create an empty list for output.
   2.  Convert the input infix string to a list by using the string method `split`
   3.  scan the token list from left to right.
       -   If the token is an operand, append it to the end of the output list.
       -   If the token is a left parenthesis, push it on the `opstack`
       -   If the token is a right parenthesis, pop the `opstack` until the corresponding left parenthesis is removed. Append each operator to the end of the output list.
       -   If the token is an operator, \*, /, +, or -, push it on the `opstack`. However, first remove any operators already on the `opstack` that have higher or equal precedence and append them to the output list.
   4.  When the input expression has been completely processed, check the `opstack`. Any operators still on the stack can be removed and appended to the end of the output list.
    
   Below shows the conversion algorithm working on the expression A \* B + C \* D. Note that the first \* operator is removed upon seeing the + operator. Also, + stays on the stack when the second \* occurs, since multiplication has precedence over addition. At the end of the infix expression when the stack is popped twice, removing both operators and placing + as the last operator in the postfix expression.
    
   ![../_images/intopost.png](https://runestone.academy/runestone/books/published/pythonds/_images/intopost.png)
    
   In order to code this algorithm in Python, will use a dictionary called `prec` to hold the precedence values for the operators. This dictionary will map each operator to an integer that can be compared against the precedence levels of other operators. The left parenthesis will receive the lowest value possible. This way any operator that is compared against it will have higher precedence and will be placed on top of it. The 15th line defines the operands to be any upper-case character or digit.
    
   ```python
    from pythonds.basic import Stack
    
    def infixToPostfix(infixexpr):
        prec = {}
        prec["*"] = 3
        prec["/"] = 3
        prec["+"] = 2
        prec["-"] = 2
        prec["("] = 1
        opStack = Stack()
        postfixList = []
        tokenList = infixexpr.split()
    
        for token in tokenList:
            if token in "ABCDEFGHIJKLMNOPQRSTUVWXYZ" or token in "0123456789":
                postfixList.append(token)
            elif token == '(':
                opStack.push(token)
            elif token == ')':
                topToken = opStack.pop()
                while topToken != '(':
                    postfixList.append(topToken)
                    topToken = opStack.pop()
            else:
                while (not opStack.isEmpty()) and \\
                   (prec[opStack.peek()] >= prec[token]):
                      postfixList.append(opStack.pop())
                opStack.push(token)
    
        while not opStack.isEmpty():
            postfixList.append(opStack.pop())
        return " ".join(postfixList)
    
    print(infixToPostfix("A * B + C * D"))
    print(infixToPostfix("( A + B ) * C - ( D - E ) * ( F + G )"))
 ```
    
   More examples of execution:
    
   ```python
    >>> infixtopostfix("(A + B) * (C + D)")
    'A B + C D + *'
    >>> infixtopostfix("(A + B) * C")
    'A B + C *'
    >>> infixtopostfix("A + B * C")
    'A B C * +'
    >>>
```
	
### 4.9.3 Postfix Evaluation
As a final stack example, will consider the evaluation of an expression that is already in postfix notation. In this case, a stack is (again) the data structure of choice. However, as you scan the postfix expression, it is the operands that must wait, not the operators as in the conversion algorithm above. Another way to think abt the solution is that whenever an operation is seen on the input, the two most recent operands will be used in the evaluation.
	
More detail: consider the postfix expression `456 * +`. As you scan the expression from left to right, you first encounter the operands 4 and 5. At this point, you're still unsure abt what to do w/ them until you see the next symbol. Placing each on the stack ensures that they are available if an operator comes next.
	
In this case, the nxt symbol is another operand. So, as before, push it and check the next symbol. Now we see an operator, \*. This means that the two most recent operands need to be used in a multiplication operation. By popping the stack twice, we can get the proper operands and then perform the multiplication(in this case getting the result 30).
	
We can now handle this result by placing it back on the stack so that it can be used as an operand for the later operators in the expression. When the final operator is processed, there will be only one value left on the stack. Pop and return it as the result of the expression.
![../_images/evalpostfix1.png](https://runestone.academy/runestone/books/published/pythonds/_images/evalpostfix1.png)
	
Below is a slightly more complex example, 7 8 + 3 2 + /. There are two things to note in this example. First, the stack size grows, shrinks, and grows again as the subexpressions are evaluated. Second, the division operation needs to be handled carefully. Recall that the operands in the postfix expression are in their original order since postfix changes only the placement of operators. When the operands for the division are popped from the stack, they are reversed. Since division is *not* a commutative operator, we must be sure that the order of the operands isn't switched.
![../_images/evalpostfix2.png](https://runestone.academy/runestone/books/published/pythonds/_images/evalpostfix2.png)

Assume that the postfix expression is a string of tokens delimited by spaces. the operators are \*, /, +, and - and the operands are assumed to be single-digit integer values. The output will be an integer result.

1. Create an empty stack called `operandStack`.
2. Convert the string to a list by using the string method `split`.
3. Scan the token list from left to right
	- If the token is an operand, convert it from a string to an integer and push the value onto the `operandStack`.
	- If the token is an operator, \*, /, +, or -, it will need two operands. Pop the `operandStack` twice. The first pop is the second operand and the second pop is the first operand. Perform the arithmetic operation. Push the result back on the `operandStack`.
4. When the input expression has been completely processed, the result is on the stack. Pop the `operandStack` and return the value.

The complete function for the evaluation of postfix expressions is shown bellow. To assist w/ the arithmetic, a helper function `doMath` is defined that will take two operands and an operator and then perform the proper arithmetic operation.
```python
from pythonds.basic import Stack

def postfixEval(postfixExpr):
    operandStack = Stack()
    tokenList = postfixExpr.split()

    for token in tokenList:
        if token in "0123456789":
            operandStack.push(int(token))
        else:
            operand2 = operandStack.pop()
            operand1 = operandStack.pop()
            result = doMath(token,operand1,operand2)
            operandStack.push(result)
    return operandStack.pop()

def doMath(op, op1, op2):
    if op == "*":
        return op1 * op2
    elif op == "/":
        return op1 / op2
    elif op == "+":
        return op1 + op2
    else:
        return op1 - op2

print(postfixEval('7 8 + 3 2 + /'))
```

