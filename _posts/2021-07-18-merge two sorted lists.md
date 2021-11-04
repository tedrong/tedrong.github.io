---
title: Merge Two Sorted Lists
author: Ted Rong
date: 2021-07-18 00:00:00 +0800
categories: [LeetCode, Easy]
tags: [leetcode]
math: true
mermaid: true
---

Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

#### Example 1
![alt tag](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)
```
Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]
```
#### Example 2
```
Input: l1 = [], l2 = []
Output: []
```
#### Example 3
```
Input: l1 = [], l2 = [0]
Output: [0]
```

#### Constraints
- The number of nodes in both lists is in the range [0, 50].
- -100 <= Node.val <= 100
- Both l1 and l2 are sorted in non-decreasing order.

#### Solution
```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
    if l1 == nil { return l2 }
    if l2 == nil { return l1 }
    if l1.Val < l2.Val {
        l1.Next = mergeTwoLists(l1.Next, l2)
        return l1
    } else {
        l2.Next = mergeTwoLists(l1, l2.Next)
        return l2
    }
}
```