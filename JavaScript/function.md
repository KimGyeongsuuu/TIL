# 함수
+ 함수 선언문 : 어디서든 호출 가능
+ ` JavaScript`에서는 `실행 전` 초기화 단계에서 코드의 모든 함수 선언문을 찾아서 생성해줍니다.

``` js
sayHello();
function sayHello(){
    console.log('Hello');
}
```
+ 함수 표현식 : 코드에 도달하면 생성
``` js
let sayHello = function(){
    console.log('Hello');
}
sayHello();
```
+ 화살표 함수(arrow function)
```js
let add = (num1,num2)=> num1 + num2
```