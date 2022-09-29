# Queue
`Queue`는 자료구조의 한 종류인데, 가장 나중에 입력된 값이 먼저 나가는 구조인 `Stack`과 다르게 먼저 들어온 데이터가 가장 먼저나갑니다.

![queue](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbhvAPe%2FbtqHlVqf0RY%2FY4oCoA4wUkEpvIkU80i43K%2Fimg.png)

+ Enqueue : 큐 맨 뒤에 데이터를 추가
+ Dequeue : 큐 맨 앞에 데이터를 삭제

### 사용법
#### 선언

```java
import java.util.LinkedList; //import
import java.util.Queue; //import
Queue<Integer> queue = new LinkedList<>(); //int형 queue 선언, linkedlist 이용
Queue<String> queue = new LinkedList<>(); //String형 queue 선언, linkedlist 이용
```
자바에서 `Queue`를 사용하려면 LinkedList를 import해주어야 합니다.

#### 추가
```java
Queue<Integer> queue = new LinkedList<>();
queue.add(1);
queue.add(3);
queue.offer(5);
```
`Queue`에서 값을 추가하려면 `add`또는 `offer`를 사용해야 합니다.    
#### 삭제
```java
queue.poll();       // queue에 첫번째 값을 반환하고 제거 비어있다면 null
queue.remove();     // queue에 첫번째 값 제거
queue.clear();      // queue 초기화
```
`Queue`에서 값을 제거하고싶다면 poll()이나 remove라는 메서드를 사용하면 됩니다.