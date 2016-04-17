---
layout: article
title: Stock Prices
modified: {}
categories: posts
excerpt: Calculating profit from an array of stock prices
tags: 
  - code_practice
comments: true
published: true
image: 
  feature: null
  teaser: null
  thumb: null
---



This is a fun and free example problem I found on [Interview Cake](https://www.interviewcake.com/). If you haven't been to that site, I would encourage you to check it out. Each problem has an interactive feature which reveals hints as you need them. The key hint for this problem, for me, was to think about how you would solve this by hand. This seems obvious to me now, but sometimes I get so caught up in doing something on a computer, I forget that I used to solve problems with a pen and paper, so I did this with a very simple case, and it was pretty straight forward from there.

**Scenario:** is that you are provided with a 1D array where the indices are in minutes past trade opening time and the values are the price of a particular stock, for each minute.

**Goal:** Write a function that returns the best profit that could be made from a single purchase and sale.

**Specifications:**
- At least 1 minute must pass between buying and selling (so you have to buy before you sell)
- The function must account for the case where the stock price goes down all day (max profit will be negative)
- Perform in O(__n__) time and O(1) space i.e. nested loops aren't going to cut it

### My solution
I decided to approach the problem by popping off the tail of the list and then getting it's difference from minimum value for the values upstream of the tail. This is done for each value in the list. By doing this, I automatically know that I am buying first, then selling at least 1 minute later. I considered updating this difference to be the max so far (greedy approach). Instead, I append each diff to a list of profits the return the maximum profit. 

{% highlight python %}
def get_max_profit(prices):


    """ Function accepts: a python list (1D array)
    Function returns: The maximum positive difference 
    or minimum negative difference possible, 
    between a downstream element - an upstream element. """
    
    profit = list() # initialize an empty list
    
    if len(prices) >= 2: # minimum of two values required    
        for item in prices: # iterate through each list
            # pop off the tail of the list and get the difference 
            # between the popped value and the minimum upstream element
            right, left_min = prices.pop(), min(prices)
            diff = right - left_min
            profit.append(diff) # append the diff
        return max(profit) # return the max diff, where the max diff may be negative
    
    return 'At least two values required to calculate maximum profit.'
{% endhighlight %}

### Testing
Potential Test Cases:

1. Input array contains a minimum of two values 
2. Stock goes up during the day
3. Stock goes down throughout the day (negative max profit)
4. Stock does not change throughout the day (profit = 0)
5. Negative prices (prices should not be below zero)
6. Resource use (time and memory) for an entire day of data from 1 stock (480 values if stocks traded for 8 hours with a value every 1 minute)
7. I could scale the item above to multiple stocks etc. etc. to see performance in this manner, but honestly, if I were going to do that I would probably use some more advanced libraries or approaches (PANDAS, map-reduce, etc.).

#### Tests
I'm new to testing, but recognize that test driven development is the way to go.  I'm going to try a few approaches to testing and see how it works out.  There is a lot of great information about testing out there, I thought this provided a great overview: [Hitchikers Guide to Python Writing Tests](http://docs.python-guide.org/en/latest/writing/tests/)

##### DocTest


{% highlight python %}

def get_max_profit(prices):

    """ Function accepts: a python list (1D array)
    Function returns: The maximum positive difference 
    or minimum negative difference possible, 
    between a downstream element - an upstream element.
    
    Doc Tests:
    >>> get_max_profit([10, 7, 5, 8, 11, 9, 12])
    7
    >>> get_max_profit([10, 9, 8, 7, 6, 5, 4])
    -1
    >>> get_max_profit([])
    'At least two values required to calculate maximum profit.'
    >>> get_max_profit([10])
    'At least two values required to calculate maximum profit.'
    >>> get_max_profit([1, 1, 1, 1, 1, 1])
    0
    """
    
    profit = list() # initialize an empty list
    
    if len(prices) >= 2: # minimum of two values required
    
        for item in prices: # iterate through each list
            # pop off the tail of the list and get the difference 
            # between the popped value and the minimum upstream element
            right, left_min = prices.pop(), min(prices)
            diff = right - left_min
            profit.append(diff) # append the diff
        return max(profit) # return the max diff, where the max diff may be negative
    
    return 'At least two values required to calculate maximum profit.'
    
   {% endhighlight %}
    
   **Results:**
    
    {% highlight python %} 

In [31]: doctest.testmod()
Out[31]: TestResults(failed=0, attempted=5)

{% endhighlight %}
