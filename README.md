## JavaScript Algorithm Solutions from Leetcode

An algorithm is a series of step-by-step instructions that describe how to do something.

To write an effective algorithm, it helps to break a problem down into smaller parts and think carefully about how to solve each part with code.

This repository contains JavaScript algorithm examples and solutions from Leetcode.

All of these examples are from FreeCodeCamp's [problemset](https://leetcode.com/problemset/all/).

### **1. Two Sum**

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

### Solution 1

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

### Solution 2

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
