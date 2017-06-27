---
layout: post
title:  "Valid Square"
date:   2017-06-27
feature: https://mir-s3-cdn-cf.behance.net/project_modules/max_1200/b75b0d53396079.5932e355d4cdb.jpg
categories: algorithm
tag:
- leetcode
- math
- medium
---
### Question:
Given the coordinates of four points in 2D space, return whether the four points could construct a square.

The coordinate (x, y) of a point is represented by an integer array with two integers.

### Example:
```
Input: p1 = [0,0], p2 = [1,1], p3 = [1,0], p4 = [0,1]
Output: True
```

### Note:
1. All the input integers are in the range [-10000, 10000].
2. A valid square has four equal sides with positive length and four equal angles (90-degree angles).
3. Input points have no order.

### Solution：
1. Calculate all six distances between the points
2. Put the distances into the dictionary with distance as the key and frequency as the value
3. Valid square should require following two conditions:
	1. One value among the distance should appear twice (diagonal)
	while the other value shoud appear four times (side)
	2. The side and diagonal should meet Pythagorean theorem: \\(a^2 + b^2 = c^2\\)

```python
def validSquare(self, p1, p2, p3, p4):
	"""
	:type p1: List[int]
	:type p2: List[int]
	:type p3: List[int]
	:type p4: List[int]
	:rtype: bool
	"""
	d = dict()
	dist = range(6)
	dist[0] = (p1[0] - p2[0])**2 + (p1[1] - p2[1])**2
	dist[1] = (p1[0] - p3[0])**2 + (p1[1] - p3[1])**2
	dist[2] = (p1[0] - p4[0])**2 + (p1[1] - p4[1])**2
	dist[3] = (p2[0] - p3[0])**2 + (p2[1] - p3[1])**2
	dist[4] = (p2[0] - p4[0])**2 + (p2[1] - p4[1])**2
	dist[5] = (p3[0] - p4[0])**2 + (p3[1] - p4[1])**2

	for i in dist:
		if i not in d.keys():
			d[i] = 1
		else:
			d[i] += 1
	return (set(d.values()) == set([2,4]) and 2*min(d.keys()) == max(d.keys()))
```