---
layout: post
title:  Course Schedule
date:   2020-05-29 04:00 -0700
catalog: false
level:  Medium
number: 207
lcurl: Course-Schedule
tags:
    - leetcode
    - Python
    - DFS
---

There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses-1`.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: `[0,1]`

Given the total number of courses and a list of prerequisite **pairs**, is it possible for you to finish all courses?

 

**Example 1:**

```
Input: numCourses = 2, prerequisites = [[1,0]]
Output: true
Explanation: There are a total of 2 courses to take. 
             To take course 1 you should have finished course 0. So it is possible.
```

**Example 2:**

```
Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
Output: false
Explanation: There are a total of 2 courses to take. 
             To take course 1 you should have finished course 0, and to take course 0 you should
             also have finished course 1. So it is impossible.
```



## Solution

我们根据prerequisites构造一个图，如果图中有环，则说明有冲突，否则就可以学完所有课。从第一个节点开始采用遍历过的节点mark成-1，没有遍历的为0，如果遍历过程中遇到-1，说明形成了还。

def canFinish(self, numCourses, prerequisites):
    graph = [[] for _ in xrange(numCourses)]
    visit = [0 for _ in xrange(numCourses)]
    for x, y in prerequisites:
        graph[x].append(y)
    def dfs(i):
        if visit[i] == -1:
            return False
        if visit[i] == 1:
            return True
        visit[i] = -1
        for j in graph[i]:
            if not dfs(j):
                return False
        visit[i] = 1
        return True
    for i in xrange(numCourses):
        if not dfs(i):
            return False
    return True
if node v has not been visited, then mark it as 0.
if node v is being visited, then mark it as -1. If we find a vertex marked as -1 in DFS, then their is a ring.
if node v has been visited, then mark it as 1. If a vertex was marked as 1, then no ring contains v or its successors.

```
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        graph =[[] for _ in range(numCourses) ]
        for x, y in prerequisites:
            graph[x].append(y)
        visited=[0] * numCourses
        
        def dfs(i):
            if visited[i] == -1:
                return False
            if visited[i] == 1:
                return True
            visited[i]= -1
            for j in graph[i]:
                if not dfs(j):
                    return False
            visited[i]=1
            return True
        for i in range(numCourses):
            if not dfs(i):
                return False
        return True
            
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZWaKl0_a6bU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

