# map
"사람"을 예로 들면 누구든지 "이름" = "홍길동", "생일" = "몇 월 며칠" 등으로 구분할 수 있다. 자바의 맵(Map)은 이러한 대응관계를 쉽게 표현할 수 있게 해 주는 자료형이다. 이것은 요즘 나오는 대부분의 언어들도 갖고 있는 자료형으로 Associative array, Hash라고도 불린다.

맵(Map)은 사전(dictionary)과 비슷하다. 즉, people 이란 단어에 "사람", baseball 이라는 단어에 "야구"라는 뜻이 부합되듯이 Map은 Key와 Value를 한 쌍으로 갖는 자료형이다.

|key|value|
|----|---|
|people|사람|
|baseball|야구|

### HashMap
자바의 맵(Map)중 가장 간단한 HashMap에 대해서 알아보자.

#### put
key와 value가 String 형태인 HashMap을 만들고 위에서 보았던 예제의 항목값들을 입력해 보자.
```java
import java.util.HashMap;

public class Sample {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("people", "사람");
        map.put("baseball", "야구");
    }
}
```
key와 value는 위 예제에서 보듯이 put메소드를 이용하여 입력했다.

#### get
key에 해당되는 value값을 얻기 위해서는 다음과 같이 한다.

```java
System.out.println(map.get("people"));  // "사람" 출력
```
위와같이 get 메소드를 이용하면 value값을 얻을 수 있다. 위 예제는 "people" Key에 대응되는 Value 값으로 "사람"이라는 문자열을 출력할 것이다.

#### getOrDefault

맵의 key에 해당하는 value가 없다면 일반적으로 `null`을 리턴한다.
```java
System.out.println(map.get("java"));  // null 출력
```
이때 **null**값 대신 다른 값을 리턴받고 싶다면 `getOrDefault` 메소드를 사용한다.
```java
System.out.println(map.getOrDefault("java", "자바"));  // "자바" 출력
```

#### containsKey
containsKey 메소드는 맵(Map)에 해당 키(key)가 있는지를 조사하여 그 결과값을 리턴한다.

```java
System.out.println(map.containsKey("people"));  // true 출력
```
"people"이라는 값이 존재하면 `true`를 출력한다.
존재하지 않으면 `false`를 출력할 것이다.

#### remove
remove는 맵의 항목을 삭제하는 메소드로 `key`값에 해당하는 `value`값을 삭제하고 삭제한 `value`값을 출력한다.
```java
System.out.println(map.remove("people"));  // "사람" 출력
```
"people"에 해당되는 아이템(people:사람)이 삭제된 후 "사람"이 출력될 것이다.

#### size
size 메소드는 Map의 갯수를 리턴한다.
```java
System.out.println(map.size());  // 1 출력
```
"people", "baseball" 두 값을 가지고 있다가 "people"항목이 삭제되었으므로 1이 출력될 것이다.

