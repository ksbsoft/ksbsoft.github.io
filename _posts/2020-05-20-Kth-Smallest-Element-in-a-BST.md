---
layout: post
title:  Kth Smallest Element in a BST
date:   2020-05-20 03:00 -0700
catalog: false
level:  Medium
number: 230
lcurl: Kth-Smallest-Element-in-a-BST
tags:
    - leetcode
    - Python
    - tree
---


Given a binary search tree, write a function `kthSmallest` to find the **k**th smallest element in it.

**Note:**
You may assume k is always valid, 1 ≤ k ≤ BST's total elements.

**Example 1:**

```
Input: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
Output: 1
```

**Example 2:**

```
Input: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
Output: 3
```

## Solution

BST树的中序遍历序列是个递增的序列，我们只要取第k-1的元素即可。

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        self.k = k
        def helper(root):
            if root is None:
                return 0
            res= helper(root.left)
            if res:
                return res
            self.k = self.k-1
            if self.k ==0:
                return root.val
            else:
                return helper(root.right)
            
        return helper(root)
   ```

   ## Youtube 视频

   <iframe width="560" height="315" src="https://www.youtube.com/embed/60vz4CRfaxs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   