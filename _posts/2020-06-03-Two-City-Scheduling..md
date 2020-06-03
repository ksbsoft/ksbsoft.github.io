---
layout: post
title:  Two City Scheduling
date:   2020-06-03 04:00 -0700
catalog: false
level:  Easy
number: 1029
lcurl: Two-City-Scheduling
tags:
    - leetcode
    - Python
    - array
---

There are `2N` people a company is planning to interview. The cost of flying the `i`-th person to city `A` is `costs[i][0]`, and the cost of flying the `i`-th person to city `B` is `costs[i][1]`.

Return the minimum cost to fly every person to a city such that exactly `N` people arrive in each city.

 

**Example 1:**

```
Input: [[10,20],[30,200],[400,50],[30,20]]
Output: 110
Explanation: 
The first person goes to city A for a cost of 10.
The second person goes to city A for a cost of 30.
The third person goes to city B for a cost of 50.
The fourth person goes to city B for a cost of 20.

The total minimum cost is 10 + 30 + 50 + 20 = 110 to have half the people interviewing in each city.
```


## Solution

这个题的思路是先让所有人都去城市A， 然后计算如果把每个人从A移到B的cost，然后排序从小到大，把前一半的人move到B

```
class Solution:
    def twoCitySchedCost(self, costs: List[List[int]]) -> int:
        res =0
        q=[]
        n = len(costs)//2                     
        for i in range(n):
            res = res +costs[i][0]
            heapq.heappush(q,costs[i][1]-costs[i][0])
        for i in range(n,len(costs)):
            res = res +costs[i][0]
            res +=heapq.heappushpop(q,costs[i][1]-costs[i][0])
        return res
```


## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/_IZ1pPdVqdQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>