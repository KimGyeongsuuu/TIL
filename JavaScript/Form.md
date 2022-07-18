# Form
### prevenDefault
+ 어떤 event의 기본 행동이든지 발생되지 않도록 막는것이다.
```js
function onLoginSubmit(event){
    event.prevenDefault(); // preventDefault를 사용하여서 event 발생을 막는다
    console.log(username);
}
```
### addEventListner