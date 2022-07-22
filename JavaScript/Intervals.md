# Clock
### interval이란
+ '매번' 일어나야 하는 무언가
+ 어떤 API로 부터 변경된 데이터를 주기적으로 받아와야 하는 경우에 `setInterval()`함수를 사용합니다.

1000ms(1초)마다 getClock이라는 함수를 주기적으로 실행시킨다.
```js
setInterval(getClock,1000);
```
### padStart이란
+ prototype의 문자열의 크기가 maxLength보다 작을 경우 문장 제일 앞에 fillstring으로 채웁니다.
```js
String.prototype.padStart(maxLength, ?fillString);
```
##### 숫자 앞에 0 붙이기
+ 시간이 출력될때 두 자릿수가 아닌 1, 4, 9 같은 한 자릿수 일때는 01, 04, 09로 표현이 이루어지게 숫자앞에 0을 붙입니다.
```js
const clock = document.querySelector("h2#clock");
function getClock(){
    const date = new Date();
    const hours = String(date.getHours()).padStart(2,"0");
    const minutes = String(date.getMinutes()).padStart(2,"0");
    const seconds = String(date.getSeconds()).padStart(2,"0");
    clock.innerText = `${hours}:${minutes}:${seconds}`;
}
getClock();
setInterval(getClock,1000);
```
### padEnd이란
+ prototype의 문자열의 크기가 maxLength보다 작을 경우 문장 제일 뒤에 fillstring으로 채웁니다.
```js
String.prototype.padStart(maxLength, ?fillString);
```
### Math
+ round(x)
    + 입력받은 수 x가 소수점 이하의 값이 0.5보다 크면 입력받은 숫자보다 다음으로 높은 수를 반환합니다.
+ ceil(x)
    + 입력받은 수 x를 올림한 수를 반환합니다.
+ floor(x)
    + 입력받은 수 x를 내림한 수를 반환합니다.
### JS에서이미지 출력
+ `appendChild`는 문서에 있는 바디 끝에 붙입니다.
```js
const bgImage = document.createElement("img");
bgImage.src = `img/${random}`;
document.body.appendChild(bgImage);
```
