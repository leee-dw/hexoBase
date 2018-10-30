---
title: 'Google IO 2018: Build the future of the web with modern JavaScript 감상 소감'
categories: Dev
date: 2018-06-24 00:01:40
tag:
---
# Build the future of the web with modern JavaScript 감상 소감

>  [Build the future of the web with modern JavaScript](https://www.youtube.com/watch?v=mIWCLOftfRw) 감상 후 소감

이번에 시청한 컨퍼런스 영상은 Google IO 2018 세션 중 자바스크립트 기술을 이용해 미래 웹을 구축한다는 주제의 영상입니다. 주로 자바스크립트에 추가된 최신 기능들을 소개하는 데 중점을 두고 있습니다.

기술 영상에선, 발표자가 코드를 직접 설명하고, 청중들한테 질문도 합니다. 영상을 보고 있으면 저 또한 세션장에 앉아있는 것 처럼 몰입하게 되고, 화면에 나타난 코드를 받아 적으면서, 뭐가 어떻게 변한건지 일시정지 버튼을 누른 뒤 궁구합니다. 아직 해석하지 못하는 코드들이 나올 때면, 그냥 따라치는 걸로 만족했습니다.

지금은 익숙해진  Arrow function 이나, const, let같은 명령어들도 당시엔 희까닥한 기술들이였겠구나, 하는 생각에 시간의 속도를 짐작했고, 지금 배우는 것도 나중엔 익숙해질 거라고, 그러니 지금부터라도 미리 공부해야 겠다고 생각했습니다. 공부할 게 더 많아진 것 같아 머릿 속이 아득해지기도 합니다.



## Modules
```js
// lib.mjs
export const repeat = (string)=> `${string} ${string}`;
export function shout(string) {
  return `${string.toUpperCase()}!`;
}


// main.mjs
import {repeat, shout} from './lib.mjs';


repeat('#io18');
// '#io18 #io18'


shout ('Modules in action');
// 'MODULES IN ACTION!'
```

```html
<link rel="modulepreload" href="lib.mjs">
<link rel="modulepreload" href="main.mjs">
<script type="module" src="main.mjs"></script>
<script module src="fallback.js"></script>
```



## Improved numeric literals 

```js
1000000000000              => 1_000_000_000_000
1019436871.42              => 1_019_436_871.42
0b010010010010111101001111 => 0b01001001_00101111_01001111
0b0100100101001111         => 0b0100_1001_0100_1111
0x23696F3138               => 0x23_69_6F_31_38
```



## BigInt

```js
const max =Number.MAX_SAFE_INTEGER;
// 9_007_199_254_740_991

max + 1; 
// 9_007_199_254_740_992 (right)

max + 2;
// 9_007_199_254_740_992 (wrong)


BigInt(max) + 2n;
// 9_007_199_254_740_993n (right)
```

```js
 1234567890123456789 * 123;
 // 151851850485185200000 (wrong)

 1234567890123456789n * 123n
 // 151851850485185185047n (right)
```



## Async {it.gen}erators

```js
async function getResponseSize(url) {
  const response = await fetch(url);
  const reader = response.body.getReader();
  let total = 0;
  while(true) {
    const {done, value} = await reader.read();
    if(done) return total;
    total += value.length;
  }
}
```

```js
async function getResponseSize(url) {
  const response = await fetch(url);
  let total = 0;
  for await( const chuck of response.body) {
    total += chunk.length;
  }
  return total;
}
```

```js
function print(readable) {
  readable.setEncoding('utf8');
  let data = '';
  readable.on('data', (chunk)=>{
    data += chunk;
  });
  readable.on('end', ()=>{
    console.log(data);
  });
}

const fs = require('fs');
print(fs.createReadStream('./file.txt'));
```






## RegExp features

1. RegExp dotAll mode
```js
const input = `Lorem ipsum dolor sit amet, consectetur adipisicing hello world elit. Adipisci, assumenda consectetur`;

/hello.world/u.teset(input);
// false
/hello[\s\S]world/u.teset(input);
// true but not recommend
/hello[^]world/u.teset(input);
// true but not recommend
/hello.world/su.teset(input);
// true and recommend
```





2. RegExp capture groups
```js
const pattern = /(\d{4})-(\d{2})-(\d{2})/u;
const result = pattern.exec('2018-05-09');
// result[0]=== '2018-05-09'
// result[1]=== '2018'
// result[2]=== '05'
// result[3]=== '09'

const pattern = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/u;
const result = pattern.exec('2018-05-09');
// result.groups === '2018-05-09'
// result.groups.year === '2018'
// result.groups.month === '05'
// result.groups.day === '09'
```

1. Unicode properties
```js
const regexGreek = /\p{Script_Extensions=Greek}/u;
regexGreek.test('π')
// true

const regexAscii = /\p{ASCII}/u;
regexAscii.test('_');
// true

const regexMath = /\p{Math}/u;
regexMath.test('≠');
// true
```
  ```html
  <style>
    :valid {background: lightgreen;}
    :invalid {background: pink;}
  </style>

  <input pattern ="/\p{Math}/u" value= "≠">
  ```

1. Lookbehind assertions
```js
// Positive lookahead:
const pattern = /\d+(?=dollars)/u;
const result = pattern.exec('42 dollars');
// result[0] === '42'


// Negative lookahead:
const pattern = /\d+(?! dollars)/u;
const result = pattern.exec('42 rupees');
// result[0] === '42'


// Positive lookbehind:
const pattern = /(?<=\$)\d+/u;
const result = pattern.exec('$42');
// result[0] === '42'


// Negative lookbehind:
const pattern = /(?<!\$)\d+/u;
const result = pattern.exec('₩42');
// result[0] === '42'
```

5. String#matchAll
```js
 const string = 'Magic hex numbers: DEADBEFF CAFE 8BADF00D';
 const regex = /\b\p{ASCII_Hex_Digit}+\b/gu;
 let match;
 while (match = regex.exec(string)) {
   console.log(match);
 }
```
  ```js
   const string = 'Magic hex numbers: DEADBEFF CAFE 8BADF00D';
   const regex = /\b\p{ASCII_Hex_Digit}+\b/gu;
   for (const match of string.matchAll(regex)) {
     console.log(match);
   }
  ```





## String#trim{Start, End}

```js
const string = '   hello world   ';
string.trim(); // 'hello world'
string.trimStart(); // 'hello world   '
string.trim(); // '   hello world'
```


## Promise#finally

```js
fetchAndDisplay({
  url: someUrl,
  element: document.querySelector('#output');
});
```

```js
function fetchAndDisplay({url, element}) {
  showLoadingSpinner();
  fetch(url)
    .then(response => response.text())
    .then(text=>{
      element.textContent = text;
      hideLoadingSpinner();
    })
    .catch(error=>{
      element.textContent = error.message;
      hideLoadingSpinner();
    });
};
```

```js
function fetchAndDisplay({url, element}) {
  showLoadingSpinner();
  fetch(url)
    .then(response => response.text())
    .then(text=>{
      element.textContent = text;
      hideLoadingSpinner();
    })
    .catch(error=>{
      element.textContent = error.message;
    })
    .finally((=>{
      hideLoadingSpinner();
    }))
};
```





## Object rest & spread

```js
// Rest elements for array destructuring assignment:
const primes = [2, 3, 5, 7, 11];
const [first, second, ...rest] = primes;
console.log(first); // 2
console.log(second); // 3
console.log(rest); // [5, 7, 11]

// Spread elements for array literals:
const primesCopy = [first, second, ...rest];
console.log(primesCopy); // [2, 3, 5, 7, 11]
```

```js
// Rest properties for ovject destructuring assignment:

const person = {
  firstName: 'Daenerys',
  lastName: 'Targaryen',
  nickname: 'Dany',
  culture: 'Valyrian',
};

const {firstName, lastName, ...rest} = person;
console.log(firstName); // 'Daenerys'
console.log(lastName); // 'Targaryen'
console.log(rest); // {nickname: 'Dany', culture: 'Valyrian' }


// Spread Properties for object literals:
const personCopy = {firstName, lastName, ...rest};

console.log(personCopy);
// { firstName: 'Daenerys',
//   lastName: 'Targaryen',
//   nickname: 'Dany',
//   culture: 'Valyrian'}
```

```js
// Shallow-clone an object:
const data = {x: 42, y: 27, label: 'Treasure'};

// The old way:
const clone1 = Object.assign({}, data);

// The new way:
const  clone2 = {...data};

// Either results in:
// { x: 42, y: 27, label: ;Treasure' }
```

```js
// Merge two objects:
const defaultSettings = { longWarning: false, logErrors: false};
const userSettings = {logErrors: true};

// The old way:
const settings1 = Object.assign({}, defaultSettings, userSetting);

const seggings2 = {...defaultSettings, ...userSetting};

// Either results in: 
// { logWarnings : false, logErrors: true }
```

## Class fields

```js
class IncreasingCounter {
  constructor() {
    this._count = 0;
  }
  get value() {
    return this._count;
  }
  increment() {
    this._count++;
  }
}
```

```js
class IncreasingCounter {
  // Private fields
  #count = 0;
  get value() {
    return this.#count;
  }
  increment() {
    this.#count++;
  }
}
```