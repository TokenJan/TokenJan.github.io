---
layout: post
title:  "Increasing Triplet Subsequence"
date:   2017-06-16
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/35ced149535589.58b77ea8a4cbd.jpg
tag:
- algorithm
- leetcode
- medium
---
### Question:
Given an unsorted array return whether an increasing subsequence of length 3 exists or not in the array.
Formally the function should:
>### Return true if there exists i, j, k 
>### such that arr[i] < arr[j] < arr[k] given 0 ≤ i < j < k ≤ n-1 else return false.

Your algorithm should run in \\(O\(n\)\\) time complexity and \\(O\(1\)\\) space complexity.

### Examples:
- Given `[1, 2, 3, 4, 5]`, return `true`
- Given `[5, 4, 3, 2, 1]`, return `false`

### Solution:
Only record the first and second smallest number.
```python
    def increasingTriplet(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        g1, g2 = float('inf'), float('inf')
        
        for num in nums:
            if num <= g1:
                g1 = num
            elif num <= g2:
                g2 = num
            else:
                return True
        return False
```