---
layout: post
title:  Valid Perfect Square
date:   2020-05-09 02:00 -0700
catalog: false
level:  Easy
number: 367
lcurl: Valid-Perfect-Square
tags:
    - leetcode
    - Python
---

Given a positive integer *num*, write a function which returns True if *num* is a perfect square else False.

**Note:** **Do not** use any built-in library function such as `sqrt`.

**Example 1:**

```
Input: 16
Output: true
```

**Example 2:**

```
Input: 14
Output: false
```

## Solution

这是一个典型的二分题，我们设定左边从0开始递增，右边从num开始递减， 如果左边（left）<= 右边这进入循环，先取中点（mid），如果t（mid * mid ）和num相同则说明num是个perferct square，返回true，否则如果t小于num，则把left移到mid+1，反之，将right移到mid-1.

 ```
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        left = 0
        right = num
        while left <= right:
            mid = (left + right) // 2
            t = mid * mid
            if t==num:
                return True
            elif t<num:
                left = mid +1
            else:
                right = mid -1
        return False
 ```

 ## Youtube视频

 <iframe width="560" height="315" src="https://www.youtube.com/embed/TqiXE_MicWw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
 