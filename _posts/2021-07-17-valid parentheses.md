---
title: Valid Parentheses
author: Ted Rong
date: 2021-07-17 00:00:00 +0800
categories: [LeetCode, Easy]
tags: [leetcode]
math: true
mermaid: true
---

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
An input string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

#### Example 1
```
Input: s = "()"
Output: true
```
#### Example 2
```
Input: s = "()[]{}"
Output: true
```
#### Example 3
```
Input: s = "([)]"
Output: false
```

#### Constraints
- 1 <= s.length <= 104
- s consists of parentheses only '()[]{}'.

#### Solution
```golang
func isValid(s string) bool {
    m := make(map[string]string)
	m[")"] = "("
	m["]"] = "["
	m["}"] = "{"

	stack := []string{}
	for _, symbol := range strings.Split(s, "") {
		if strings.Contains("([{", symbol) {
			stack = append(stack, symbol)
        } else if len(stack) > 0{
			// fmt.Printf("stack : %s, map: %s\n", stack[len(stack)-1], m[symbol])
			// fmt.Println(stack[len(stack)-1] == m[symbol])
			if stack[len(stack)-1] == m[symbol] {
				stack = stack[:len(stack)-1]
            } else {
                return false
            }
        } else {
            return false
        }
	}
	if len(stack) == 0 {
		return true
	}
    return false
}
```