---
title: level Easy. Simple Array Sum
categories: Algorithm
date: 2017-12-15 09:26:11
---

# 문제
Given an array of integers, can you find the sum of its elements?

Input Format
The first line contains an integer, , denoting the size of the array.
The second line contains space-separated integers representing the array's elements.

Output Format
Print the sum of the array's elements as a single integer. 

Sample Input
```bash
6
1 2 3 4 10 11
```

Sample Output
```bash
31
```

## 나의 풀이
```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');

var number = Number(input[0]);
var arr = input[1].split(' ').map(Number);
var sum = 0;

for(var i = 0; i < number; i++) {
    sum += arr[i];
}

console.log(sum);
```