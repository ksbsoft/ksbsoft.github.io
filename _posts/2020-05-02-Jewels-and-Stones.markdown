---
layout: post
title:  "Jewels and Stones"
date:   2020-05-02 22:43 -0700
tags: 
    - leetcode
    - Python
    - string
---
You're given strings  `J`representing the types of stones that are jewels, and  `S`representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

# **Code**:

{% highlight python %}
class Solution:
    def numJewelsInStones(self, J: str, S: str) -> int:
        res = 0
        for s in S:
            if s in J:
                res += 1
        return res
{% endhighlight %}

