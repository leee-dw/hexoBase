---
title: level Easy. Two Sum
categories: Algorithm
date: 2017-12-12 10:47:17
---

## 문제
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.


Example:
```javascript
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
- 출처: https://leetcode.com/problems/two-sum/description/


### 나의 풀이
```javascript
var twoSum = function(nums, target) {
  for (var i = 0; i < nums.length; i++) {
    for (var j = i + 1; j < nums.length; j++) {
        if(nums[i] + nums[j] === target) {
            return [i, j]
        }
      }
    }
  };
```
C 언어 스타일의 알고리즘 풀이.


### 다른사람의 풀이
```javascript
var twoSum = function(nums, target) {
  for (var i = 0; i < nums.length; i++) {
    var x = target - nums[i];
    var idx = nums.lastIndexOf(x);
    if (idx > i) {
      return [i, idx]
    }
  }
};
```
자바스크립트의 스타일을 활용하여 문제 해결
indexOf를 사용하면 루프를 한 번만 써서 간단해 보이지만, 사실 indexOf는 루프를 두 번 도는 것과 똑같다.


