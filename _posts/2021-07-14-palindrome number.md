---
title: Palindrome Number
author: Ted Rong
date: 2021-07-14 00:00:00 +0800
categories: [LeetCode, Easy]
tags: [leetcode]
math: true
mermaid: true
---

Given an integer x, return true if x is palindrome integer.
An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.

#### Example 1
```
Input: x = 121
Output: true
```
#### Example 2
```
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```
#### Example 3
```
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

#### Constraints
- -231 <= x <= 231 - 1

#### Solution
```golang
func isPalindrome(x int) bool {
    ans := true
	digits := strings.Split(strconv.Itoa(x), "")
	for idx, digit := range digits {
		tail := len(digits) - 1 - idx
		if idx == tail || idx > tail {
			break
		}
		if digit != digits[tail] {
			ans = false
			break
		}
	}
    return ans
}
```