---
layout: post
title:  Delete Node in a Linked List
date:   2020-06-02 04:00 -0700
catalog: false
level:  Easy
number: 237
lcurl: Delete-Node-in-a-Linked-List
tags:
    - leetcode
    - Python
    - linkedlist
---


Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

Given linked list -- head = [4,5,1,9], which looks like following:

![img](https://assets.leetcode.com/uploads/2018/12/28/237_example.png)

 

**Example 1:**

```
Input: head = [4,5,1,9], node = 5
Output: [4,1,9]
Explanation: You are given the second node with value 5, the linked list should become 4 -> 1 -> 9 after calling your function.
```

**Example 2:**

```
Input: head = [4,5,1,9], node = 1
Output: [4,5,9]
Explanation: You are given the third node with value 1, the linked list should become 4 -> 5 -> 9 after calling your function.
```


## Solution

这个题没有给linkedlist的头结点， 我们的做法是把当前结点的下一个结点的值赋给当前结点，然后删除掉下一个结点。

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val =node.next.val
        node.next = node.next.next
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/pcpQrFsI0eU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>