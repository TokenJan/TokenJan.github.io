---
layout: post
title:  "Inverse Binary Tree"
date:   2017-07-05
feature: https://mir-s3-cdn-cf.behance.net/project_modules/max_1200/15fde053396079.5932e355d49b6.jpg
categories: algorithm
tag:
- leetcode
- binary tree
- easy
---
### Question:
Invert a binary tree.

```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
to
```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

>Google: 90% of our engineers use the software you wrote (Homebrew), but you can’t invert a binary tree on a whiteboard so fuck off.

### Solution:
__recursion version:__
```python
def invertTree(self, root):
    """
    :type root: TreeNode
    :rtype: TreeNode
    """
    if root:
        root.left, root.right =  self.invertTree(root.right),  self.invertTree(root.left)
        return root
```

__iterative version:__ stack is used
```python
def invertTree(self, root):
    """
    :type root: TreeNode
    :rtype: TreeNode
    """
    stack = [root]
    while stack:
        node = stack.pop()
        if node:
            node.left, node.right = node.right, node.left
            stack += node.left, node.right
    return root
```