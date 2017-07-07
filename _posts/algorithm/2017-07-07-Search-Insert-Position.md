---
layout: post
title:  "Search Insert Position"
date:   2017-07-07
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/7b2ff953396079.5932e355d423b.jpg
categories: algorithm
tag:
- leetcode
- array
- easy
---
### Question:
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

### Example:
`[1,3,5,6]`, 5 → 2

`[1,3,5,6]`, 2 → 1

`[1,3,5,6]`, 7 → 4

`[1,3,5,6]`, 0 → 0

### Solution:
__Sequential search:__ \\(O(n)\\)
```python
def searchInsert(self, nums, target):
    """
    :type nums: List[int]
    :type target: int
    :rtype: int
    """
    for i in range(len(nums)):
        if nums[i] >= target:
            return i
    return len(nums)
```

__Binary search:__ \\(O(log(n))\\)
```python
def searchInsert(self, nums, target):
    """
    :type nums: List[int]
    :type target: int
    :rtype: int
    """
    low = 0
    high = len(nums) - 1
    if nums[0] >= target:
        return 0
    elif nums[-1] < target:
        return high + 1
    while (low < high):
        mid = (low + high)/2
        if (nums[mid] == target):
            return mid
        elif (nums[mid] < target):
            low = mid + 1
        else:
            high = mid
    return low
```
