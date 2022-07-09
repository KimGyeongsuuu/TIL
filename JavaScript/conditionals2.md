# NaN
+ isNaN(is Not a Number)
    + 하나의 인자를 주면 그 인자가 숫자인지 아닌지 Boolean으로 구별해준다.
    + true이면 숫자가 아닌것이 맞기이기 때문에 숫자가 아니다
    + flase면 숫자가 아닌것이 아니기 때문에 숫자가 맞다.
    ``` js
    const age = parseInt(prompt("How old are you?"));
    console.log(isNaN(age));
    ```