## JavaScript Algorithm Solutions from Leetcode

An algorithm is a series of step-by-step instructions that describe how to do something.

To write an effective algorithm, it helps to break a problem down into smaller parts and think carefully about how to solve each part with code.

This repository contains JavaScript algorithm examples and solutions from Leetcode.

All of these examples are from FreeCodeCamp's [problemset](https://leetcode.com/problemset/all/).

## **1. Two Sum**

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have **exactly one solution**, and you may not use the same element twice.

You can return the answer in any order.

**Example 1:**

```js
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:
```

```js
Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:
```

```js
Input: (nums = [3, 3]), (target = 6);
Output: [0, 1];
```

**Constraints:**

- 2 <= nums.length <= 104
- -109 <= nums[i] <= 109
- -109 <= target <= 109
- **Only one valid answer exists.**

### **Solution 1**

The space complexity for this solution is a constant O(1).

The time complexity for this solution is O(N)^2, as we are looping over the array twice.

```js
var twoSum = function (nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
};
```

To improve the first solution we can improve time complexity by sacrificing space and creating an object and storing the difference between the index of nums array and the target value.

The space complexity for this solution is O(N).

The time complexity for this solution is O(N).

### **Solution 2**

```js
var twoSum = function (nums, target) {
  let numsStorage = {};
  for (let i = 0; i < nums.length; i++) {
    if (numsStorage[nums[i]] === undefined) {
      numsStorage[target - nums[i]] = i;
    } else {
      return [numsStorage[nums[i]], i];
    }
  }
};
```

## **Palindrome Number**

Given an integer x, return true if x is palindrome integer.

An integer is a palindrome when it reads the same backward as forward.

For example, 121 is a palindrome while 123 is not.

**Example 1**:

```js
Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
```

**Example 2**:

```js
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

**Example 3**:

```js
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

Constraints:

- -231 <= x <= 231 - 1

### **Solution 1**

The space complexity for this solution is O(N).

The time complexity for this solution is O(N).

```js
var isPalindrome = function (x) {
  let splitNumber = x.toString().split("");
  let reverseNumberArr = [];
  for (let i = splitNumber.length; i > -1; i--) {
    reverseNumberArr.push(splitNumber[i]);
  }
  return Number(reverseNumberArr.join("")) === x;
};
```

### **Solution 2**

The space complexity for this solution is a constant O(1).

The time complexity for this solution is also O(1).

```js
var isPalindrome = function (x) {
  return x.toString() === x.toString().split("").reverse().join("");
};
```

## **Roman to Integer**

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

```js
Symbol Value
I 1
V 5
X 10
L 50
C 100
D 500
M 1000
```

For example, 2 is written as II in Roman numeral, just two ones added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9.
X can be placed before L (50) and C (100) to make 40 and 90.
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.

**Example 1**:

```js
Input: s = "III";
Output: 3;
Explanation: III = 3;
```

**Example 2**:

```js
Input: s = "LVIII";
Output: 58;
Explanation: (L = 50), (V = 5), (III = 3);
```

```js
Example 3:
Input: s = "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

**Constraints**:

- 1 <= s.length <= 15
- s contains only the characters ('I', 'V', 'X', 'L', 'C', 'D', 'M').
- It is guaranteed that s is a valid roman numeral in the range [1, 3999].

## **Solution**

```js
var romanToInt = (s) => {
  let result = 0;
  const romanVal = { I: 1, V: 5, X: 10, L: 50, C: 100, D: 500, M: 1000 };

  for (let i = 0; i < s.length; i++) {
    if (romanVal[s[i]] < romanVal[s[i + 1]]) {
      result -= romanVal[s[i]];
    } else {
      result += romanVal[s[i]];
    }
  }
  return result;
};
```

## Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

**Example 1**:

```js
Input: strs = ["flower", "flow", "flight"];
Output: "fl";
```

**Example 2**:

```js
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Constraints**:

- 1 <= strs.length <= 200
- 0 <= strs[i].length <= 200
- strs[i] consists of only lowercase English letters.

## **Solution**

```js
var longestCommonPrefix = function (strs) {
  if (!strs.length) return "";

  for (let i = 0; i < strs[0].length; i++) {
    for (let j = 1; j < strs.length; j++) {
      if (strs[0][i] !== strs[j][i]) {
        return strs[0].slice(0, i);
      }
    }
  }

  return strs[0];
};
```
