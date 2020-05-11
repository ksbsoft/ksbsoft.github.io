---
layout: post
title:  Cousins in Binary Tree
date:   2020-05-07 14:00 -0700
catalog: false
level:  Easy
number: 993
lcurl: Cousins-in-Binary-Tree
tags:
    - leetcode
    - Python
    - tree
---

In a binary tree, the root node is at depth `0`, and children of each depth `k` node are at depth `k+1`.

Two nodes of a binary tree are *cousins* if they have the same depth, but have **different parents**.

We are given the `root` of a binary tree with unique values, and the values `x` and `y` of two different nodes in the tree.

Return `true` if and only if the nodes corresponding to the values `x` and `y` are cousins.

 

**Example 1:
![img](https://assets.leetcode.com/uploads/2019/02/12/q1248-01.png)**

```
Input: root = [1,2,3,4], x = 4, y = 3
Output: false
```

**Example 2:
![img](https://assets.leetcode.com/uploads/2019/02/12/q1248-02.png)**

```
Input: root = [1,2,3,null,4,null,5], x = 5, y = 4
Output: true
```

**Example 3:**

**![img](https://assets.leetcode.com/uploads/2019/02/13/q1248-03.png)**

```
Input: root = [1,2,3,null,4], x = 2, y = 3
Output: false
```

 

**Note:**

1. The number of nodes in the tree will be between `2` and `100`.
2. Each node has a unique integer value from `1` to `100`.

 **Solution**
 
 这个题的基本思路是写一个方法，用这个方法返回对应某个节点的父节点和相应的度，然后分别输入x和y调用相应的函数，如果2次函数的返回值中度相同而且父节点不相同，则返回True,否则返回false。
 ```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isCousins(self, root: TreeNode, x: int, y: int) -> bool:
        def dfs(node, parent, depth, mod):
            if node:
                if node.val == mod:
                    return depth, parent
                return dfs(node.left, node, depth + 1, mod) or dfs(node.right, node, depth + 1, mod)
        dx, px, dy, py = dfs(root, None, 0, x) + dfs(root, None, 0, y)
        return dx == dy and px != py

```

下面的视频提供了另一种思路，就是按层次遍历树，如果它们是在同一层，而且parent不同则返回True,否则返回false。


## 视频讲解 YouTube

<iframe width="560" height="315" src="https://www.youtube.com/embed/2WbgNzAPZD4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
