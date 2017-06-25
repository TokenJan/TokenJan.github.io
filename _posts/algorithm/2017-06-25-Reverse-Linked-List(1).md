---
layout: post
title:  "Reverse Linked List I"
date:   2017-06-25
feature: https://mir-s3-cdn-cf.behance.net/project_modules/max_1200/68bb1f53396079.5932e355d594f.jpg
categories: algorithm
tag:
- leetcode
- linked list
- easy
---
### Question: 
Reverse a singly linked list.

### Example:
Given `1->2->3->4->5->NULL`,

return `5->4->3->2->1->NULL`.

### Solution：
Time complexity: \\(O\(n\)\\)

Space complexity: \\(O\(1\)\\)

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None
def reverseList(self, head):
"""
:type head: ListNode
:rtype: ListNode
"""
    dummy = ListNode(0)
    dummy.next = head

    # dummy -> 1(head) -> 2 -> 3 -> 4 -> 5
    # dummy -> 2 -> 1(head) -> 3 -> 4 -> 5
    # dummy -> 3 -> 2 -> 1(head) -> 4 -> 5
    # dummy -> 4 -> 3 -> 2 -> 1(head) -> 5
    # dummy -> 5 -> 4 -> 3 -> 2 -> 1(head)

    while (head and head.next):
        dummy.next, head.next.next, head.next  = head.next, dummy.next, head.next.next
    return dummy.next
```