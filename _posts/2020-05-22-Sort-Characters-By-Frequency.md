---
layout: post
title:  Sort Characters By Frequency
date:   2020-05-22 03:00 -0700
catalog: false
level:  Medium
number: 451
lcurl: Sort-Characters-By-Frequency
tags:
    - leetcode
    - Python
    - string
---

Given a string, sort it in decreasing order based on the frequency of characters.

**Example 1:**

```
Input:
"tree"

Output:
"eert"

Explanation:
'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.
```



**Example 2:**

```
Input:
"cccaaa"

Output:
"cccaaa"

Explanation:
Both 'c' and 'a' appear three times, so "aaaccc" is also a valid answer.
Note that "cacaca" is incorrect, as the same characters must be together.
```



**Example 3:**

```
Input:
"Aabb"

Output:
"bbAa"

Explanation:
"bbaA" is also a valid answer, but "Aabb" is incorrect.
Note that 'A' and 'a' are treated as two different characters.
```

## Solution 

我们先把string转化成Counter，然后对counter对象进行排序，然后再转换成string

```
from collections import Counter
class Solution:
    def frequencySort(self, s: str) -> str:
        cs = Counter(s)
        return ''.join([x*i for x , i in sorted(cs.items(), key = lambda  x:x[1] ,reverse=True)])
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/EhZlKElgdCo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
