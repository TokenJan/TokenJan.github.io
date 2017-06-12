---
layout: post
title:  "simple character set"
date:   2017-06-12
feature: http://i.imgur.com/Ds6S7lJ.png
tag:
- algorithm
- string
---
Question: Input a string, output a set of the included characters.
- Input: the string is up to 100 length, only include letters, cannot be empty and case sensitive.
- Output: keep the original order of the characters.

Example:
- Input: `abcqweracb`
- Output: `abcqwer`

Since we use a new string to record the result, the space complexity is __\\(O\(n\)\\)__
```python
# use a new string and check character one by one
# time complexity: O(n)
# space complexity: O(n)
def getSet(str):
	result = ""
	for i in str:
		if(i not in result):
			result += i
	return result

print(getSet(text))
```