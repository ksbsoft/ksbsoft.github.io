---
layout: post
title:  Ransom Note
date:   2020-05-08 02:00 -0700
catalog: false
level:  Easy
number: 383
lcurl: Ransom-Note
tags:
    - leetcode
    - Python
    - string
---

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

 

**Example 1:**

```
Input: ransomNote = "a", magazine = "b"
Output: false
```

**Example 2:**

```
Input: ransomNote = "aa", magazine = "ab"
Output: false
```

**Example 3:**

```
Input: ransomNote = "aa", magazine = "aab"
Output: true
```

 

**Constraints:**

- You may assume that both strings contain only lowercase letters.

## Solution

这个题的思路就是看看ransomNote中的每个字符是不是都在magazine 中，重复的也要考虑，我们借助python的Counter，把ransomNote和magazine 都转化成Counter，然后比较ransomNote中每个字符对应的计数器是不是都大于magazine ，如果是，则返回true，否则返回false。


```
from collections import Counter
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        rans = Counter(ransomNote)
        mags = Counter(magazine)
        for s in rans:
            if mags[s]<rans[s]:
                return False
        return True
```

## 视频讲解 YouTube

<iframe width="560" height="315" src="https://www.youtube.com/embed/N7Rgmz_RykE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>