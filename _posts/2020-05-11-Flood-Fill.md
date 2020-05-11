---
layout: post
title:  Flood Fill
date:   2020-05-11 02:00 -0700
catalog: false
level:  Easy
number: 733
lcurl: Flood-Fill
tags:
    - leetcode
    - Python
    - list
---
An `image` is represented by a 2-D array of integers, each integer representing the pixel value of the image (from 0 to 65535).

Given a coordinate `(sr, sc)` representing the starting pixel (row and column) of the flood fill, and a pixel value `newColor`, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image.

**Example 1:**

```
Input: 
image = [[1,1,1],[1,1,0],[1,0,1]]
sr = 1, sc = 1, newColor = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: 
From the center of the image (with position (sr, sc) = (1, 1)), all pixels connected 
by a path of the same color as the starting pixel are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected
to the starting pixel.
```

## Solution

这个题的使用递归遍历的思想，从sr，sc开始如果分别向上下左右四个方向调用递归函数，如果所调用的当前位置的值和原来的值一样，则用新的值替换掉。注意递归结束的条件有2个，一个是所输入的位置必须是在image的有效范围内，即row>=0 and row <len(image), col>=0 and col<len(image[0])

```
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
        rows,cols, origion_value = len(image), len(image[0]), image[sr][sc]
        def dfs(row, col):
            if (not(0<=row<rows and 0<=col<cols)) or image[row][col]!=origion_value:
                return
            image[row][col] = newColor
            [dfs(row+x,col+y) for x,y in ([(-1,0),(1,0),(0,-1),(0,1)])]
        if origion_value !=newColor:
            dfs(sr, sc)
        
        return image

```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/muVS7mUeq6g" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

