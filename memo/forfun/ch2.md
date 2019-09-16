Leet Code 习题册

### Q1 两数之和

**题目**:

> Given an array of integers, return indices of the two numbers such that they add up to a specific target.
> You may assume that each input would have exactly one solution, and you may not use the same element twice.

**参考答案**：

方案1： 双游标顺序遍历寻找

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = nums.length-1; j > i; j--) {
                if ( nums[i] + nums[j] == target){
                    return new int[] {i, j};
                }
            }
        }
        return null;
    }
}
```

分析： 任意时候，额外开销只有两个游标，所以占用空间很小，空间复杂度为O(1)，但是由于需要嵌套循环，故时间复杂度为O(n^2)

方案2： 使用HashMap

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>(nums.length*2);
        for(int i = 0; i < nums.length; i++) {
            int num = target - nums[i]
            if (map.containsKey(num)){
                return new int[] {map.get(num), i};
            } else {
                map.put(nums[i], i);
            }
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
```

分析： 最差情况，map的可用容积被沾满，长度为n-1，实际占用空间（n-1）/0.75，空间复杂度O(n)，时间复杂度O(n)


## 2.两数相加

### 题目：

>给出两个**非空**的链表用来表示两个非负的整数。其中，它们各自的位数是按照**逆序**的方式存储的，并且它们的每个节点只能存储**一位**数字。
>
>如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。
>
>您可以假设除了数字**0**之外，这两个数都不会以**0**开头。
>
>**示例**：
>
>**输入**：(2 -> 4 -> 3) + (5 -> 6 -> 4)
>**输出**：7 -> 0 -> 8
>**原因**：342 + 465 = 807

### 思路

### 参考

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        if (l1 != null && l2 != null) {
            l1.val += l2.val;
            int up = l1.val/10;
            l1.val = l1.val%10;
            if(up > 0){
                if(l1.next != null) {
                    l1.next.val += up;
                } else {
                    l1.next = new ListNode(up);
                }
            }
            l1.next = addTwoNumbers(l1.next, l2.next);
            return l1;
        } else {
            return l1 == null ? l2
                :addTwoNumbers(l1, new ListNode(0));
        }
    }
}
```

## 3.无重复字符的最长子串

### 题目：

给定一个字符串，请你找出其中不含有重复字符的**最长子串**的长度。

**示例 1**:

> 输入: "abcabcbb"
> 输出: 3
> 解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

**示例 2**:

> 输入: "bbbbb"
> 输出: 1
> 解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。

**示例 3**:

> 输入: "pwwkew"
> 输出: 3
> 解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
> *请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。*

### 思路

使用滑动窗口，右侧游标每前进一格，随即比对窗口内有没有和右侧游标扫过字符重复的字符。如果有，左侧游标移动至重复字符后一个的位置，如果没有则左侧游标不移动。比对每次移动后滑动窗口的宽度，保留最大值，直到右侧游标抵达字符串末尾，返回最大值。

### 参考

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int max = 0;
        int from = 0;
        for(int i = 0; i < n; i++) {
            for(int j = from; j < i; j++) {
                if(s.charAt(j) == s.charAt(i)) {
                    from = j + 1;
                    break;
                }
            }
            max = max > i - from + 1 ? max : i - from + 1;
        }
        return max;
    }
}
```

## 4.寻找两个有序数组的中位数

### 题目

> 给定两个大小为`m`和`n`的有序数组`nums1`和`nums2`。
>
> 请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为`O(log(m + n))`。
>
> 你可以假设`nums1`和`nums2`不会同时为空。
>
> **示例 1**:
>
> nums1 = [1, 3]
> nums2 = [2]
>
> 则中位数是 2.0
>
> **示例 2**:
>
> nums1 = [1, 2]
> nums2 = [3, 4]
>
> 则中位数是 (2 + 3)/2 = 2.5

### 思路

### 参考


