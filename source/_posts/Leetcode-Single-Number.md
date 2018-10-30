---
title: 'Leetcode: Single Number'
categories: Algorithm
date: 2018-06-06 18:29:53
tag: Leet Code

---
출처: https://leetcode.com/problems/single-number/description/

```js
let singleNumber = function (nums) {
  let res = {};
  for (let idx of nums) {
    res[idx] = res[idx] == undefined ? 1 : res[idx] += 1;
  }

  for (let val in res) {
    if (res[val] === 1) {
      return Number(val);
    }
  }
};

```

위 코드처럼 풀었는데, 훨씬 간단하게 문제를 푼 사람들이 많았다.

```js
var singleNumber = function(nums) {
    return nums.reduce((a,b)=>a^b);
};

```