---
layout: post
title:  Odd Even Linked List
date:   2020-05-16 03:00 -0700
catalog: false
level:  Medium
number: 328
lcurl: Odd-Even-Linked-List
tags:
    - leetcode
    - Python
    - list
---

Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.

You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.

**Example 1:**

```
Input: 1->2->3->4->5->NULL
Output: 1->3->5->2->4->NULL
```

**Example 2:**

```
Input: 2->1->3->5->6->4->7->NULL
Output: 2->3->6->7->1->5->4->NULL
```

**Note:**

- The relative order inside both the even and odd groups should remain as it was in the input.
- The first node is considered odd, the second node even and so on ...

## Solution

先定义下面几个指针， 偶数的头指针，偶数的next指针，奇数的next指针。

然后将奇数的next指针指向偶数的next指针。

然后将奇数指向奇数的next

再把偶数的next指针指向奇数的next。

偶数指向偶数的next。

直到偶数位指针为空并且它的next也为空，此时循环结束，把奇数的next指向偶数的头指针，最后返回头指针。

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def oddEvenList(self, head: ListNode) -> ListNode:
        if not head:
            return None
        
        odd = head
        even =head.next
        even_head = head.next
        
        while even and even.next:
            odd.next = even.next
            odd= odd.next
            even.next = odd.next
            even = even.next
        odd.next = even_head
        return head
        
```

## Youtube视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/lk-6nRW5hnU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


