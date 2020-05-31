---
layout: post
title:  Compare Version Numbers
date:   2020-05-31 05:00 -0700
catalog: false
level:  Medium
number: 155
lcurl: Compare-Version-Numbers
tags:
    - leetcode
    - Python
    - string
---

Compare two version numbers *version1* and *version2*.
If `*version1* > *version2*` return `1;` if `*version1* < *version2*` return `-1;`otherwise return `0`.

You may assume that the version strings are non-empty and contain only digits and the `.` character.

The `.` character does not represent a decimal point and is used to separate number sequences.

For instance, `2.5` is not "two and a half" or "half way to version three", it is the fifth second-level revision of the second first-level revision.

You may assume the default revision number for each level of a version number to be `0`. For example, version number `3.4` has a revision number of `3` and `4` for its first and second level revision number. Its third and fourth level revision number are both `0`.

 

**Example 1:**

```
Input: version1 = "0.1", version2 = "1.1"
Output: -1
```

**Example 2:**

```
Input: version1 = "1.0.1", version2 = "1"
Output: 1
```

**Example 3:**

```
Input: version1 = "7.5.2.4", version2 = "7.5.3"
Output: -1
```

**Example 4:**

```
Input: version1 = "1.01", version2 = "1.001"
Output: 0
Explanation: Ignoring leading zeroes, both “01” and “001" represent the same number “1”
```

**Example 5:**

```
Input: version1 = "1.0", version2 = "1.0.0"
Output: 0
Explanation: The first version number does not have a third level revision number, which means its third level revision number is default to "0"
```

## solution

这个题的思路就是把2个字符串按.分割逐步比较，同时处理0的情况。
 ```
class Solution:
    def compareVersion(self, version1: str, version2: str) -> int:
        if len(version1)==0 and len(version2)==0:
            return 0
        s1 = version1.split('.')[0]
        s2 =version2.split('.')[0]
        
        i1= i2 = None
        if s1 !='':
                i1 = int(s1)
        else:
            i1=0
        if s2 != '':
            i2 = int(s2) 
        else:
            i2=0 
        if i1>i2:
            return 1
        elif i1<i2:
            return -1
        else:
            return self.compareVersion(version1[len(s1)+1:],version2[len(s2)+1:])
 ```

## Youtube视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/GNSTPuSBZFk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>