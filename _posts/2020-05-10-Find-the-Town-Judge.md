---
layout: post
title:  Find the Town Judge
date:   2020-05-10 02:00 -0700
catalog: false
tags:
    - leetcode
    - Python
    - list
---
In a town, there are `N` people labelled from `1` to `N`. There is a rumor that one of these people is secretly the town judge.

If the town judge exists, then:

1. The town judge trusts nobody.
2. Everybody (except for the town judge) trusts the town judge.
3. There is exactly one person that satisfies properties 1 and 2.

You are given `trust`, an array of pairs `trust[i] = [a, b]` representing that the person labelled `a` trusts the person labelled `b`.

If the town judge exists and can be identified, return the label of the town judge. Otherwise, return `-1`.

 

**Example 1:**

```
Input: N = 2, trust = [[1,2]]
Output: 2
```

**Example 2:**

```
Input: N = 3, trust = [[1,3],[2,3]]
Output: 3
```

**Example 3:**

```
Input: N = 3, trust = [[1,3],[2,3],[3,1]]
Output: -1
```

**Example 4:**

```
Input: N = 3, trust = [[1,2],[2,3]]
Output: -1
```

**Example 5:**

```
Input: N = 4, trust = [[1,3],[1,4],[2,3],[2,4],[4,3]]
Output: 3
```

## Solution

根据题意，作为一个法官，如果有N个人，那么必须要有N-1个人信任他，也就是在trust列表的第二个元素个数要等于N-1，而且，他不相信任何人，也就是说他不会出现在trust列表的第一个元素上。用个图形来表示，下图中1，2，4都信任3，而3不信任任何人，也就是入度-出度= N-1

![judge]\img\judge.png)



```
class Solution:
    def findJudge(self, N: int, trust: List[List[int]]) -> int:
        ct= [0] * (N+1)
        for x, y in trust:
            ct[x] -=1
            ct[y] +=1
        for i in range(1,N+1):
            if ct[i] ==N-1:
                return i
        return -1
```


## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/qhFHaLPjfjM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>