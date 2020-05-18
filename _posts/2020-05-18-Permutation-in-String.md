---
layout: post
title:  Permutation in String
date:   2020-05-17 03:00 -0700
catalog: false
level:  Medium
number: 567
lcurl: Permutation-in-String
tags:
    - leetcode
    - Python
    - string
---

Given two strings **s1** and **s2**, write a function to return true if **s2** contains the 
permutation of **s1**. In other words, one of the first string's permutations is the **substring** of the second string.

 

**Example 1:**

```
Input: s1 = "ab" s2 = "eidbaooo"
Output: True
Explanation: s2 contains one permutation of s1 ("ba").
```

**Example 2:**

```
Input:s1= "ab" s2 = "eidboaoo"
Output: False
```

## Solution

这个题和438题几乎一模一样，我们还是用来做，如果s2的子串是s1的排列，那么他们对应的Counter应该是一样的。
同样使用活动窗口的思路。

```
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        cp = Counter(s1)
        lp =len(s1)
        i = 0
        sc=  Counter(s2[i:i+ lp-1])
        while (i+lp<=len(s2)):
            sc[s2[i+lp -1]] +=1
            if sc ==cp:
                return True
            sc[s2[i]] -=1
            if sc[s2[i]] ==0:  
                del  sc[s2[i]]      
            i = i+1
        return False
```


## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/nKXeVLBnONs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
