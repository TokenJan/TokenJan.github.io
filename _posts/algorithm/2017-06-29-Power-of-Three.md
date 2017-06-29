---
layout: post
title:  "Power of three"
date:   2017-06-29
feature: https://mir-s3-cdn-cf.behance.net/project_modules/max_1200/fcb49853396079.5932e355d399c.jpg
categories: algorithm
tag:
- leetcode
- math
- easy
---
### Question:
Given an integer, write a function to determine if it is a power of three.

### Follow up:
Could you do it without using any loop / recursion?

### Solution：
__recursion version:__ too much space is required
>Error: maximum recursion depth exceeded.

```python
def isPowerOfThree(self, n):
    """
    :type n: int
    :rtype: bool
    """
    if (n == 1):
        return True
    if (n%3 == 0):
        return self.isPowerOfThree(n/3)
    else:
        return False
```

__iterative version:__ too much time is required
>Time Limit Exceeded

```python
def isPowerOfThree(self, n):
    """
    :type n: int
    :rtype: bool
    """
    if (n == 1):
        return True        
    while(n%3 == 0):
        n = n/3
        if (n == 1):
            return True
    return False
```

__math version:__
1162261467 is \\(3^{19}\\),  \\(3^{20}\\) is bigger than int  
```python
def isPowerOfThree(self, n):
    """
    :type n: int
    :rtype: bool
    """
    return ( n>0 and 1162261467%n == 0);
```
