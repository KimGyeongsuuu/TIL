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

### 4. 함수
+ 기본형 함수
```kotlin
fun main(){
    print(add(1,2,3))
}
fun add(a:Int, b:Int, c:Int): Int{
    return a+b+c
}
// 출력 : 6
```

+ 단일 표현식 함수
```kotlin
fun main(){
    print(add(1,2,3))
}
fun add(a:Int,b:Int,c:Int) = a+b+c

// 출력 : 6
```

### 5. 조건문
+ if : 만약 ~~
```kotlin
fun main(){
    var a = 5
    if(a>4){
        println(a)
    }else{
        println("exit")
    }
}
// 출력 : 5
```
+ is : 타입 비교
```kotlin
fun main(){
    var a:Any = 5
    if(a is Int){
        println("int")
    }
    if(a is String){
        println("String")
    }
}
// 출력 : int
```
+ when : switch문이랑 비슷한 기능
```kotlin
fun main(){
    exWhen(2)
}
fun exWhen(a:Any){
    when(a){
        1 -> print(a)
        "awd" -> print("awd")
        else -> print(a)
    }
}
// 출력 : 2
```

### 6. 반복문
+ while 
```kotlin
fun main(){
    var i:Int = 0
    while(i<3){
        println(i)
        i++
    }
}
```
+ for
```kotlin
fun main(){
    for(i in 0..3){
        print(i)
        print(" ")
    }

    println()

    for(i in 3 downTo 0){
        print(i)
        print(" ")
    }

    println()

    for(i in 0..5 step 2){
        print(i)
        print(" ")
    }

    println()

    for(i in 'a'..'e'){
        print(i)
        print(" ")
    }
}

결과
0 1 2 3 
3 2 1 0 
0 2 4 
a b c d e
```

### 7. 흐름제어
+ break, continue
```kotlin
fun main(){
    for(i in 0..5){
        if(i==2){
            break;
        }
        println(i)
    }
    println()
    for(i in 0..5){
        if(i==2){
            continue;
        }
        println(i)
    }
}

출력 
0 
1

0
1
2
3
4
5
```

### 람다표현식
쉽게 말하면 익명함수로 함수의 이름이 없는 함수를 의미한다.<br>
보통 한 번 만들고 재사용하지 않는 함수를 사용할때 사용한다.<br>
람다표현식을 사용하면 코드 가독성이 높아진다. 함수형 프로그래밍에서 사용하는 패턴이다.

### 람다식 생성 : 인자가 없는 람다식
```kotlin
// 익명함수 생성 방법 1
var greeting = fun(){ print("hello") }
// 익명함수 생성 방법2
var greeting : () -> Unit = { print("hello") }

// 익명함수 호출
greeting()
```

### 람다식 생성 : 인자가 있는 람다식
인자를 받으려면 인자값과 인자 타입을 명시해주어야한다.<br>
return 키워드를 사용하지 않고 -> 이후에 값이 리턴값이 된다.
```kotlin
fun main(){
    // 익명함수를 생성하여 greeting에 할당
    val greeting = { name:String, age:Int -> "Hello My name is $name. I'm $age year old"}

    // 익명함수 호출
    val result = greeting("kim",18)
    println(result)
}
```

### 람다식 생성 : 인자가 있는 람다식(인자 타입 생략)
인자를 받으려면 인자값과 인자 타입을 명시해주어야하지만, 익명함수의 값이 할당되는 변수에 리턴타입이 명시되어있다면 인자 타입을 생략해도 된다.
```kotlin
fun main(){
    // 익명함수를 생성하여 greeting에 할당
    val greeting: (String, Int) -> String = { name, age -> "Hello My name is $name. I'm $age years old"}

    val result = greeting("kim",18)
    println(result)
}
// 결과 : Hello. My name is kim. I'm 18 years old
```

### 람다식 생성 : 인자값이 하나이면, 인자를 생략하는 람다식
원래는 인자를 받으려면 인자값과 인자타입을 명시해야하는데, 받는 인자값이 하나라면 인자타입을 생략
```kotlin
fun main(){
    val greeting: (String) -> String = {"Hello. My name is $it"}
    val result = greeting("kim")
    println(result)
}
// 결과 : Hello. My name is kim
```

### 스코프 함수
```kotlin
fun main(){

}
class Book(var name:String, var price:Int){
    fun discount(){
        price-=2000
    }
}
```
### 1. apply
위와 같이 Book이라는 클래스가 있다고 가정하자.<br>
Book클래스에는 name과 price를 프로퍼티로 갖게 된다. 그리고 discount()라는 함수를 가지고 있다
```kotlin
fun main(){
    var a = Book("해로의 모험" , 10000).apply{
        name="초특가"+name
        discount()
    }
    println("상품명 : ${a.name}, 가격 : ${a.price}")

}
class Book(var name:String, var price:Int){
    fun discount(){
        price-=2000
    }
}
// 결과 : [초특가]해로의 모험, 가격 8000
```
다시 말해, `apply`함수는 인스턴스를 새로 생성하고 특정 변수값을 할당시키기 전에 초기화 작업을 해줄 수 있는 스코프 함수를 만들어준다.

apply함수 내의 모든 명령이 수행되고 나면 새로운 명령에 값들이 적용된 인스턴스가 생성된다.

### run
run과 apply는 비슷해 보이지만 차이점이 있다.<br>
apply는 반환하는 값이 인스턴스 이지만, run은 반환하는것이 결과값이다.<br>
이미 만들어진 인스턴스를 계산해서 출력해야하는 상황에는 run 활용할 수 있다.
```kotlin
fun main(){
     var a = Book("해로의 모험" , 10000).apply{
        name="초특가"+name
        discount()
    }
    var bookCast = a.run{
        println("상품명 : ${name}, 가격 : ${price}")
        price+2000
    }
    println("원가는 $bookCast 입니다")
}
class Book(var name:String, var price:Int){
    fun discount(){
        price-=2000
    }
}
// 결과 : 상품명 : 해로의 모험, 가격 : 8000
//        원가 : 10000
```
run의 스코프 마지막 줄에 `price+2000`의 결과값을 반환해주는 것이다.

run은 특정 인스턴스의 프로퍼티를 출력하거나 계산결과를 출력해야하는 상황에 사용된다.


### with
with와 run은 사실 같은 기능이다. 생긴것만 다를 뿐 기능적인 차이점은 없다.
```kotlin
var bookCast = a.run{
    println("상품명 : ${name}, 가격 : ${price}")
    price+2000
}
var bookCast2 = with(a){
    println("상품명 : ${name}, 가격 : ${price}")
    price+2000
}
```

### also / let
also와 let은 위에서 설명한 함수들과 동작이 아래와 일치하다
+ 생성된 인스턴스를 반환 : apply , also
+ 최종 실행 결과를 반환 : run , let

also/let 과 apply/run의 차이점은 조금 다른 특징을 가지고 있다.<br>
바로 `it` 키워드르 사용할 수 있다는 것이다!!

```kotlin
fun main(){
    var price = 99999

    var a = Book("해로의 모험",10000).apply{
        name = "[폭탄세일중]" + name
        discount()
    }
    a.run{
        println("상품명 : ${name}, 가격 : ${price}")
    }
    
}
class Book(var name:String, var price:Int){
    fun discount(){
        price-=2000
    }
}
```
위와 같은 코드를 실행시키면 a인스턴스의 책이름과 가격을 기대했지만, 
```
상품명 : [폭탄세일중]해로의 모험, 가격 : 99999
```
위와 같은 결과가 나오게 된다. 이러한 이유는 main에서 a인스턴스 프로퍼티와 이름이 같은 이름이 있기 때문이다.

이러한 상황에서 also / let은 `it` 키워드를 지원합니다.

```kotlin
fun main(){
    var price = 99999

    var a = Book("해로의 모험",10000).apply{
        name = "[폭탄세일중]" + name
        discount()
    }
    a.let{
        println("상품명 : ${it.name}, 가격 : ${it.price}")
    }
    
}
class Book(var name:String, var price:Int){
    fun discount(){
        price-=2000
    }
}
```
```
상품명 : [폭탄세일중]해로의 모험, 가격 : 8000
```
`it`을 사용하니 main() 스코프의 price값이 출력되지 않고, a인스턴스 스코프의 price값이 출력됬다.