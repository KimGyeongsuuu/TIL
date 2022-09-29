# Stack
자료구조의 정의중 하나인 `Stack`은 사전적 의미 그대로 '쌓다', '더미' 입니다

### 특징
`Stack`구조의 가장 큰 특징 중 하나는 나중에 들어간 것이 나중에 나온다는 점입니다.

![stack](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FYhtxB%2FbtqHsbZTFED%2FDhCPI65pmzfsqETjti138k%2Fimg.jpg)

### 사용법
#### 선언
```java
import java.util.Stack; //import
Stack<Integer> stack = new Stack<>(); //int형 스택 선언
Stack<String> stack = new Stack<>(); //char형 스택 선언
```
자바에서 `Stack`을 선언하려면 <stack> `import java.util.Stack` 을 import 한 뒤 Stack<Element> stack = new Stack<>();과 같은 형식으로 선언하면 됩니다. 

#### 추가
```java
Stack<Integer> stack = new Stack<>(); //int형 스택 선언
stack.push(1);     // stack에 값 1 추가
stack.push(2);     // stack에 값 2 추가
stack.push(3);     // stack에 값 3 추가
```
Stack에 값을 추가하고 싶다면 push(value)라는 메소드를 활용하면 됩니다. Stack에 위의 예제와 같이 값을 계속해서 추가해나간다면 아래 그림처럼 데이터가 쌓이게 됩니다.

#### 삭제
```java
Stack<Integer> stack = new Stack<>(); //int형 스택 선언
stack.push(1);     // stack에 값 1 추가
stack.push(2);     // stack에 값 2 추가
stack.push(3);     // stack에 값 3 추가
stack.pop();       // stack에 값 제거
stack.clear();     // stack의 전체 값 제거 (초기화)
```
`Stack`에서 값을 제거하려면 `pop()`이라는 함수를 사용합니다.
그러면 가장 위쪽에 위치한 값이 삭제됩니다.
`clear`를 사용하면 모든 값이 삭제됩니다.

![stack](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcru4A7%2FbtqHra73O8h%2FQ2fkHsFA9NJFxsD5n1AKN0%2Fimg.png)

