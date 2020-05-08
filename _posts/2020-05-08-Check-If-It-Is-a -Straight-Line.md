---
layout: post
title:  Check If It Is a Straight Line
date:   2020-05-08 13:00 -0700
catalog: false
tags:
    - leetcode
    - Python
    - list
---

You are given an array `coordinates`, `coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.

 

 

**Example 1:**

![img](https://assets.leetcode.com/uploads/2019/10/15/untitled-diagram-2.jpg)

```
Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
Output: true
```

**Example 2:**

**![img](https://assets.leetcode.com/uploads/2019/10/09/untitled-diagram-1.jpg)**

```
Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
Output: false
```

 

**Constraints:**

- `2 <= coordinates.length <= 1000`
- `coordinates[i].length == 2`
- `-10^4 <= coordinates[i][0], coordinates[i][1] <= 10^4`
- `coordinates` contains no duplicate point.

## Solution

这个题比较直接，我们只需要比较这些点构成的斜率是不是一样，如果是那么它们就在同一条直线上，计算斜率的方法就还是用任意两点的y值，除以它们对应的x值
$$
(y_{2}-y_{1})\over(x_{2}-x_{1})
$$
考虑到分母可能为0，我们可以用2个变量，分别计算y2-y1 和x2-x1,

```
class Solution:
    def checkStraightLine(self, coordinates: List[List[int]]) -> bool:
        
        dy = (coordinates[1][1] - coordinates[0][1])
        dx = (coordinates[1][0] - coordinates[0][0])
        
        for i in range(2,len(coordinates)):
            dyp = (coordinates[i][1] - coordinates[1][1])
            dxp = (coordinates[i][0] - coordinates[1][0])
            if dy* dxp!= dx * dyp:
                return False
        return True;
```

## Youtube视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/fiuEeBWYFJM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
