---
title: 'Programmers Hash: 완주하지 못한 선수'
categories: Algorithm
date: 2018-09-13 23:40:02
tag:
---
```js
function solution(participant, completion) {

    completion.forEach((el, idx)=> {
        participant.splice(participant.indexOf(el), 1);
    })
    return participant.join();
}
```

나중에 재도전.