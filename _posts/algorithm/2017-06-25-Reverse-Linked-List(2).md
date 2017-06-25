---
layout: post
title:  "Reverse Linked List II"
date:   2017-06-25
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/b8922849535589.58ba16641fd50.jpg
categories: algorithm
tag:
- leetcode
- linked list
- medium
---
### Question: 
Reverse a linked list from position m to n. Do it in-place and in one-pass.

### Example:
Given `1->2->3->4->5->NULL`, m = 2 and n = 4,

return `1->4->3->2->5->NULL`.

### Note:
Given m, n satisfy the following condition:
1 < m < n < length of list.

### Solution：
Time complexity: \\(O\(n\)\\)

Space complexity: \\(O\(1\)\\)

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None
def reverseBetween(self, head, m, n):
    """
    :type head: ListNode
    :type m: int
    :type n: int
    :rtype: ListNode
    """
    dummy = ListNode(0)		# create a dummy node to mark the head of this list
    dummy.next = head
    pre = dummy 		# make a pointer pre as a marker for the node before reversing
    for i in range(m-1):
        pre = pre.next
    start = pre.next 		# a pointer to the beginning of a sub-list that will be reversed
    then = start.next 		# a pointer to a node that will be reversed

    # 1 - 2 -3 - 4 - 5 ; m=2; n =4 ---> pre = 1, start = 2, then = 3
    # dummy-> 1 -> 2 -> 3 -> 4 -> 5
    
    for j in range(n-m):
        pre.next, then.next, start.next, then = then, pre.next, then.next, then.next

    ## first reversing : dummy->1 - 3 - 2 - 4 - 5; pre = 1, start = 2, then = 4
    ## second reversing: dummy->1 - 4 - 3 - 2 - 5; pre = 1, start = 2, then = 5 (finish)

    return dummy.next
```