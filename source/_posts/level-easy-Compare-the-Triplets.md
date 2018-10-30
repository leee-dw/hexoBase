---
title: level Easy. Compare the Triplets
categories: Algorithm
date: 2017-12-15 09:16:13
---

## 문제

Alice and Bob each created one problem for HackerRank. A reviewer rates the two challenges, awarding points on a scale from to for three categories: problem clarity, originality, and difficulty.

We define the rating for Alice's challenge to be the triplet , and the rating for Bob's challenge to be the triplet .

Your task is to find their comparison points by comparing with , with , and with .
```bash
If , then Alice is awarded point.
If , then Bob is awarded point.
If , then neither person receives a point.
```
Comparison points is the total points a person earned.

Given and , can you compare the two challenges and print their respective comparison points?

Input Format
The first line contains space-separated integers, , , and , describing the respective values in triplet .
The second line contains space-separated integers, , , and , describing the respective values in triplet .


Output Format
Print two space-separated integers denoting the respective comparison points earned by Alice and Bob.

Sample Input
```bash
5 6 7
3 6 10
```

Sample Output
```bash
1 1 
```

Explanation
In this example:
Now, let's compare each individual score:

    , so Alice receives point.
    , so nobody receives a point.
    , so Bob receives point.

Alice's comparison score is , and Bob's comparison score is . Thus, we print 1 1 (Alice's comparison score followed by Bob's comparison score) on a single line. 

출처: https://www.hackerrank.com/challenges/compare-the-triplets/problem

### 나의 풀이

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');


var alice = input[0].split(' ');
var bob = input[1].split(' ');
var aliceAnswer = 0;
var bobAnswer = 0;


for (var i = 0; i < alice.length; i++) {
  if (Number(alice[i]) > Number(bob[i])) {
    aliceAnswer++;
  } else if (Number(alice[i]) < Number(bob[i])) {
    bobAnswer++;
  }
}

console.log(aliceAnswer, bobAnswer);

```
