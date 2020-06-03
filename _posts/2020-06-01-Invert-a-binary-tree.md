---
layout: post
title:  Invert Binary Tree
date:   2020-05-31 04:00 -0700
catalog: false
level:  Easy
number: 226
lcurl: Invert-Binary-Tree
tags:
    - leetcode
    - Python
    - tree
---
Invert a binary tree.

**Example:**

Input:

```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

Output:

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

## Solution

这个题，我们假设某个节点的左右子树已经invert了，那么对于该节点我们只需要简单交换一下它的左右子树。如果节点为空。则退出递归。

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        if root is None:
            return None
        root.left,root.right = self.invertTree(root.right),self.invertTree(root.left)
        return root

```


## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/f0_3O1msz4I" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

