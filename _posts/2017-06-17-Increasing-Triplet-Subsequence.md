---
layout: post
title:  "Increasing Triplet Subsequence"
date:   2017-06-16
feature: https://mir-s3-cdn-cf.behance.net/project_modules/1400/35ced149535589.58b77ea8a4cbd.jpg
tag:
- algorithm
- leetcode
---
Question: Given an unsorted array return whether an increasing subsequence of length 3 exists or not in the array.
Formally the function should:
>### Return true if there exists i, j, k 
>### such that arr[i] < arr[j] < arr[k] given 0 ≤ i < j < k ≤ n-1 else return false.

Your algorithm should run in \\(O\(n\)\\) time complexity and \\(O\(1\)\\) space complexity.

__Examples:__<br/>
Given `[1, 2, 3, 4, 5]`,<br/>
return `true`<br/>
Given `[5, 4, 3, 2, 1]`,<br/>
return `false`

### First thought solution
This solution is intuitive but not elegant and difficult to understand.
```python
    def increasingTriplet(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        seq = []
        for num in nums:
            if len(seq) == 0:
                seq.append(num)
            elif len(seq) == 1:
                if num <= seq[0]:
                    seq[0] = num
                else:
                    seq.append(num)
            elif len(seq) == 2:
                if num < seq[0]:
                    seq.append(num)
                elif seq[0] <= num and seq[1] >= num:
                    seq.append(num)
                else:
                    return True
            elif len(seq) == 3:
                if seq[2] <= seq[0]:
                    if num > seq[1]:
                        return True
                    elif num > seq[2] and num < seq[1]:
                        seq.append(num)
                        del seq[0:1]
                    elif num < seq[2]:
                        seq[2] = num
                else:
                    if num > seq[2]:
                        return True
                    else:
                        seq[2] = num
        return False
```