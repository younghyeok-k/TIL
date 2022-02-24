# Kotlinday2

## 1. 표현식
------------------------------------------------------------------------------
 하나의 값으로 수렴하는 수식 뭉치. 자바에서는 표현식이 단독으로 오는 것을 허용하지 않기 때문에 아래와 같은 코드는 오류를 일으키지만, 코틀린은 그렇지 않다.
```
fun Example() {
    53 + 62 - 126
}
```

 

## 2. 변수
------------------------------------------------------------------------------
var : 일반 변수
val : 불변 변수, 자바의 final
```
// 변수를 선언하고 그와 동시에 초기화

var total: Int = 0
val a: Int = 10 + 53 - 7
val b: Int = 32 + 45 - a

total = a + b
 
```
 

## 3. 리터럴
------------------------------------------------------------------------------
 변수의 값이 변하지 않는 데이터, 리터럴에 타입이 있기 때문에 표현식의 결과 값에도 자연스럽게 타입이 생기게 된다. 뒤의 10 + 12 - 5는 표현식의 결과가 Int 이므로 variable 뒤에 :int가 생략되어 있는걸 알 수 있다.
```
val variable = 10 + 12 - 5
 
```
 

## 4. Unit 타입
------------------------------------------------------------------------------

 반환값을 가지지 않는 함수, Unit 타입을 반환하는 함수는 return을 생략한다고 해도 암묵적으로 Unit 타입의 객체를 return 하도록 되어있다.
```
fun noReturnFunction(a: Int): Unit {
    println("a는 $a")
}
 ```

 

## 5. 디폴트 인수
------------------------------------------------------------------------------
 함수에서 인수를 받을 때 디폴트 값을 지정해줄 수 있다.
```
fun getAverage(a: Int = 0, b: Int = 0, print: Boolean = false): Double {
    val result = (a + b) / 2.0
    if (print) {
        println(result)
    }
    return result
}

getAverage(89, 96)
getAverage(a = 66, print = true)
getAverage(print = true)
getAverage(print = true, a = 10, b = 30)
 

```
 

## 6. 객체
------------------------------------------------------------------------------

 서로 연관있는 변수(속성)들을 묶어 놓은 데이터 덩어리를 뜻한다.
```
fun main(args: Array<String>) {
    val person = object {
        val name: String = "홍길동"
        val age: Int = 36
    }
    
    println(person.name)
    println(person.age)
}
 
```
 

## 7. 클래스
------------------------------------------------------------------------------
```
class Person {
    var name: String = ""
    var age: Int = 0
}

fun main(args: Array<String>) {
    val person: Person
    person = Person()
    person.name = "홍길동"
    person.age = 36
    
    val person2 = Person()
    person2.name = "김미영"
    person2.age = 29
    
    val person3 = Person()
    person3.name = "JOhn"
    person3.age = 52
}
 

``` 

## 8. 멤버 함수
------------------------------------------------------------------------------
 클래스에 내장된 함수
```
class Building {
    var name = ""
    var date = ""
    var area = 0
    
    fun print() {
        println("이름: " + this.name)
        pritnln("건축일자: " + this.date)
        println("면적: ${this.area}m2")
    }
}
 
```
## 9. 생성자와 초기화 블록
------------------------------------------------------------------------------
```
class Person constructor(name: String, age: Int) {
    val name: String
    val age: Int
    
    init {
        this.name = name
        this.age = age
    }
}
 
```
 

## 10. init 블록 나누어 쓰기
------------------------------------------------------------------------------
```
class Size(width: Int, height: Int) {
    val width = widht
    val height: Int
    
    init {
        this.height = height
    }
    
    val area: Int
    
    init {
        area = width * height
    }
}
 
```
 

11. 생성자와 프로퍼티 한번에 쓰기

매개변수 앞에 val, var 키워드를 붙이면 동일한 이름의 프로퍼티가 같이 선언된다.
생성자 매개변수에 들어온 인수가 프로퍼티의 초기값이 된다.
class Car(val name: String, val speed: Int = 0)
 

 

12. 보조 생성자

 클래스 내부에 오는 생성자, 여러 개가 올 수 있다.

class Time(val second: Int) {
    init {
        println("Init 블록 실행중")
    }
    
    constructor(minute: Int, second: Int) : this(minute * 60 + second){
        println("보조 생성자 1 실행중")
    }
    
    constructor(hour: Int, minute: Int, second: Int) : this(hour * 60 + minute, second) {
        println("보조 생성자 2 실행중")
    }
    
    init {
        println("또 다른 init 블록 실행중")
    }
}

fun main(args: Array<String>) {
    println("${Time(15, 6).second}초")
    println("${Time(6, 3, 17).second}초")
}

>>> init 블록 실행중
>>> 또 다른 init 블록 실행중
>>> 보조 생성자 1 실행중
>>> 906초

>>> init 블록 실행중
>>> 또 다른 init 블록 실행중
>>> 보조 생성자 1 실행중
>>> 보조 생성자 2 실행중
>>> 21797초
 

 

13. 프로퍼티와 Getter / Setter

 코틀린에서는 프로퍼티에 디폴트 getter/setter가 포함이 되어있기 때문에 따로 만들 필요가 없다. getter/setter의 동작을 커스터마이징 하고 싶다면 별도로 정의를 해야 한다.

class Person {
    var age: Int = 0
    	get() {
            return field
        }
    	set(value) {
            field = if (value >= 0) value else 0
        }
}



