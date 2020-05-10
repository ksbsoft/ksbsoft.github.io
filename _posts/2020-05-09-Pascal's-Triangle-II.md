---
layout: post
title:   Pascal's Triangle II
date:   2020-05-09 15:00 -0700
catalog: false
tags:
    - leetcode
    - Python
---

Given a non-negative index *k* where *k* ≤ 33, return the *k*th index row of the Pascal's triangle.

Note that the row index starts from 0.

![img](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)
In Pascal's triangle, each number is the sum of the two numbers directly above it.

**Example:**

```
Input: 3
Output: [1,3,3,1]
```
## Solution
我们首先确定一下最后返回的列表里有rowIndex + 1个数，而且第一个元素是1， 可以先初始化一个列表[1,0,0,0,0] 0的个数等于rowIndex， 然后循环rowindex次，每一次从最后一个元素开始计算。

i = 0

row[0] =1

j从1(i+1)开始递减， 计算row[1] = row[1] +row[0]= 1+0=1

此时 row的结果为[1,1,0,0,0]

接下来i=1

j从2到0递减，先计算row[2]=row[2]+row[1] = 0+1 =1

然后计算row[1] = row[1] +row[0] = 1 + 1 =2

row[0]不计算，还是1，退出内层循环，此时 row的结果为[1,2,1,0,0]

同理，i=2后  row的结果为[1,3,3,1,0]

i=3后 此时 row的结果为[1,4,6,4,1]

```
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:

            row = [1] + [0] * rowIndex
            for i in range(rowIndex):
                row[0] = 1
                for j in range(i+1,0,-1):
                    row[j] = row[j] +row[j-1]
            
            return row
    
            
```


## 视频讲解推荐

<iframe width="560" height="315" src="https://www.youtube.com/embed/PKiV5HhnfDw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>