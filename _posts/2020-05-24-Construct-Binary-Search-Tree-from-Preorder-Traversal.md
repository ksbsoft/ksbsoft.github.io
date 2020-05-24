---
layout: post
title:  Construct Binary Search Tree from Preorder Traversal
date:   2020-05-24 03:00 -0700
catalog: false
level:  Medium
number: 1008
lcurl: Construct-Binary-Search-Tree-from-Preorder-Traversal
tags:
    - leetcode
    - Python
    - tree
---
Return the root node of a binary **search** tree that matches the given `preorder` traversal.

*(Recall that a binary search tree is a binary tree where for every node, any descendant of `node.left` has a value `<` `node.val`, and any descendant of `node.right` has a value `>` `node.val`. Also recall that a preorder traversal displays the value of the `node` first, then traverses `node.left`, then traverses `node.right`.)*

It's guaranteed that for the given test cases there is always possible to find a binary search tree with the given requirements.

**Example 1:**

```
Input: [8,5,1,7,10,12]
Output: [8,5,10,1,7,null,12]
```


## Solution

利用二叉搜索树的特点，它的左子树小于根节点，右子树大于根节点。二叉树的先序遍历，都有一个元素是根节点，然后比根节点小的都是它的左子树，剩下的就是它的左子树，进行递归调用，直到preorder为空。

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def bstFromPreorder(self, preorder: List[int]) -> TreeNode:
        if not preorder:
            return
        val = preorder[0]
        index =1
        while index < len(preorder) and preorder[index]<val:
            index = index+1

        root = TreeNode(val)
        root.left = self.bstFromPreorder(preorder[1:index])
        root.right = self.bstFromPreorder(preorder[index:])
        return root
```

           
