# 클래스 종류



## 데이터 클래스

```kotlin
class NonDataClass(val name: String, val age: Int, val address: String)

data class DataClass(val name: String, val age: Int, val address: String)
```

데이터 클래스는 `data` 키워드로 선언하며 자주 사용하는 데이터를 객체로 묶어 줍니다.

데이터 클래스는 VO(value-object)클래스를 편리하게 이용할 수 있게 해줍니다.

2개의 클래스가 다른 점을 알기 위해서 객체를 각각 만들어보도록 하겠습니다.



```kotlin
fun main() {
    val non1 = NonDataClass("홍길동", 30, "율도국")
    val non2 = NonDataClass("홍길동", 30, "율도국")
    
    val data1 = DataClass("홍길동", 30, "율도국")
    val data2 = DataClass("홍길동", 30, "율도국")
}
```



### equals()

객체의 데이터를 비교하기 위해 `equals()`함수를 사용하도록  하겠습니다.

```kotlin
// 해당 내용은 main 함수 안에 있어야 합니다.
println("Non: ${non1.equals(non2)}") // false
println("Data: ${data1.equals(data2)}") // true
```

`equals()` 함수는 <u>주 생성자에 선언한 멤버 변수의 데이터만 비교 대상</u>으로 삼습니다.

즉, 이말은 보조 생성자를 통한 이후의 데이터들이 있다면 옳바르지 않은 결과를 얻을 수 있습니다.

```kotlin
data class DataClass(val name: String, val age: Int) {
    constructor(name: String, age: Int, address: String): this(name, age) {
    }
}

fun main() {
    
    val data1 = DataClass("홍길동", 30, "율도국")
    val data2 = DataClass("홍길동", 30, "대한민국")

	println("Data: ${data1.equals(data2)}") // true
}
```

address값이 다른데 true의 값이 나온 것을 확인할 수 있습니다.



### toString()

```kotlin
class NonDataClass(val name: String, val age: Int, val address: String)

data class DataClass(val name: String, val age: Int) {
    constructor(name: String, age: Int, address: String): this(name, age) {
    }
}

fun main() {
    
    val non = NonDataClass("홍길동", 30, "율도국")
    
    val data = DataClass("홍길동", 30, "율도국")
    
    println(non.toString()) // NonDataClass@49c2faae
    println(data.toString()) // DataClass(name=홍길동, age=30)
}
```

`toString()` 함수는 <u>객체가 포함하는 멤버 변수의 데이터를 출력</u>합니다.

데이터 클래스의 toString()함수 역시 주생성자의 매개변수에 선언된 데이터만 출력 대상입니다.



## 오브젝트 클래스

오브젝트 클래스는 익명 클래스(Anonymous class)를 목적으로 사용합니다.

클래스의 이름이 없기에 선언과 동시에 객체를 생성해야 합니다.

```kotlin
val obj = object {
    fun greeting() {
        println("Hello, Object Class")
    }
}

fun main() {
    obj.greeting()
}
```

이렇게만 작성하면 오류가 발생하게 됩니다. 그 이유는 클래스의 타입 때문입니다.

object 키워드로 클래스를 선언했지만 타입을 명시하지 않았기에 이 객체는 코틀린의 최상위 타입인 Any로 취급됩니다.

그런데 Any 타입 객체에는 greeting이라는 함수가 없어서 오류가 발생합니다.

```kotlin
open class Person() {
    open fun greeting() {
        println("Person Greeting")
    }
}

val obj = object: Person() {
    override fun greeting() {
        println("Hello, Object Class")
    }
}

fun main() {
    obj.greeting()
}
```

위와 같은 방식을 통해서 해결할 수 있습니다.



## 컴패니언 클래스

멤버 변수나 함수를 클래스 이름으로 접근하고자 할 때 사용합니다.

```kotlin
class Person() {
    var name = "홍길동"
    fun greeting() {
        println("제 이름은 $name입니다.")
    }
}

fun main() {
    val person = Person()
    person.name = "정태준"
    person.greeting()
    Person.name = "테스터" // 오류
    Person.greeting() // 오류
}
```

위와 같은 경우에 오류가 나온 것을 되게 만들고 싶으면 컴패니언 클래스를 사용하면 됩니다.



`companion` 키워드를 사용하면 됩니다.

`companion object { }`형태로 선언하면 이 클래스를 감싸는 클래스 이름으로 멤버를 접근할 수 있습니다.

```kotlin
class Person {
    companion object {
        var name = "홍길동"
        fun greeting() {
            println("제 이름은 ${name}입니다.")
        }
    }
}

fun main() {
    Person.name = "테스터"
    Person.greeting()
}
```


컴패니언 클래스는 결과적으로 Java의 **static**을 대체한다고 할 수 있습니다.

> :question:Kotlin도 static을 두면 더 편할텐데 왜 없나요?
>
> :man:Kotlin은 최상위에 함수나 변수를 선언할 수 있어서 객체로 이용할 필요가 없는 멤버를 굳이 클래스에 선언하지 않아도 되기 때문입니다.