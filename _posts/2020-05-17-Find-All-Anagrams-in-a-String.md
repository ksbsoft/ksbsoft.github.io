---
layout: post
title:  Find All Anagrams in a String
date:   2020-05-7 03:00 -0700
catalog: false
level:  Medium
number: 438
lcurl: Find-All-Anagrams-in-a-String
tags:
    - leetcode
    - Python
    - string
---

Given a string **s** and a **non-empty** string **p**, find all the start indices of **p**'s anagrams in **s**.

Strings consists of lowercase English letters only and the length of both strings **s** and **p** will not be larger than 20,100.

The order of output does not matter.

**Example 1:**

```
Input:
s: "cbaebabacd" p: "abc"

Output:
[0, 6]

Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```



**Example 2:**

```
Input:
s: "abab" p: "ab"

Output:
[0, 1, 2]

Explanation:
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
```

## Solution
先计算一下p的长度， 然后按顺序从s中取长度和p等长的字符串，看看他们是不是anagram, 我们可以排序这两个字符串，然后看看是不是相等，如果相等则把索引放进最终的结果中，但这样会超时，我们用来替换。然后移到下一个字符，把新字符放在里去，同时把第一个从Counter里减少一个,如果为0，则移除。

```
from collections import Counter
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        res =[]
        cp = Counter(p)
        lp =len(p)
        i = 0
        sc=  Counter(s[i:i+ lp-1])
        while (i+lp<=len(s)):
            sc[s[i+lp -1]] +=1
            if sc ==cp:
                res.append(i)
            sc[s[i]] -=1
            if sc[s[i]] ==0:  
                del  sc[s[i]]      
            i = i+1
        return res
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/OmgN9AqfxEk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
