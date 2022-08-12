# 객체(Object)
+ 객체
``` js
const superman = {
    name:'clark',
    age:33,
}
```
+ 접근
```js 
superman.name // 'clark'
superman['age'] // 33 
```
+ 추가
```js
superman.gender='male';
superman['hairColor']='black';
```
+ 삭제
``` js
delete superman.hairColor;
```
+ 존재 여부 확인
    + 함수 안에 존재하면 `true`
    + 함수 안에 존재하지 않으면 `false`
    + 함수에서 찾을 수 없으면 `undefined`
```js
superman.birthDay; // undefined

'birthDay' in superman; // false

'age' in superman; // true
```


