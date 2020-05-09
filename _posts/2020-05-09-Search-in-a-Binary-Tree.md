---
layout: post
title:  Search in a Binary  Tree
date:   2020-05-09 14:00 -0700
catalog: false
tags:
    - leetcode
    - Python
    - tree
    - recursion
---
Given the root node of a binary  tree  and a value. You need to find the node in the tree that the node's value equals the given value. Return the subtree rooted with that node. If such node doesn't exist, you should return NULL.

For example, 

```
Given the tree:
        4
       / \
      2   7
     / \
    1   3

And the value to search: 2
```

You should return this subtree:

```
      2     
     / \   
    1   3
```

In the example above, if we want to search the value `5`, since there is no node with value `5`, we should return `NULL`.

Note that an empty tree is represented by `NULL`, therefore you would see the expected output (serialized tree format) as `[]`, not `null`.

## Solution

 我们可以采用先序遍历的方式进行，从根节点开始，如果发现对应的节点的val和输入的val一样，就返回该节点，否则继续遍历左子树，如果还没找到则继续遍历右子树，直到遍历结束。
 递归结束条件是root为空或者对应节点的值等于输入的参数。

 ```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def searchBT(self, root: TreeNode, val: int) -> TreeNode:
        if root == None:
            return root
        if root.val == val:
            return root;
        return self.searchBT(root.left, val) or self.searchBT(root.right, val)
 ```

 如果这是一个BST,那么我们可以根据BST的特点，所有左子树的值小于等于根节点，右之树的值大于根节点，稍微改一下上面的代码：

  ```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def searchBST(self, root: TreeNode, val: int) -> TreeNode:
        if root == None:
            return root
        if root.val == val:
            return root;
        if root.val < val:
            return self.searchBST(root.right, val)
        else:
            return self.searchBST(root.left, val) 
 ```
