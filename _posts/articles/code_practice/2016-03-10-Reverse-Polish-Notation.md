---
layout: article
title: Reverse Polish Notation Script
modified:
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
Publishing my solution, future posts will build out with comments and walk through.

```python
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
    ```
