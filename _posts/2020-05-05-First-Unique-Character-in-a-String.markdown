---
layout: post
title:  "First Unique Character in a String"
date:   2020-05-05 11:00 -0700
catalog: false
tags:
    - leetcode
    - Python
    - string
---

### First Unique Character in a String ###



Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

**Examples:**

```
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.
```



**Note:** You may assume the string contain only lowercase letters.



**Solution:**

```
from collections import Counter
class Solution:
    def firstUniqChar(self, s: str) -> int:
        cs = Counter(s)
        for i,c in enumerate(s):
            if cs[c]==1:
                return i
        return -1
```



[![Watch Youtube](https://img.youtube.com/vi/FOZ4zkXnKD4/0.jpg)](https://www.youtube.com/watch?v=FOZ4zkXnKD4)