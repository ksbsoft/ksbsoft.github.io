---
layout: post
title:  Majority Element
date:   2020-05-06 11:00 -0700
catalog: false
tags:
    - leetcode
    - Python
    - array
---

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

**Example 1:**

```
Input: [3,2,3]
Output: 3
```

**Example 2:**

```
Input: [2,2,1,1,1,2,2]
Output: 2
```

------

**Solution 1:**

这个题的一种思路就是先把输入数组转化成一个Counter对象，然后把Counter对象中出现最多的找出来，或者把Counter中出现的值比list长度一半还大的找出来。
```
from collections import Counter
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        ct= Counter(nums)
        l = len(nums) //2
        for num in nums:
            if ct[num] >l:
                return num
```

**Solution 2:**

这个题的另一个解决方法很巧，就是初始化一个计数器，然后遍历数组，如果计数器为0，则将当前值作为候选结果，如果不是0，则如果所遍历的值和候选值一样，将计数器加1，否则减一，遍历完后最后的候选值就是所找的元素，（假设一定存在该数）。
```
class Solution:
    def majorityElement(self, nums):
        count = 0
        candidate = None

        for num in nums:
            if count == 0:
                candidate = num
            count += (1 if num == candidate else -1)

        return candidate

```

## 视频讲解 YouTube

<iframe width="560" height="315" src="https://www.youtube.com/embed/MGJkXgQri8k" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
