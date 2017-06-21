---
layout: post
title:  "Merge Two Binary Trees"
date:   2017-06-21
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/4acf6d49535589.58ba166420a53.jpg
tag:
- algorithm
- leetcode
- binary tree
- recursion
- easy
---
### Question: 
Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

### Example:
```
Input: 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
Output: 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
```

### Note:
The merging process must start from the root nodes of both trees.

### Solution：
1. if only one node has the value, return the node
2. if both two nodes have the value, use recursion to go through further nodes
3. until both two nodes are `null`

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
def mergeTrees(self, t1, t2):
    """
    :type t1: TreeNode
    :type t2: TreeNode
    :rtype: TreeNode
    """
    if not t1 and not t2:
        return None
    elif t1 and not t2:
        return t1
    elif t2 and not t1:
        return t2
    root = TreeNode(t1.val + t2.val)
    root.left = self.mergeTrees(t1.left, t2.left)
    root.right = self.mergeTrees(t1.right, t2.right)
    return root
```