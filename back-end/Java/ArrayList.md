    # ArrayList
ArrayList는 자바의 List 인터페이스를 상속받은 여러 클래스 중 하나입니다.
일반 배열과 동일하게 연속된 메모리 공간을 사용하며 인덱스는 0부터 시작합니다.
배열과의 차이점은 배열이 크기가 고정인 반면 ArrayList는 크기가 가변적으로 변합니다.

내부적으로 저장이 가능한 메모리 용량(Capacity)이 있으며 현재 사용 중인 공간의 크기(Size)가 있습니다.

만약 현재 가용량(Capacity) 이상을 저장하려고 할 때 더 큰 공간의 메모리를 새롭게 할당합니다.


### 1. ArrayList 생성

자바에서 ArrayList를 사용하려면 아래 구문을 먼저 추가해야 합니다.
```java
import java.util.ArrayList;
```
ArrayList의 생성은 다음과 같은 구문들로 가능합니다.
```java
ArrayList<Integer> integers1 = new ArrayList<Integer>(); // 타입 지정
ArrayList<Integer> integers2 = new ArrayList<>(); // 타입 생략 가능
ArrayList<Integer> integers3 = new ArrayList<>(10); // 초기 용량(Capacity) 설정
ArrayList<Integer> integers4 = new ArrayList<>(integers1); // 다른 Collection값으로 초기화
ArrayList<Integer> integers5 = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5)); // Arrays.asList()
```
### 2. ArrayList 엘레멘트 추가/변경

ArrayList를 생성한 후 `add()` 메소드로 엘레멘트를 추가할 수 있습니다.
또한 `set()` 메소드로 기존에 추가된 값을 변경하는 것도 가능합니다.
```java
import java.util.ArrayList;
```
```java
public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>();
        // add() method
        colors.add("Black");
        colors.add("White");
        colors.add(0, "Green");
        colors.add("Red");

        // set() method
        colors.set(0, "Blue");

        System.out.println(colors);
    }
}
```
add()는 기본적으로 리스트의 가장 끝에 값을 추가합니다.

결과
```
Blue, Black, White, Red
```

### 3. ArrayList 엘레멘트 삭제

추가했던 값을 삭제할 때는 remove() 메소드를 호출합니다.
```java
import java.util.ArrayList;
import java.util.Arrays;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>(Arrays.asList("Black", "White", "Green", "Red"));
        String removedColor = colors.remove(0);
        System.out.println("Removed color is " + removedColor);

        colors.remove("White");
        System.out.println(colors);

        colors.clear();
        System.out.println(colors);
    }
}
```
삭제할 때는 엘레멘트의 인덱스를 입력하거나 엘레멘트를 직접 입력할 수 있습니다.
인덱스를 통해 삭제할 경우 삭제되는 엘레멘트를 리턴받을 수 있습니다.
ArrayList 안의 내용을 전체 삭제할 때는 clear()를 호출하면 됩니다.


### 4. ArrayList 전체 값 확인

ArrayList의 모든 값들을 순회해서 출력하고 싶은 경우 다양한 방법을 사용할 수 있습니다.
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Iterator;
import java.util.ListIterator;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>(Arrays.asList("Black", "White", "Green", "Red"));
        // for-each loop
        for (String color : colors) {
            System.out.print(color + "  ");
        }
        System.out.println();

        // for loop
        for (int i = 0; i < colors.size(); ++i) {
            System.out.print(colors.get(i) + "  ");
        }
        System.out.println();

        // using iterator
        Iterator<String> iterator = colors.iterator();
        while (iterator.hasNext()) {
            System.out.print(iterator.next() + "  ");
        }
        System.out.println();

        // using listIterator
        ListIterator<String> listIterator = colors.listIterator(colors.size());
        while (listIterator.hasPrevious()) {
            System.out.print(listIterator.previous() + "  ");
        }
        System.out.println();
    }
}
```

결과
```
Black White Green Red
Black White Green Red
Black White Green Red
Red Green White Black
```

### 5. 값의 존재 유무

배열안에 값이 존재한다면 어떤 위치에 존재하는지 알고 싶은 경우가 있습니다.
값이 존재하는지 알고 싶다면 `contains`를 사용하고, 값의 위치를 알고 싶다면 `indexOf`를 사용할 수 있습니다.
```java
import java.util.ArrayList;
import java.util.Arrays;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>(Arrays.asList("Black", "White", "Green", "Red"));
        boolean contains = colors.contains("Black");
        System.out.println(contains);

        int index = colors.indexOf("Blue");
        System.out.println(index);

        index = colors.indexOf("Red");
        System.out.println(index);
    }
}
```
`contains`는 값이 존재하면 `true`를 출력합니다.

`indexOf`는 해당 배열의 인덱스를 리턴합니다.