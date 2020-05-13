---
layout: post
title:  Construct Binary Tree from Preorder and Inorder Traversal
date:   2020-05-13 03:00 -0700
catalog: false
level:  Medium
number: 105
lcurl: Construct-Binary-Tree-from-Preorder-and-Inorder-Traversal
tags:
    - leetcode
    - Python
    - tree
---
Given preorder and inorder traversal of a tree, construct the binary tree.

**Note:**
You may assume that duplicates do not exist in the tree.

For example, given

```
preorder = [3,9,20,15,7]
inorder = [9,3,15,20,7]
```

Return the following binary tree:

```
    3
   / \
  9  20
    /  \
   15   7
```

## Solution

树的前序遍历的第一个元素是树的根，我们可以在中序遍历中找根的位置，那么在中序遍历根位置的左边就是树的左子树，右边就是树的右子树，反复递归调用直到前序遍历或中序遍历的list为空。


```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:
        
        if not preorder or not inorder:
            return 
        val = preorder[0]
        root = TreeNode(val)
        valueIndex = inorder.index(val)
        
        root.left = self.buildTree(preorder[1:valueIndex + 1], inorder[:valueIndex])
        root.right = self.buildTree(preorder[valueIndex +1:], inorder[valueIndex+1:])
        return root
        

```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qc0XLGFnchU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>