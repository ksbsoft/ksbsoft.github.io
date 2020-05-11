---
layout: post
title:  Build an Array With Stack Operations
date:   2020-05-11 03:00 -0700
catalog: false
level:  Easy
number: 1441
lcurl: Build-an-Array-With-Stack-Operations
tags:
    - leetcode
    - Python
    - list
---
Given an array `target` and an integer `n`. In each iteration, you will read a number from  `list = {1,2,3..., n}`.

Build the `target` array using the following operations:

- **Push**: Read a new element from the beginning `list`, and push it in the array.
- **Pop**: delete the last element of the array.
- If the target array is already built, stop reading more elements.

You are guaranteed that the target array is strictly increasing, only containing numbers between 1 to `n` inclusive.

Return the operations to build the target array.

You are guaranteed that the answer is unique.

 

**Example 1:**

```
Input: target = [1,3], n = 3
Output: ["Push","Push","Pop","Push"]
Explanation: 
Read number 1 and automatically push in the array -> [1]
Read number 2 and automatically push in the array then Pop it -> [1]
Read number 3 and automatically push in the array -> [1,3]
```

**Example 2:**

```
Input: target = [1,2,3], n = 3
Output: ["Push","Push","Push"]
```

**Example 3:**

```
Input: target = [1,2], n = 4
Output: ["Push","Push"]
Explanation: You only need to read the first 2 numbers and stop.
```

**Example 4:**

```
Input: target = [2,3,4], n = 4
Output: ["Push","Pop","Push","Push","Push"]
```

## Solution

这个题的思路是循环遍历从1到n+1(不含n+1）,如果发现当前值在target里，那么往结果集里append字符串"Push"。否则，同时append "Push"  和 "Pop"，注意退出条件，当target被遍历完后，说明已经结束了，后面就没必要继续遍历了。

```
class Solution:
    def buildArray(self, target: List[int], n: int) -> List[str]:
        tc =0    
        res = []
        for i in range(1,n+1):
            if tc== len(target):
                break
            if i ==target[tc]:
                res.append("Push")
                tc +=1
            else:
                res.append("Push")
                res.append("Pop")
        return res        
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/gee8Ce-lUzo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>