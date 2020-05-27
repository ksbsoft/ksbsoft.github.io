---
layout: post
title:  Possible Bipartition
date:   2020-05-27 03:00 -0700
catalog: false
level:  Medium
number: 886
lcurl: Possible Bipartition
tags:
    - leetcode
    - Python
    - array
    - DFS
---
Given a set of `N` people (numbered `1, 2, ..., N`), we would like to split everyone into two groups of **any** size.

Each person may dislike some other people, and they should not go into the same group. 

Formally, if `dislikes[i] = [a, b]`, it means it is not allowed to put the people numbered `a` and `b` into the same group.

Return `true` if and only if it is possible to split everyone into two groups in this way.

 

**Example 1:**

```
Input: N = 4, dislikes = [[1,2],[1,3],[2,4]]
Output: true
Explanation: group1 [1,4], group2 [2,3]
```

**Example 2:**

```
Input: N = 3, dislikes = [[1,2],[1,3],[2,3]]
Output: false
```

**Example 3:**

```
Input: N = 5, dislikes = [[1,2],[2,3],[3,4],[4,5],[1,5]]
Output: false
```

## Solution

我们把N个人作为图的顶点，不喜欢关系作为边，构造出一个不喜欢的图。然后进行DFS遍历，同时给每个人黑白两色，相邻的不能有相同的颜色。如果冲突，则返回False，否则如果遍历完整个图没发现冲突则返回True。

```
class Solution:
    def possibleBipartition(self, N: int, dislikes: List[List[int]]) -> bool:
        edges = [[] for i in range(N + 1)]
        colors = [0] * (N + 1)
        for u,v in dislikes:
            edges[u].append(v)
            edges[v].append(u)
        for i in range(1,N+1):
            if colors[i]==0:
                q=[i]
                colors[i] = 1
                while q:
                    cur = q.pop()
                    cur_c =colors[cur]
                    for edge in edges[cur]:
                        if colors[edge]==0:
                            q.append(edge)
                            colors[edge] = -1 *cur_c
                        elif (colors[edge] ==cur_c):
                            return False
        return True
```


## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/K97LwvEOxEk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
