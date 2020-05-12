---
layout: post
title:  Single Element in a Sorted Array  
date:   2020-05-12 02:00 -0700
catalog: false
level:  Medium
number: 540
lcurl: Single-Element-in-a-Sorted-Array  
tags:
    - leetcode
    - Python
    - list
---
You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once. Find this single element that appears only once.

 

**Example 1:**

```
Input: [1,1,2,3,3,4,4,8,8]
Output: 2
```

**Example 2:**

```
Input: [3,3,7,7,10,11,11]
Output: 10
```

 ## Solution
 
在有序的数组中查找，我们采用二分的方法。起始位置left = 0， right = len(nums) -1.
mid =(left  + right) //2.假如mid 是个偶数， 那么在它前面就是个偶数个数字，如果此时它和nums[mid+1]的 值相同，该把left 移到mid+1的位置。 同样，如果mid是奇数，如果此时。nums[mid]和nums[mid -1]相等，说明该找的数字在右边。此时也把left移到mid+1.其他情况，移动right到mid -1.

 ```
 class Solution:
    def singleNonDuplicate(self, nums: List[int]) -> int:
        left = 0
        right = len(nums)-1
        while (left<right):
            mid = (left + right) //2
            if (nums[mid]>nums[mid-1]) and (nums[mid] < nums[mid +1]):
                return nums[mid]
            elif((mid%2==0) and (nums[mid] ==nums[mid +1])) or ((mid%2==1) and (nums[mid] ==nums[mid -1])):
                left = mid +1
            else:
                right = mid - 1
        return nums[left]

```

## Youtube视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/H0ZWQa2k-1E" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>