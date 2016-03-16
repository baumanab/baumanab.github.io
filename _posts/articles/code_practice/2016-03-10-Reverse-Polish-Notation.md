---
layout: article
title: Reverse Polish Notation Script
modified: 2016-03-16
categories: posts
excerpt: Python code to make calculations in RPN
tags: [code_practice]
comments: true
published: true
image:
  feature:
  teaser:
  thumb:
---
This is a kata from codewars, the assignement being to code up a reverse Polish notation calculator (RPN).  This takes me way back to high school trig, where I was first introduced to RPN, via an HP calculator.  If you aren't familiar with RPN, check this out [Wikipedia RPN](https://en.wikipedia.org/wiki/Reverse_Polish_notation).  

### The Challenge:

Your job is to create a calculator which evaluates expressions in Reverse Polish notation.

For example expression 5 1 2 + 4 * + 3 - (which is equivalent to 5 + ((1 + 2) * 4) - 3 in normal notation) should evaluate to 14.

Note that for simplicity you may assume that there are always spaces between numbers and operations, e.g. 1 3 + expression is valid, but 1 3+ isn't.

Empty expression should evaluate to 0.

Valid operations are +, -, *, /.

You may assume that there won't be exceptional situations (like stack underflow or division by zero).

### Per the Wikipedia RPN link (above):

In reverse Polish notation the operators follow their operands; for instance, to add 3 and 4, one would write "3 4 +" rather than "3 + 4". If there are multiple operations, the operator is given immediately after its second operand; so the expression written "3 − 4 + 5" in conventional notation would be written "3 4 − 5 +" in RPN: 4 is first subtracted from 3, then 5 added to it. An advantage of RPN is that it removes the need for parentheses that are required by infix. While "3 − 4 × 5" can also be written "3 − (4 × 5)", that means something quite different from "(3 − 4) × 5". In postfix, the former could be written "3 4 5 × −", which unambiguously means "3 (4 5 ×) −" which reduces to "3 20 −"; the latter could be written "3 4 − 5 ×" (or 5 3 4 − ×, if keeping similar formatting), which unambiguously means "(3 4 −) 5 ×".

To create an RPN calculator, a postfix algorithm can be used, again, per Wikipedia:

The algorithm for evaluating any postfix expression is fairly straightforward:

- While there are input tokens left
+ Read the next token from input.
+ If the token is a value
++ Push it onto the stack.
- Otherwise, the token is an operator (operator here includes both operators and functions).
+ It is already known that the operator takes n arguments.
+ If there are fewer than n values on the stack
++ (Error) The user has not input sufficient values in the expression.
+ Else, Pop the top n values from the stack.
+ Evaluate the operator, with the values as arguments.
+ Push the returned results, if any, back onto the stack.
- If there is only one value in the stack
+ That value is the result of the calculation.
- Otherwise, there are more values in the stack
+ (Error) The user input has too many values.

**Example**
The infix expression "5 + ((1 + 2) × 4) − 3" can be written down like this in RPN:

5 1 2 + 4 × + 3 −
The expression is evaluated left-to-right, with the inputs interpreted as shown in the following table (the Stack is the list of values the algorithm is "keeping track of" after the Operation given in the middle column has taken place):

So, basically, to solve this coding problem, we should use a stack.  Since I am using Python, I don't have handy access to a stack data structure, but I can use a list (1D array) like a stack by using the .append and .push methods on a list.

### Test Set:

{% highlight python % linenos=table}

Test.assert_equals(calc(""), 0, "Should work with empty string")
Test.assert_equals(calc("1 2 3"), 3, "Should parse numbers")
Test.assert_equals(calc("1 2 3.5"), 3.5, "Should parse float numbers")
Test.assert_equals(calc("1 3 +"), 4, "Should support addition")
Test.assert_equals(calc("1 3 *"), 3, "Should support multiplication")
Test.assert_equals(calc("1 3 -"), -2, "Should support subtraction")
Test.assert_equals(calc("4 2 /"), 2, "Should support division")


{% endhighlight %}


{% highlight python % linenos=table}

def calc(expr):
    
    """recieves an rpn string as an argument, returns float value
    https://en.wikipedia.org/wiki/Reverse_Polish_notation"""
    
    if expr:
        ops = list('+-/*')
        stack = list()
        for item in expr.split():
            if item in ops:
                a,b = stack.pop(), stack.pop()
                result = eval('{}{}{}'.format(b, item, a))
                stack.append(str(result))
            else:
                stack.append(item)
        return float(stack.pop())
    
    return 0
    
    {% endhighlight %}
