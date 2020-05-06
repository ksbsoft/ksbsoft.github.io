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

## 视频讲解 YouTube

<iframe width="560" height="315" src="https://www.youtube.com/embed/MDBhZhdn4xk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="" class="embed-responsive-item" style="box-sizing: border-box; position: absolute; top: 0px; bottom: 0px; left: 0px; width: 706.5px; height: 397.406px; border: 0px;"></iframe>
