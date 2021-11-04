---
title: Length of Last Word
author: Ted Rong
date: 2021-07-24 00:00:00 +0800
categories: [LeetCode, Easy]
tags: [leetcode]
math: true
mermaid: true
---

Given a string s consisting of some words separated by some number of spaces, return the length of the last word in the string.

A word is a maximal substring consisting of non-space characters only.

#### Example 1
```
Input: s = "Hello World"
Output: 5
Explanation: The last word is "World" with length 5.
```
#### Example 2
```
Input: s = "   fly me   to   the moon  "
Output: 4
Explanation: The last word is "moon" with length 4.
```
#### Example 3
```
Input: s = "luffy is still joyboy"
Output: 6
Explanation: The last word is "joyboy" with length 6.
```

#### Constraints
- 1 <= s.length <= 104
- s consists of only English letters and spaces ' '.
- There will be at least one word in s.

#### Solution
```golang
func lengthOfLastWord(s string) int {
	words := []byte(s)
	length := 0
	if strings.Contains(s, " ") {
		for i := len(words) - 1; i >= 0; i-- {
			// fmt.Println(words[i])
			if i == len(words)-1 && words[i] == 32 {
				words = words[:len(words)-1]
			} else if words[i] != 32 {
				length++
			} else {
				break
			}
		}
	} else {
		length = len(s)
	}
    return length
}
```