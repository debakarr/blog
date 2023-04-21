---
title:  "[LeetCode] 88. Merge Sorted Array"
date:   2019-06-17
comments: true
author: Debakar Roy
authorLink: https://github.com/debakarr
tags: ["Merge Sorted Array", "Two Pointers", "Array", "LeetCode", "Algorithm"]
categories: ["Programming", "Algorithms", "LeetCode"]
---

### Merge Sorted Array
 
[Link to original Problem on LeetCode](https://leetcode.com/problems/merge-sorted-array/)

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

**Note:**

* The number of elements initialized in nums1 and nums2 are m and n respectively.
* You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.

**Example:**

>Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

>Output: [1,2,2,3,5,6]

**Company:**
*Adobe*, *Expedia*, *Microsoft*



**Solution:**

```python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: None Do not return anything, modify nums1 in-place instead.
        """
        # We can start comparing from the end of each array
        # Note for 1st array end is specified by m
        # We can swap after comparing
        # The largest elemtn will go to the end of 1st array
        # Which is actually a 0
        while m > 0 and n > 0:
            if nums2[n - 1] >= nums1[m - 1]:
                nums1[m + n - 1] = nums2[n - 1]
                n -= 1
            else:
                nums1[m + n - 1] = nums1[m - 1]
                m -= 1
                
        # If the first array is completed traversing before second
        # Put all the remaining element of second element inside 1st array
        # while n > 0:
        #     nums1[n - 1] = nums2[n - 1]
        #     n -= 1
        if n > 0:
            nums1[:n] = nums2[:n]
```

<hr><br />

