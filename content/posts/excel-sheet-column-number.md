---
title:  "[LeetCode] 171. Excel Sheet Column Number"
date:   2019-09-05
comments: true
author: Debakar Roy
authorLink: https://github.com/debakarr
tags: ["Algorithms", "Excel", "Column Number", "Programming"]
categories: ["Algorithms", "Programming", "LeetCode"]
---

### Excel Sheet Column Number
 
[Link to original Problem on LeetCode](https://leetcode.com/problems/excel-sheet-column-number)

Given a column title as appear in an Excel sheet, return its corresponding column number.

**For example**:

<pre>
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...

</pre>

**Example 1**:

**Input**: "A"

**Output**: 1


**Example 2**:

**Input**: "AB"

**Output**: 28


**Example 3**:

**Input**: "ZY"

**Output**: 701

**Company:**
*Amazon*

**Solution (Using Hash Map):**

**Time Complexity:** O(n)
**Space Complexity:** O(1)

```python
class Solution(object):
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        # First create a dictionary containing key 'A' to 'Z' 
        # assigning 'A': 1, 'B': 2, 'C': 3, ..., 'Z': 26
        # For element in position i, value = (26 ^ i) x (character number)
        # eg: if A is in 3rd position from left,
        # value = (26 ^ 2) x 1 = 676
        # We just need to add up all the values
        charDict = {chr(x): x - 64 for x in range(65, 65 + 26)}
        
        columnNumber = 0
        for i, char in enumerate(reversed(s)):
            columnNumber += 26 ** i * charDict[char]
            
        return columnNumber
```

<hr><br />
