---
layout: post
title:  Edit Distance
date:   2020-05-31 05:00 -0700
catalog: false
level:  Hard
number: 155
lcurl: Edit-Distance
tags:
    - leetcode
    - Python
    - dp
---
Given two words *word1* and *word2*, find the minimum number of operations required to convert *word1* to *word2*.

You have the following 3 operations permitted on a word:

1. Insert a character
2. Delete a character
3. Replace a character

**Example 1:**

```
Input: word1 = "horse", word2 = "ros"
Output: 3
Explanation: 
horse -> rorse (replace 'h' with 'r')
rorse -> rose (remove 'r')
rose -> ros (remove 'e')
```

**Example 2:**

```
Input: word1 = "intention", word2 = "execution"
Output: 5
Explanation: 
intention -> inention (remove 't')
inention -> enention (replace 'i' with 'e')
enention -> exention (replace 'n' with 'x')
exention -> exection (replace 'n' with 'c')
exection -> execution (insert 'u')
```

## Solution

这是一个典型的动态规划题目， 初始化第一行从0开始到len(word1)表示将一个空字符转化为word1需要的步骤。第一列为0开始到len(word2)表示将空字符转化为word2所需的步骤。 状态转移方程为：

dp[i][j]= dp[i-1][j-1] if word1[i]==word2[j]
dp[i][j]= min(dp[i-1][j-1] , dp[i-1][j], dp[i][j-1]) + 1 if word1[i] !=word2[j]

```
class Solution:
    def minDistance(self, word1: str, word2: str) -> int:
        m = len(word1)
        n =len(word2)
        dp=[[0 for j in range(n+1)] for i in range(m+1)]

                
        for i in range(m+1):
            dp[i][0] = i
        for j in range(n+1):
            dp[0][j] = j
        
        for i in range(1,m+1):
            for j in range(1,n+1):
                if word1[i-1] ==word2[j-1]:
                    dp[i][j] =dp[i-1][j-1]
                else:
                    dp[i][j] = min(dp[i-1][j], dp[i][j-1],dp[i-1][j-1])+1
        
        return dp[m][n]
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/okJQqpne4F8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


