---
layout: post
title:  "Complex Number Multiplication"
date:   2017-06-28
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/d6dcd653396079.5932e355d2912.jpg
categories: algorithm
tag:
- leetcode
- math
- medium
---
### Question:
Given two strings representing two complex numbers.

You need to return a string representing their multiplication. Note \\(i^2 = -1\\) according to the definition.

### Example 1:
```
Input: "1+1i", "1+1i"
Output: "0+2i"
Explanation: (1 + i) * (1 + i) = 1 + i2 + 2 * i = 2i, and you need convert it to the form of 0+2i.
```

### Example 2:
```
Input: "1+-1i", "1+-1i"
Output: "0+-2i"
Explanation: (1 - i) * (1 - i) = 1 + i2 - 2 * i = -2i, and you need convert it to the form of 0+-2i.
```

### Note:
1. The input strings will not have extra blank.
2. The input strings will be given in the form of __a+bi__, where the integer __a__ and __b__ will both belong to the range of [-100, 100]. And __the output should be also in this form__.

### Solution：
split the real part and imaginary part and calculate it as math definition.

```python
def complexNumberMultiply(self, a, b):
    """
    :type a: str
    :type b: str
    :rtype: str
    """
    l1 = a.split("+")
    l2 = b.split("+")
    realA = int(l1[0])
    realB = int(l2[0])
    imgA = int(l1[1][:-1])
    imgB = int(l2[1][:-1])
	real = realA * realB - imgA * imgB
    img = realA * imgB + realB * imgA
    return str(real)+ "+" + str(img) + "i"
```
### A pythonic way to solve this problem
```python
def complexNumberMultiply(self, a, b):
	"""
	:type a: str
	:type b: str
	:rtype: str
	"""
	extract = lambda s: map(int, s[:-1].split('+'))
	m, n = extract(a)
	p, q = extract(b)
	return '%s+%si' % (m * p - n * q, n * p + m * q)
```
