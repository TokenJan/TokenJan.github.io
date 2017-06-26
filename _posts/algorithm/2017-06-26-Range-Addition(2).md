---
layout: post
title:  "Range Addition II"
date:   2017-06-26
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/a00e1353396079.5932e355d3d7d.jpg
categories: algorithm
tag:
- leetcode
- math
- easy
---
### Question:
Given an m * n matrix __M__ initialized with all __0__'s and several update operations.

Operations are represented by a 2D array, and each operation is represented by an array with two __positive__ integers __a__ and __b__, which means __M[i][j]__ should be added by one for all __0 <= i < a__ and __0 <= j < b__.

You need to count and return the number of maximum integers in the matrix after performing all the operations.

### Example:
```
Input:
m = 3, n = 3
operations = [[2,2],[3,3]]
Output: 4
Explanation:
Initially, M =
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]

After performing [2,2], M =
[[1, 1, 0],
 [1, 1, 0],
 [0, 0, 0]]

After performing [3,3], M =
[[2, 2, 1],
 [2, 2, 1],
 [1, 1, 1]]

So the maximum integer in M is 2, and there are four of it in M. So return 4.
```

### Note:
1. The range of m and n is [1,40000].
2. The range of a is [1,m], and the range of b is [1,n].
3. The range of operations size won't exceed 10,000.

### Solution：
The area is the multiplication of two smallest sides in operations
```python
def maxCount(self, m, n, ops):
    """
    :type m: int
    :type n: int
    :type ops: List[List[int]]
    :rtype: int
    """
    for i in range(len(ops)):
        m = min(ops[i][0], m)
        n = min(ops[i][1], n)
    return m*n
```