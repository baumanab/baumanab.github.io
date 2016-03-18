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
    
    for item in prices: # iterate through each list
        # pop off the tail of the list and get the difference 
        # between the popped value and the minimum upstream element
        right, left_min = prices.pop(), min(prices)
        diff = right - left_min
        profit.append(diff) # append the diff
    return max(profit) # return the max diff, where the max diff may be negative
{% endhighlight %}