# Saving
### localStorage란
+ localStorage를 사용하면 key와 value를 브라우저에 저장할 수 있습니다.
```
setItem() - key, value 추가
getItem() - value 읽어 오기
removeItem() - item 삭제
```
#### 사용법
+ localStorage.setItem("저장될 키 이름",저장할 변수);
+ localStorage.setItem에 저장이 된다. 
+ 예) localStoreage.setItem("myName","Kim");
```js
function onLoginSubmit(event){
    event.preventDefault();
    loginForm.classList.add("hidden"); // 아이디가 login-form의 아이디를 hidden으로 바꾼다
    const username = loginInput.value;
    localStorage.setItem("username",username);
    greeting.innerText = "Hello " + username;
    greeting.innerText = `Hello ${username}`;
    greeting.classList.remove("hidden");
}
loginForm.addEventListener("submit",onLoginSubmit); 
```
#### localStorage에 배열 저장하기
+ `JSON.stringify`를 사용하면 배열을 저장할 수 있습니다.
```js
function saveToDos(){
    localStorage.setItem("todos", JSON.stringify(toDos));
}
```