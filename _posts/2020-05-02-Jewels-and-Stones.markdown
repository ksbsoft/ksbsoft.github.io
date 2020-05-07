---
layout: post
title:  "Jewels and Stones"
date:   2020-05-02 22:43 -0700
catalog: true
tags:
    - leetcode
    - Python
    - string
---
You're given strings  `J`representing the types of stones that are jewels, and  `S`representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

这题的思路就是同时遍历字符串S和J,如果遍历S的时候发现该字符也出现在J中，则将计数器加1，最后返回计数器的值。

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

优化点的解决方案是把J转化成set对象，这样lookup的复杂度就减少为O(1)了，参考代码：

{% highlight python %}
class Solution:
    def numJewelsInStones(self, J: str, S: str) -> int:
        res = 0
        for s in S:
            if s in set(J):
                res += 1
        return res
{% endhighlight %}