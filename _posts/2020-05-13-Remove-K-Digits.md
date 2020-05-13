---
layout: post
title:  Remove K Digits
date:   2020-05-13 02:00 -0700
catalog: false
level:  Medium
number: 402
lcurl: Remove-K-Digits 
tags:
    - leetcode
    - Python
    - list
---
Given a non-negative integer *num* represented as a string, remove *k* digits from the number so that the new number is the smallest possible.

**Note:**

- The length of *num* is less than 10002 and will be ≥ *k*.
- The given *num* does not contain any leading zero.



**Example 1:**

```
Input: num = "1432219", k = 3
Output: "1219"
Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.
```



**Example 2:**

```
Input: num = "10200", k = 1
Output: "200"
Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.
```



**Example 3:**

```
Input: num = "10", k = 2
Output: "0"
Explanation: Remove all the digits from the number and it is left with nothing which is 0.
```

## Solution

边界情况，如果 k比字符串的长度还大或者相等，那么相当于把所有的字符都移除掉，直接返回字符串 "0".
然后尽可能使得左边的数字小，构造一个递增的数字序列，如果不是，就pop出来。

比如： Input: num = "1432219", k = 3
[]
['1'] => 因为stack为空，直接进去。
['1', '4'] => 因为 1 < 4, 也直接进去
['1', '3'] => 因为3< 4,把4pop掉，k减1，然后把3进stack
['1', '2'] => 2 < 3, pop3，2进去，k-1
['1', '2', '2'] => 2 == 2, 进stack
['1', '2', '1'] => 因为  1 < 2, pop 2 出来，1 进去，k减1， 此时，k=0
['1', '2', '1', '9'] => 因为k=0，我们不需要再移除任何字符，把后面的数字直接进stack

特殊情况1：
所有的字符已经递增，那么我们只需要把右边k个字符去掉就行。
特殊情况2：
前面是0，需要去掉，
特殊情况3：
去掉前面的0后，变成空了，这个时候需要返回"0"

```
class Solution:
    def removeKdigits(self, num: str, k: int) -> str:
        if (k>= len(num)):
            return '0'
        res = []
        for c in num:
            while (k>0 and len(res)>0 and c<res[-1]):
                k = k -1
                res.pop()
            res.append(c)
        while k:
            res.pop()
            k = k-1
        return ''.join(res).lstrip('0') or '0'
```

##　Youtube视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/dDJX1ZL8ZOw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

