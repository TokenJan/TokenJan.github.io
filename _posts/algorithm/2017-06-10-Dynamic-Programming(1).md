---
layout: post
title:  "10 steps problem"
date:   2017-06-10
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/f0ec3c49535589.58b77ea8a64b4.jpg
categories: algorithm
tag:
- algorithm
- dynamic programming
---

Question: There are 10 stairs, a person standing at the bottom wants to reach the top. The person can climb either 1 stair or 2 stairs at a time. Count the number of ways, the person can reach the top.

![10 stairs problem(1)](https://github.com/TokenJan/TokenJan.github.io/blob/master/assets/img/dp_problem(1).jpg?raw=true)
{: .image-center}

## recursion version
Since the number of ways to reach the \\(10^{th}\\) is the sum of the number of ways to reach the \\(9^{th}\\) and the \\(8^{th}\\). That is `F(10) = F(9) + F(8)`, and it is known that `F(1) = 1` and `F(2) = 2`. So we can use a recursion to solve this problem.

```python
# recursion version
# time complexity: O(2^n) --- 0.00142097473145 seconds ---
# space complexity: O(2^n)
def recursion (num):
    if (num > 2):
        return recursion(num-1) + recursion(num-2)
    elif (num == 2):
        return 2
    elif (num == 1):
        return 1
    else:
        print("please input a positive number.")
```

## recursion with reminder version
However, the time and space complexity of recursion method are \\(O\(n^{2}\)\\), which can be optimized to __linear__ complexity with recursion with reminder version.
```python
# recursion with reminder version
# time complexity: O(n) --- 2.09808349609e-05 seconds ---
# space complexity: O(1)
def recursion_reminder (num):
    if (num > 2):
        if (num in reminder):
            return reminder.get(num)
        else:
            value = recursion_reminder(num-1) + recursion_reminder(num-2)
            reminder[num] = value
            return value
    elif (num == 2):
        return 2
    elif (num == 1):
        return 1
    else:
        print("please input a positive number.")
```

## dynamic programming version
By using dynamic programming, we can optimize the space complexity to __constant__.
```python
# dynamic programming version
# time complexity: O(n) --- 1.90734863281e-05 seconds ---
# space complexity: O(1)
def dp (num):
    firstNum = 1
    secNum = 2
    for i in range(num-2):
        secNum, firstNum = firstNum + secNum, secNum
    return secNum
```