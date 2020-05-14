---
layout: post
title:  Implement Trie (Prefix Tree)
date:   2020-05-14 03:00 -0700
catalog: false
level:  Medium
number: 208
lcurl: Implement-Trie-Prefix-Tree
tags:
    - leetcode
    - Python
    - tree
---
Implement a trie with `insert`, `search`, and `startsWith` methods.

Example:

Trie trie = new Trie();

trie.insert("apple");
trie.search("apple");   // returns true
trie.search("app");     // returns false
trie.startsWith("app"); // returns true
trie.insert("app");   
trie.search("app");     // returns true

## Solutions

```
class Trie:

    def __init__(self):
        """
        Initialize your data structure here.
        
        """
        self.dict={}

    def insert(self, word: str) -> None:
        """
        Inserts a word into the trie.
        """
        cur = self.dict
        for c in word:
            if c not in cur:
                cur[c]={}
            cur = cur[c]
        cur['#'] = True
            
            

    def search(self, word: str) -> bool:
        """
        Returns if the word is in the trie.
        """
        cur = self.dict
        for c in word:
            if c not in cur:
                return False
            else:
                cur= cur[c]
        if '#' in cur:
            return True
        else:
            return False
        

    def startsWith(self, prefix: str) -> bool:
        """
        Returns if there is any word in the trie that starts with the given prefix.
        """
        cur = self.dict
        for c in prefix:
            if c not in cur:
                return False
            else:
                cur= cur[c]
        return True

        


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
```

## Youtube 视频

<iframe width="560" height="315" src="https://www.youtube.com/embed/vSA1_aJfYsk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>