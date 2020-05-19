---
layout: post
title:  Online Stock Span
date:   2020-05-19 03:00 -0700
catalog: false
level:  Medium
number: 901
lcurl: Online-Stock-Span
tags:
    - leetcode
    - Python
    - design
---

Write a class `StockSpanner` which collects daily price quotes for some stock, and returns the *span* of that stock's price for the current day.

The span of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backwards) for which the price of the stock was less than or equal to today's price.

For example, if the price of a stock over the next 7 days were `[100, 80, 60, 70, 60, 75, 85]`, then the stock spans would be `[1, 1, 1, 2, 1, 4, 6]`.

 

**Example 1:**

```
Input: ["StockSpanner","next","next","next","next","next","next","next"], [[],[100],[80],[60],[70],[60],[75],[85]]
Output: [null,1,1,1,2,1,4,6]
Explanation: 
First, S = StockSpanner() is initialized.  Then:
S.next(100) is called and returns 1,
S.next(80) is called and returns 1,
S.next(60) is called and returns 1,
S.next(70) is called and returns 2,
S.next(60) is called and returns 1,
S.next(75) is called and returns 4,
S.next(85) is called and returns 6.

Note that (for example) S.next(75) returned 4, because the last 4 prices
(including today's price of 75) were less than or equal to today's price.
```

## Solution


Let's maintain a weighted stack of decreasing elements. The size of the weight will be the total number of elements skipped. For example, 11, 3, 9, 5, 6, 4, 7 will be (11, weight=1), (9, weight=2), (7, weight=4).

When we get a new element like 10, this helps us count the previous values faster by popping weighted elements off the stack. The new stack at the end will look like (11, weight=1), (10, weight=7).

```
class StockSpanner:

    def __init__(self):
        self.stack=[]

    def next(self, price: int) -> int:
        res = 1
        while self.stack and self.stack[-1][0] <= price:
            res +=self.stack.pop()[1]
        self.stack.append([price, res])
        return res


# Your StockSpanner object will be instantiated and called as such:
# obj = StockSpanner()
# param_1 = obj.next(price)
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZTelsIrE11w" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
