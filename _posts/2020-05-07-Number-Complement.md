---
layout: post
title:  Number Complement
date:   2020-05-08 02:00 -0700
catalog: false
level:  Easy
number: 476
lcurl: Number-Complement
tags:
    - leetcode
    - Python
---

Given a **positive** integer `num`, output its complement number. The complement strategy is to flip the bits of its binary representation.

 

**Example 1:**

```
Input: num = 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
```

**Example 2:**

```
Input: num = 1
Output: 0
Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.
```

 

**Constraints:**

- The given integer `num` is guaranteed to fit within the range of a 32-bit signed integer.
- `num >= 1`
- You could assume no leading zero bit in the integer’s binary representation.
- This question is the same as 1009: https://leetcode.com/problems/complement-of-base-10-integer/
```

**Solution**

 这个题和计算机术语上的取反不太一样，它是这样的，比如整数5，它对应的二进制是101，这个题目要求的是按位取反， 1->0, 0->1, 因此101->010，然后再变回10进制的2.

 我们知道1和1取异或得到0， 0和1取异或得到1，这样就达到取反的目的，然后我们要决定需要多少位的1，通过简单的数学计算，我们知道需要的数是比输入参数大的，离它最近的2的n次方减一，比如5， 比5大的2的次幂是8，再减去1，得到7，然后用5和7取异或运算，就得到010了。

```
class Solution:
    def findComplement(self, num: int) -> int:
        x = 1
        while x<=num:
            x<<= 1
        return (x-1)^num
```

## 视频讲解 YouTube

<iframe width="560" height="315" src="https://www.youtube.com/embed/WCw5DUqo7e4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>