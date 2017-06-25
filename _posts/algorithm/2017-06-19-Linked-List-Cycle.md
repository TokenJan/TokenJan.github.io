---
layout: post
title:  "Linked List Cycle"
date:   2017-06-19
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/39506c49535589.58b77ea8a36f5.jpg
categories: algorithm
tag:
- leetcode
- linked list
- two pointers
- easy
---
### Question: 
Given a linked list, determine if it has a cycle in it.

### Follow up:
Can you solve it without using extra space?

### Solution：
- Use fast and slow pointers
- If the linked list has a cycle, these two pointers will point the same object at certain step


```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None
def hasCycle(self, head):
    """
    :type head: ListNode
    :rtype: bool
    """
    if head is None:
        return False
    slow = head
    try:
        fast = head.next
        while slow is not fast:
            slow = slow.next
            fast = fast.next.next
        return True
    except:
        return False
```