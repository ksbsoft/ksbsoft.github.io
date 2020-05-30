---
layout: post
title:  Counting Bits
date:   2020-05-28 04:00 -0700
catalog: false
level:  Medium
number: 338
lcurl: Counting-Bits
tags:
    - leetcode
    - Python
    - array
---
Given a non negative integer number **num**. For every numbers **i** in the range **0 ≤ i ≤ num** calculate the number of 1's in their binary representation and return them as an array.

**Example 1:**

```
Input: 2
Output: [0,1,1]
```

**Example 2:**

```
Input: 5
Output: [0,1,1,2,1,2]
```


## Solution
这个题的基本思路是，任何一个数乘以2后的1的个数如果是奇数，则比原来的数多出一个1，否则和原来的数的1的个数相同。比如5，（101），有2个1， 10（1010）也是2个1， 11（1011）3个1.


```
class Solution:
    def countBits(self, num: int) -> List[int]:
        res =[0] *(num + 1)
        for i in range(num+1):
            if i%2==0:
                res[i] = res[i//2]
            else:
                res[i] = res[i//2] +1
        return res
```


## YOutube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/OfIyDdepVL0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

