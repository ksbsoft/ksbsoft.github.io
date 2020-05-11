---
layout: post
title:  Count Triplets That Can Form Two Arrays of Equal XOR
date:   2020-05-11 04:00 -0700
catalog: false
level:  Medium
number: 1442
lcurl: Count-Triplets-That-Can-Form-Two-Arrays-of-Equal-XOR
tags:
    - leetcode
    - Python
    - list
---
Given an array of integers `arr`.

We want to select three indices `i`, `j` and `k` where `(0 <= i < j <= k < arr.length)`.

Let's define `a` and `b` as follows:

- `a = arr[i] ^ arr[i + 1] ^ ... ^ arr[j - 1]`
- `b = arr[j] ^ arr[j + 1] ^ ... ^ arr[k]`

Note that **^** denotes the **bitwise-xor** operation.

Return *the number of triplets* (`i`, `j` and `k`) Where `a == b`.

 

**Example 1:**

```
Input: arr = [2,3,1,6,7]
Output: 4
Explanation: The triplets are (0,1,2), (0,2,2), (2,3,4) and (2,4,4)
```

**Example 2:**

```
Input: arr = [1,1,1,1,1]
Output: 10
```

**Example 3:**

```
Input: arr = [2,3]
Output: 0
```

**Example 4:**

```
Input: arr = [1,3,5,7,9]
Output: 3
```

**Example 5:**

```
Input: arr = [7,11,12,9,5,2,7,17,22]
Output: 8
```


## Solution

这个题要求找出满足条件的i,j,k使得arr[i]^arr[i+1]...arr[j-1] 和arr[j]^arr[j+1]...arr[k]的结果一样，换句话说它们的异或结果等于0时是个有效的切片，我们可以通过计算此时j-i 的 差来计算以i开始，以j结尾的i,j,k组合。然后把所有的结果加起来就是最后可能的组合总数。

```
class Solution:
    def countTriplets(self, arr: List[int]) -> int:
        ans = 0
        for i in range(len(arr)):
            xor = arr[i]
            for j in range(i+1,len(arr)):
                xor = xor ^ arr[j]
                if (xor ==0):
                    ans = ans +(j-i)
        
        return ans
```