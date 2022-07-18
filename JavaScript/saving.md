# Saving
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
### 읽는 법
```
const username = localStoreage.setItem('myName'); // 키 이름이 myName인 항목을 읽는다.
```
### 삭제
```
localStoreage.removeItem('myName'); // 키 이름이 myName인 항목을 삭제한다.
```