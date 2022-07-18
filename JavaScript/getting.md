# Getting Username
HTML-body
```js
<form id="login-form">
        <input 
            required maxlength="15" 
            type="text" 
            placeholder="What is your name?"
        />
        <input type="submit" value ="Log In">
</form>
<h1 id="greeting" class="hidden"></h1>
```
Java script
``` js
const loginForm = document.querySelector("#login-form");
const loginInput = document.querySelector("#login-form input");
const greeting = document.querySelector("#greeting");

function onLoginSubmit(event){
    event.preventDefault();
    loginForm.classList.add("hidden"); // 아이디가 login-form인 아이디를 hidden으로 바꾼다
    const username = loginInput.value; // 입력한 이름이 username에 저장이 된다.
    greeting.innerText = "Hello " + username; // Hello username(자신이 입력한)으로 출력이 된다.
    greeting.innerText = `Hello ${username}`;
    greeting.classList.remove("hidden");
}

loginForm.addEventListener("submit",onLoginSubmit); 
```
css
```css
body{
    background-color: beige;
}
.hidden{
    display: none; // hidden인 클래스를 숨긴다.
}
```

