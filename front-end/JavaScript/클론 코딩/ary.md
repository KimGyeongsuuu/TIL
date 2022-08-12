# 배열
Array
+ 1번에 철수
+ 2번에 영희
+ 30번에 영수
```js
let students['철수','영희',...'영수']

console.log(students[0]); // 철수
console.log(students[1]); // 영희
console.log(students[29]); // 영수
```
+ 대입
``` js
students[0] = '민정';
console.log(students) // ['민정','영희',...]
```
+ 특징
    + 배열은 문자 뿐만 아니라,숫자,객체,함수 등도 포함할 수 있음
+ length : 배열의 길이
``` js
students.length // 30
```
+ push() : 배열 끝에 추가
```js
let days = ['월','화','수'];
days.push('목')
console.log(days) // ['월','화','수','목']
```
+ pop() : 배열 끝 요소 제거
``` js
let days = ['월','화','수'];
days.pop()
console.log(days) //['월','화'] 
```
+ shift,unshift : 배열 앞에 제거/추가
    + 추가 : 배열 앞에 추가
    ``` js
    days.unshift('일');
    console.log(days)// ['일','월','화','수']
    ```
    + 제거 : 배열 앞에 제거
    ```js
    days.shift();
    console.log(days) // ['월','화','수'];