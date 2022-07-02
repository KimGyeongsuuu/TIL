# 형변환
+ String 
    
    `String` 전역 객체는 문자열(문자의 나열)의 생성자입니다.
    + 문자형으로 변환
    ``` js
    const mathScore = prompt("수학 몇점?");
    const engSCORE = prompt("영어 몇점?);
    const result = (mathScore + engScore) / 2;

    console.log(result);
    ```
+ Number()

    `Number()`는 다른 타입의 값을 숫자로 바꿀 수 있습니다.
    + 숫자형으로 변환
        + true 
            + 숫자 1
        + false
            + 숫자 0
    ```js
    console.log(
        Number(true),
        Number(False)
    )
    ```

+ Boolean()
    + 불린형으로 변환
        + `O,"",null,undefined,NaN는 false 나머지는 true`
    ``` js
    console.log(
        Boolean(1),
        Boolean(1000),
        Boolean("javascript")
    )
    console.log(
        Boolean(0),
        Boolean(""),
        Boolean(null),
        Boolean(undefined),
        Boolean(NaN)
    )