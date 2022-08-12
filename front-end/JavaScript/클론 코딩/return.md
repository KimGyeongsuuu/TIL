# return
+ return은 누군가가 function을 실행 할 때, 이것을 대체한다.
+ 함수의 결과를 return하기 위해 function을 사용한다.
+ return은 function에 대한 결과값이다
  ```js
  const age = 96;
  function calculateKrAge(AgeOfForeigner){
    return ageOfForeigner +2;
  }
  const krAge = calculateKrAge(age);
  console.log(kr.Age);
  ```
+ return을 하면 그 함수는 끝난다
  ``` js
  const calculator = {
    plus: function(a,b){
      console.log("hello");
      return a+b;
      console.log("bye bye");
    }
  }
