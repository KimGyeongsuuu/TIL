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