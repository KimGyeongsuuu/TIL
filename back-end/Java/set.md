# set
### Hash
Hash는 값을 저장하고 조회하는데 있어 가장 빠른 알고리즘이다.<br>

![hash](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbMXUAM%2FbtqHR7kuE7O%2FjVgSdkU08LGsl5tEtagT41%2Fimg.png)
저장하려는 값을 HashCode로 바꾸면 그 HashCode가 값을 저장하는 주소가 된다.
### HashSet
Set은 비선형 자료구조이기 때문에 저장한 순서대로 값이 저장되지 않고, 따라서 출력 또한 저장된 순서대로 출력되지 않는 특징을 갖고 있습니다.

또한, 값의 중복을 허용하고 있지 않습니다. 해시의 경우 값 자체가 메모리 주소가 되기 때문에, 같은 위치에 두 개의 값을 저장할 수는 없고, 한 번만 저장됩니다.
### lterator
자바의 컬렉션에 존재하는 값들을 읽어오기 위한 방법으로 'iterator'라는 클래스가 존재합니다.

이 iterator는 해당 컬렉션의 주소값을 기반으로 하나씩 값을 조회하는 클래스입니다.
따라서, 대표적으로 다음과 같은 두 개의 함수가 존재합니다.
```
hasNext() : 다음 값을 갖고 있는지 true/false 반환

next() : 다음 값으로 이동 및 반환
```
```java
import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;
public class setExam {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Set<String> set1 = new HashSet<>();
		boolean flag1 = set1.add("kang");
		boolean flag2 = set1.add("kim");
		boolean flag3 = set1.add("kang");
		
		System.out.println(set1.size());
		
		System.out.println(flag1);
		System.out.println(flag2);
		System.out.println(flag3);
		
		Iterator<String> iter = set1.iterator();
		while(iter.hasNext()) {
			String str = iter.next();
			System.out.println(str);
			
		}
	}

}
```
<hr>

다음 코드는 set에 a를 두 번 더하고, b를 한 번 더합니다. 출력해 보면 a와 b가 각각 한 번씩만 출력되는데요. set은 이미 있는 값이면 값을 더해도 2개가 아니라 하나의 값만 유지하기 때문입니다.
```java
import java.util.*;

public class SetExam{
    public static void main(String[] args){
        Set<String> set = new HashSet<String>();
        set.add("a");
        set.add("a");
        set.add("b");
        
        System.out.println("set의 내용을 출력합니다.");
        for(String str : set){
            System.out.println(str);
        }
    }
}
```
```java
boolean flag1 = set1.add("kim");
boolean flag2 = set1.add("lee");
boolean flag3 = set1.add("kim");   // 같은 값 입력
// 저장된 크기를 출력합니다. 3개를 저장하였지만, 이미 같은 값이 있었기 때문에 2개가 출력
System.out.println(set1.size());
System.out.println(flag1);         // true
System.out.println(flag2);         // true
System.out.println(flag3);         // false  : 같은 값을 add하였기 때문에 false
```