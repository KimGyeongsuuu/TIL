# Kotlin
### 1. 변수
+ var : 변수값 변경 가능
+ val : 선언시에만 초기화 가능(이후에는 값을 변경하지 못한다) -> Java에서 **final**

```kotlin
fun main(){
    var a: Int
    a=123
    println(a)
}
```
```kotlin
fun main(){
    val a:Int
    a=1234  // 중간에 값을 바꾸지 못함으로 에러발생
    println(a)
}
```
+ ? : 변수의 값이 `null`일 수 있다는 표시(`?`를 표시하지 않으면 null이 값이 될 수 없다)
```kotlin
fun main(){
    var a:Int? = null
    println(a)
}
// 출력 : null
```

<hr>

### 2. 형변환
+ 코틀린에서는 to변수()를 통해서 형변환을 할 수 있다<br>
+ **코틀린은 암시적 형변환을 지원하지 않는다**
```kotlin
fun main(){
    var a:Int = 5
    var b:String = a.toString()
    print(b)
}
```
#### 암시적 형변환
컴파일러에 의해 자동으로 형변환이 이루어지는것을 말한다.<br>
예를 들어 `int`와 `float`을 더할 때는 자동으로 float형변환이 이루어진다

#### 명시적 형변환
사용자가 직접 데이터의 타입을 변경하는 것을 말한다.
```kotlin
fun main(){
    var a:Int = 5
    var b:String = a.toString()
    print(b)
}
```

<hr>

### 3. 배열

```kotlin
fun main(){
    var array = arrayOf(1,2,3,4,5)  // 특정 값을 넣어서 배열을 생성하는 경우
    var array2 = Array(10,{0})  // 크기만 정해서 배열을 생성하는 경우
}
```

#### arrayOf()<br>

arrayOf()함수에는 특정 타입을 정하지 않고 배열을 생성한다. 어떠한 타입이 들어가도 상관없다.
```kotlin
fun main(){
    var array = arrayOf(1,"hello",3.4,100)
}
```
특정 타입을 정하고 배열을 생성하는 경우

+ 제네릭
```kotlin
fun main(){
    var array = arrayOf<Int>(10,20,30)
    var array2 = arrayOf<String>("hello","kotlin")
}
```
+ 제공 함수
```kotlin
fun main(){
    var arrInt = intArrayOf(10,20,30)
    var arrChar = charArrayOf('A','B','C')
    var arrBoolean = booleanArrayOf(true,false)
}
```

#### 배열에 값 넣고 빼기
넣기
```kotlin
fun main(){
    array.set(0,100)  // array.set(인덱스,값)
    array[3] = 30   // array[인덱스] = 값
}
```
빼기
```kotlin
fun main(){
    array.get(0) // array.get(인덱스)
    array[3]  // array[인덱스]
}
```

<hr>