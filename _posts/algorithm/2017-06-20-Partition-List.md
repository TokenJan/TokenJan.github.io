---
layout: post
title:  "Partition List"
date:   2017-06-20
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/0a317c49535589.58b77ea8a560e.jpg
categories: algorithm
tag:
- algorithm
- leetcode
- linked list
- two pointers
- medium
---
### Question: 
Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

### Example:
Given `1->4->3->2->5->2` and `x = 3`,

return `1->2->2->4->3->5`.

### Solution：
- Since there is no limitation on space complexity, we can create another two linked lists
- One list is used to record the nodes whose value is smaller than `x`
- The other list is used to record the nodes whose value is larger or equal to `x`
- Concatenate these two lists

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None
def partition(self, head, x):
    """
    :type head: ListNode
    :type x: int
    :rtype: ListNode
    """
    h1 = l1 = ListNode(0)
    h2 = l2 = ListNode(0)
    while head:
        if head.val < x:
            l1.next = head
            l1 = l1.next
        else:
            l2.next = head
            l2 = l2.next
        head = head.next
    l2.next = None
    l1.next = h2.next
    return h1.next
```