Java와 다르게 Kotlin에서는 다양한 클래스들을 제공합니다. 그중 Data Class라는 클래스는 Java에서 개발자들이 불편했던 점을 완벽하게 개선해 줄 기능을 가지고 있는 클래스입니다.
​
### Data Class
​
보통 데이터 전달을 위한 객체를 DTO(Data Transfer Object)라고 부릅니다. 구현 로직을 가지지 않고 순수 데이터만 가졌기 때문입니다. dto의 역할을 하는 클래스는 getter, setter의 역할이 필요하고, toString, equals와 같이 데이터를 출력하고 비교하는 기능도 필요합니다. Java에서는 이 모든 기능을 구현하려면 직접 구현해야 하지만, Kotlin에서는 직접 구현할 필요가 없습니다.
​
Kotlin에서는 위에서 말한 함수들을 Data Class에 프로퍼티만 지정한다면 자동으로 생성해 줍니다.
​
자동으로 생성되는 메서드들은 아주 유용하게 사용되는 메서드들입니다.
​
Kotlin은 data class와 같이 데이터를 보관하기 위한 목적으로 만들어진 클래스를 만들 때는 boilerplate Code를 컴파일러가 자동으로 작성하도록 설계돼 있습니다.
​
```
// getter 와 setter 를 작성한 Java POJO class 의 형태
​
public class Person {
    private String name;
    private int age;
​
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
​
    public String getName() {
        return name;
    }
​
    public void setName(String name) {
        this.name = name;
    }
​
    public int getAge() {
        return age;
    }
​
    public void setAge(String int) {
        this.age = age;
    }
    
}
```
​
위의 코드는 기존의 Java로 구현한 Person의 데이터를 담고 있는 클래스입니다.
​
```
// 위의 POJO 클래스와 같은 기능을 하지만, boilerplate code 가 사라졌다
data class person(
    val name: String, 
    val age: Int
)
```
​
위에서는 Kotlin의 data class를 사용한 모습입니다. data class는 getter, setter 등 다양한 메서드를 제공합니다.
​
boilerplate code를 개발자가 직접 구현할 필요가 없어졌습니다.
​
이렇게 kotlin에서 data class를 사용했을 때의 큰 장점은 개발자의 번거로움을 줄여준다는 점이라고 생각합니다.
​
### data class에서 제공되는 메서드
​
data class에서는 kotlin이라는 언어 자체에서 제공되는 메서드들이 있습니다.
​
#### copy()
​
copy() 함수는 객체의 복사본을 만들어서 반환합니다. 반환된 복사본 객체는 얕은 복사로 생성됩니다. 
​
copy() 함수의 인자로는 클래스에 정의된 프로퍼티를 넘길 수 있으며, 그 프로퍼티의 값만 변경된 새로운 객체가 반환됩니다.
​
아래의 예시에서는 이름이 "올라프"이고 나이가 24인 Person 객체를 생성하고, olaf라는 객체에 copy() 함수를 사용하여 age를 25로 변경하였습니다. 그럼 olderOlaf객체에는 이름이 "올라프"이고 나이가 25인 객체가 생성되어 저장됩니다.
​
복사된 객체의 프로퍼티 값을 바꾸거나 복사본을 제거해도 원본의 객체에는 아무 영향을 주지 않습니다.
​
```
data class Person(val name: String, val age: Int)
​
fun main(args: Array) { 
    val olaf = Person("올라프", 24)  
    
    // olaf 객체를 복사하여 나이를 업데이트한 olderOlaf 객체를 만들었다
    // 기존의 olaf 객체는 변하지 않는다
    val olderOlaf = olaf.copy(age = 25)
}
```
​
#### toString()
​
toString()은 data class에 포함된 프로퍼티를 반환해 주는 기능을 가지고 있습니다. 
​
위에서 정의한 Person data class를 사용해서 예시를 들면 Person data class를 디컴파일 한다면 아래와 같이 toString() 함수가 생성됩니다.
​
```
@NotNull
public String toString() {
   return "Person(name=" + this.name + ", age=" + this.age + ")";
}
```
​
#### Equals와 hashCode
​
이 둘 함수에 대한 규칙을 정리해 보겠습니다.
​
-   Class에 equals를 정의했다면, 반드시 hashCode도 재정의해야 한다.
-   2개의 객체의 equals가 일치하다면, 반드시 hashCode의 리턴값도 같아야 한다.
-   이런 조건이 충족하지 않는다면 HashMap, HashSet 등의 컬렉션을 사용할 때 문제가 생길 수 있다.
​
#### Equals()
​
이 함수는 객체를 비교하는데 아주 유용하게 사용됩니다.
​
```
class Person (
    val name: String,
    val age: Int
)
​
val person1 = Person("kim", 19)
val person2 = Person("kim", 19)
​
println(person1 == person2) // false
```
​
위의 코드에서는 person1과 person2가 같은 프로퍼티를 가지고 있는 인스턴스임에도 false가 반환됐습니다. 
​
class를 data class로 바꾸면 equals가 컴파일 시 재정의 되기 때문에 해결이 가능합니다.
​
```
data class Person (
    val name: String,
    val age: Int
)
​
val person1 = Person("kim", 19)
val person2 = Person("kim", 19)
​
println(person1 == person2) // true
```
​
#### hashCode()
​
객체를 식별할 수 있는 값을 반환합니다. data class가 아닌 일반 class일 때는 값이 같아도 객체가 다르면 다른 hashCode를 반환했는데 class에서는 값이 같으면 같은 hashCode를 반환하도록 구현돼 있습니다.
​
```
class Person (
    val name: String,
    val age: Int
)
​
// val person1 = Person("kim", 19)
// val person2 = Person("kim", 19)
​
// Person 객채의 hashCode
// person1 hashCode 177246405
// person2 hashCode 151509530
​
// data class Person HashCode
// person1 hashcode 1755737970
// person2 hashcode 1755737970
```
