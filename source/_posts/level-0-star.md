---
title: level 0. 별 찍기 연습
categories: Algorithm
date: 2017-12-11 23:05:50
---

# 별찍기 연습

## 문제 1
input: 4
output
```bash
*
**
***
****
```

```javascript
var star = "";
var input = 4;

for (var i = 0; i < input; i++) {
  star += "*"
  console.log(star);
}
```


## 문제 2
input: 4
output
```bash
   *
  ***
 *****
*******
```

```javascript
var star ="*";

for (var i = 0; i < 4; i++) {
  star = "";
  for (var j = 4; j > i; j--) {
    star += " ";
  }
  for (var j = 1; j <= i; j++) {
    star += "**"
  }
console.log(star + "*");
}
```


## 문제 3
input: 4
output
```bash
   *
  ***
 *****
*******
 *****
  ***
   *
```

```javascript
var upStar = "";

for (var i = 0; i < 4; i++) {
  upStar = "";
  for (var j = 4; j > i; j--) {
    upStar += " ";
  }
  for (var j = 1; j <= i; j++) {
    upStar += "**"
  }
  console.log(upStar + "*");
}

var downStar = "";

for (var i = 0; i < 3; i++) {
  downStar = "  ";
  for (var j = 0; j < i; j++) {
    downStar += " ";
  }
  for (var j = 2; j > i; j--) {
    downStar += "**"
  }
  console.log(downStar + "*");
}
```
