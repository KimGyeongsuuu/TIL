# Collections Framework
이전 시간에 배열에 대해서 공부했다. 배열은 연관된 데이터를 관리하기 위한 수단이었다. 그런데 배열에는 몇가지 불편한 점이 있었는데 그 중의 하나가 한번 정해진 배열의 크기를 변경할 수 없다는 점이다. 이러한 불편함을 컬렉션즈 프래임워크를 사용하면 줄어든다.
```java
String[] arrayObj = new String[2];
arrayObj[0] = "one";
arrayObj[1] = "two";
// arrayObj[2] = "three"; 오류가 발생한다.
```
하지만 ArrayList는 크기를 미리 지정하지 않기 때문에 얼마든지 많은 수의 값을 저장할 수 있다.
```java
ArrayList al = new ArrayList();
al.add("one");
al.add("two");
al.add("three");
```
ArrayList는 배열과는 사용방법이 조금 다르다. 배열의 경우 값의 개수를 구할 때 .length를 사용했지만 ArrayList는 메소드 size를 사용한다. 또한, 특정한 값을 가져올 때 배열은 [인덱스 번호]를 사용했지만 컬렉션은 .get(인덱스 번호)를 사용한다.
```java
for(int i=0; i<al.size(); i++){
    System.out.println(al.get(i));
}
```
### 장점
컬렉션 프레임워크는 아래와 같은 이점으로 프로그램의 유지보수를 쉽게 만들어준다.

+ List, Queue, Set, Map 등의 인터페이스를 제공하고, 이를 구현하는 클래스를 제공하여 일관된 API 를 사용할 수 있다.

+ 가변적인 저장 공간을 제공한다. 고정적인 저장 공간을 제공하는 배열에 대비되는 특징이다.

+ 자료구조, 알고리즘을 구현하기 위한 코드를 직접 작성할 필요 없이, 이미 구현된 컬렉션 클래스를 목적에 맞게 선택하여 사용하면 된다.

+ 제공되는 API 의 코드는 검증되었으며, 고도로 최적화 되어있다.

### 구성요소
1. 인터페이스 : 각 컬렉션을 나타내는 추상 데이터에 대한 인터페이스 (List, Set, Map 등). 클래스는 이 인터페이스를 구현하는 방식으로 작성되었기 때문에 상세 동작은 달라도 일관된 조작법으로 사용할 수 있다.

2. 클래스 : 컬렉션 별 인터페이스의 구현 (Implementation). 위에서 언급했듯, 같은 List 컬렉션이더라도 목적에 따라 ArrayList, LinkedList 등으로 상세 구현이 달라질 수 있다.

3. 알고리즘 : 컬렉션이 제공하는 연산, 검색, 정렬, 셔플 (Shuffle) 등에 대한 메소드.

### 종류
렉션 프레임워크는 아래와 같이 크게 4개로 분류할 수 있다.

+ 리스트 (List) : 인덱스 순서로 요소를 저장한다. **중복된 데이터를 저장**할 수 있다.
+ 큐 (Queue) : 데이터가 저장된 순서대로 출력되는 선입선출 (FIFO: First In First Out) 의 구조를 갖는 선형 자료구조이다.
+ 집합 (Set) : 순서가 없으며, **데이터를 중복하여 저장할 수 없다**. 집합 연산 (합집합, 교집합, 차집합 등) 을 지원한다.
+ 맵 (Map) : Key-value 쌍으로 데이터를 저장한다. 순서가 존재하지 않으며, Key 가 중복될 수 없다.

### Collections Framework 계층

![collections](https://hudi.blog/static/1bacac1babc556100455a8c64e7658da/e6c4b/2.png)

검정색은 인터페이스, 파랑색은 클래스, 실선 화살표는 상속, 점선 화살표는 구현을 의미한다.

### set
Set은 한국어로 집합이라는 뜻이다. 여기서의 집합이란 수학의 집합과 같은 의미다. 수학에서의 집합도 순서가 없고 중복되지 않는 특성이 있다는 것이 기억날 것이다. (기억나지 않아도 상관없다) 수학에서 집합은 교집합(intersect), 차집합(difference), 합집합(union)과 같은 연산을 할 수 있었다. Set도 마찬가지다.

### 부분집합 (subset)
```java
System.out.println(A.containsAll(B)); // false
System.out.println(A.containsAll(C)); // true
```
![set](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/516/2155.png)

### 합집합
```java
A.addAll(B);
```
![set](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/516/2156.png)

### 차집합
```java
A.removeAll(B);
```
![set](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/516/2158.png)
