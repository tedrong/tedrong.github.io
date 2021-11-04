---
title: Longest Common Prefix
author: Ted Rong
date: 2021-07-16 00:00:00 +0800
categories: [LeetCode, Easy]
tags: [leetcode]
math: true
mermaid: true
---

Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "".

#### Example 1
```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```
#### Example 2
```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

#### Constraints
- 1 <= strs.length <= 200
- 0 <= strs[i].length <= 200
- strs[i] consists of only lower-case English letters.

#### Solution
```golang
func longestCommonPrefix(strs []string) string {
    // Get shortest string
	length := 200
	prefix := ""
	for _, str := range strs {
		if len(str) < length {
			length = len(str)
			prefix = str
		}
	}
	for i := 0; i < length; i++ {
		for _, str := range strs {
			if !strings.HasPrefix(str, prefix) {
				prefix = prefix[:len(prefix)-1]
				break
			}
		}
	}
    return prefix
}
```