---
title: Search Insert Position
author: Ted Rong
date: 2021-07-22 00:00:00 +0800
categories: [LeetCode, Easy]
tags: [leetcode]
math: true
mermaid: true
---

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

#### Example 1
```
Input: nums = [1,3,5,6], target = 5
Output: 2
```
#### Example 2
```
Input: nums = [1,3,5,6], target = 2
Output: 1
```
#### Example 3
```
Input: nums = [1,3,5,6], target = 7
Output: 4
```
#### Example 4
```
Input: nums = [1,3,5,6], target = 0
Output: 0
```
#### Example 5
```
Input: nums = [1], target = 0
Output: 0
```

#### Constraints
- 1 <= nums.length <= 104
- -104 <= nums[i] <= 104
- nums contains distinct values sorted in ascending order.
- -104 <= target <= 104

#### Solution
```golang
func searchInsert(nums []int, target int) int {
    for idx, element := range nums {
        if element >= target {
            if idx == 0 {
                return 0
            }
            return idx
        }
    }
    return len(nums)
}
```