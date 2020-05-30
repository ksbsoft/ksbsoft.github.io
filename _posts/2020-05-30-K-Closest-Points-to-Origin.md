---
layout: post
title:  K Closest Points to Origin
date:   2020-05-30 04:00 -0700
catalog: false
level:  Medium
number: 973
lcurl: k-closest-points-to-origin/
tags:
    - leetcode
    - Python
    - array
---

We have a list of `points` on the plane. Find the `K` closest points to the origin `(0, 0)`.

(Here, the distance between two points on a plane is the Euclidean distance.)

You may return the answer in any order. The answer is guaranteed to be unique (except for the order that it is in.)

 

**Example 1:**

```
Input: points = [[1,3],[-2,2]], K = 1
Output: [[-2,2]]
Explanation: 
The distance between (1, 3) and the origin is sqrt(10).
The distance between (-2, 2) and the origin is sqrt(8).
Since sqrt(8) < sqrt(10), (-2, 2) is closer to the origin.
We only want the closest K = 1 points from the origin, so the answer is just [[-2,2]].
```

**Example 2:**

```
Input: points = [[3,3],[5,-1],[-2,4]], K = 2
Output: [[3,3],[-2,4]]
(The answer [[-2,4],[3,3]] would also be accepted.)
```

## Solution

这个题的思路就是计算每个点的平方和，然后按从小到大排列，取出前个数。我们用优先队列来实现。

Python中的heapq

```
import heapq
class Solution:
    def kClosest(self, points: List[List[int]], K: int) -> List[List[int]]:
        q=[]
        for x, y in points:
            t = (-x*x-y*y,x,y)
            if len(q)<K:
                heapq.heappush(q,t)
            else:
                heapq.heappushpop(q,t)
        res =[]
        for _,x,y in q:
            res.append([x,y])
        return res
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/UcGlcA1NE-U" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

