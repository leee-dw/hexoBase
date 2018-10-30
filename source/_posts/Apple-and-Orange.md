---
title: Apple and Orange
categories: Algorithm
date: 2018-02-27 16:40:24
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');

var distances = input[0].split(' ');
var positions = input[1].split(' ');
var appleScore = input[3].split(' ');
var orangeScore = input[4].split(' ');

var larry = [];
var larryScore = 0
var rob = [];
var robScore = 0


for ( var val of appleScore) {
  larry.push(Number(positions[0]) + Number(val))
}

for ( var val of orangeScore) {
  rob.push(Number(positions[1]) + Number(val))
}


for (var i = 0; i < larry.length; i++) {
  if (Number(distances[0]) <= larry[i] && Number(distances[1]) >= larry[i]) {
    larryScore++;
  }
}

for (var i = 0; i < rob.length; i++) {
  if (Number(distances[0]) <= rob[i] && Number(distances[1]) >= rob[i]) {
    robScore++;
  }
}

console.log(larryScore);
console.log(robScore);
```