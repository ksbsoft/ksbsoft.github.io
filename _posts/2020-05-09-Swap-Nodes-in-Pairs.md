---
layout: post
title:  Swap Nodes In Pairs
date:   2020-05-09 02:00 -0700
catalog: false
level:  Medium
number: 24
lcurl: Swap-Nodes-in-Pairs
tags:
    - leetcode
    - Python
    - linklist
    - recursion
---
Given a linked list, swap every two adjacent nodes and return its head.

You may **not** modify the values in the list's nodes, only nodes itself may be changed.

 

**Example:**

```
Given 1->2->3->4, you should return the list as 2->1->4->3.
```
## solution
这个题的思路是递归，递归结束条件是当节点为空或者节点的下一个节点为空，这个时候不需要交换，直接返回。
我们先定义一个next节点，指向head的next， nextnext指向head的下下个节点。
第一步：切断next的next指针，让它指向head。
第二步：让head的next指向以nextnext为head的函数返回值。
第三步，让nead指向next。


```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def swapPairs(self, head: ListNode) -> ListNnext
        if head == None or head.next ==None:
            return head
        nextnext = head.next.next
        next = head.next
        next.next = head

        head.next = self.swapPairs(nextnext)
        head = next
        return head
```