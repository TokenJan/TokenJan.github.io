---
layout: post
title:  "what is dynamic programming? (1)"
date:   2017-06-10
tag:
- algorithm
- dynamic programming
---

Question: There are 10 stairs, a person standing at the bottom wants to reach the top. The person can climb either 1 stair or 2 stairs at a time. Count the number of ways, the person can reach the top.

![10 stairs problem(1)](https://github.com/TokenJan/TokenJan.github.io/blob/master/assets/img/dp_problem(1).jpg?raw=true)
{: .image-left}


![10 stairs problem(2)](https://github.com/TokenJan/TokenJan.github.io/blob/master/assets/img/dp_problem(2).jpg?raw=true)
{: .image-center}


![10 stairs problem(3)](https://github.com/TokenJan/TokenJan.github.io/blob/master/assets/img/dp_problem(3).jpg?raw=true)
{: .image-right}

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

## iterative version
However, the time and space complexity of recursion method are \\(O\(n^{2}\)\\), which can be optimized to __linear__ complexity with iterative version.
```python
# iterative version
# time complexity: O(n) --- 2.09808349609e-05 seconds ---
# space complexity: O(n)
def iterative (num):
    results = [1,2]
    for i in range(num-2):
        results.append(results[i]+results[i+1])
    return results[num-1]

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