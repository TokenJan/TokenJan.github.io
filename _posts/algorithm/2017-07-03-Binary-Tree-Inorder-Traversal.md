---
layout: post
title:  "Binary Tree Inorder Traversal"
date:   2017-07-01
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/9ac30253396079.5932e355d30b9.jpg
categories: algorithm
tag:
- leetcode
- binary tree
- medium
---
### Question:
Given a binary tree, return the inorder traversal of its nodes' values.

### Example:
Given binary tree `[1,null,2,3]`,
```
   1
    \
     2
    /
   3
```
return `[1,3,2]`.

### Note:
Recursive solution is trivial, could you do it iteratively?

### Solution：
__recursion version:__ it is trivial

```python
def inorderTraversal(self, root):
    res = []
    self.helper(root, res)
    return res

def helper(self, root, res):
    if root:
    	self.helper(root.left, res)
    	res.append(root.val)
    	self.helper(root.right, res)
```

__iterative version:__ stack is used

```python
def inorderTraversal(self, root):
    ans = []
    stack = []
    while stack or root:
        if root:
            stack.append(root)
            root = root.left
        else:
            tempNode = stack.pop()
            ans.append(tempNode.val)
            root = tempNode.right
    return ans
```