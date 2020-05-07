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

### Majority Element ###

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
