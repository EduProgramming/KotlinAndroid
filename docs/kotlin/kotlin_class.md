# Class

 클래스의 생성자를 본문이 아닌 선언부에 작성할 수 있어서 본문이 없는 클래스도 의미가 있습니다.



클래스의 멤버는 생성자, 변수, 메서드(함수), 클래스로 구성됩니다.

코틀린의 생성자는 `constructor` 키워드를 사용합니다.

클래스 안에 클래스 또한 선언할 수 있습니다.



```kotlin
class Person {
    var name = "taejune"
    constructor(name: String) {
        this.name = name
    }
    fun hello() {
        println("name: $name, 입니다. 안녕하세요.")
    }
    class Action {}
}
```



## constructor, 생성자

Kotlin 클래스 생성자를 `주 생성자`와 `보조 생성자`로 구분합니다.



### 주 생성자

```kotlin
class Person constructor() {
}
```

`constructor`을 생략할 수도 있습니다.

```kotlin
class Person() {   
}
```

`()`조차도 생략해서 나타낼 수 있습니다. 생략을 하면 컴파일러가 자동으루 매개변수가 없는 주 생성자를 추가합니다.

```kotlin
class Person {
}
```

매개변수가 있을 때는 선언을 해줘야 합니다.

```kotlin
class Person(name: String, age: Int) {
}
```



#### init

init 키워드를 농해 주 생성자의 본문을 구현할 수 있습니다.

```kotlin
class Person(name: String, age: Int) {
    init {
        println("Create Person Constructor")
    }
}
```

주 생성자의 파라미터는 지역 변수로 init 내부에서만 활용 가능합니다.

이를 멤버 변수로 사용하는 방법은 아래와 같습니다.



```kotlin
class Person(name: String, age: Int) {
    var name: String
    var age: Int
    init {
        this.name = name
        this.age = age
    }
    
    fun hello() {
        println("저의 이름은 $name이며 나이는 $age살 입니다.")
    }
}
```

위의 방법 말고도 생성자의 매개변수를 클래스의 멤버 변수로 선언하는 방법이 있습니다.

```kotlin
class Person(val name: String, val age: Int) {
    fun hello() {
        println("저의 이름은 $name이며 나이는 $age살 입니다.")
    }
}
```

주 생성자에서만 유일하게 var나 val 키워드로 매개변수를 선언할 수 있으며 이렇게 할 경우 멤버 변수가 됩니다.



### 보조 생성자

`constructor`을 클래스의 선언부에 선언할 경우 -> 주 생성자

클래스의 본문에 선언할 경우 -> 보조 생성자

```kotlin
class Person {
    constructor(name: String) {
        println("Parameter name constructor")
    }
    constructor(name: String, age: Int) {
        println("Parameter name, age constructor")
    }
}
```

이렇게 보조 생성자를 2개를 선언했는데 이러한 것을 `생성자 오버로딩(Overloadding)`이라고 합니다.

> **Overloading이란,**
>
> 같은 함수 이름을 가지고 있으나 매개 변수, 리턴타입 등의 특징을 다른 여러개의 서브프로그램 생성을 가능하게 하는 함수의 특징입니다.



#### 보조 생성자에 주 생성자 연결

만약 주 생성자와 보조 생성자를 모두 선언한다면 <u>반드시 생성자끼리 연결</u>을 해주어야 합니다.

**this() 구문 사용**

```kotlin
class Person(name: String) {
    constructor(name: String, age: Int): this(name) {
        println("Name: $name / Age: $age")
    }
}
```



**보조 생성자가 여럿일 때 생성자 연결**

```kotlin
class Person(name: String) {
    constructor(name: String, age: Int): this(name) {
        println("Name: $name / Age: $age")
    }
    
    constructor(name: String, age: Int, address: String): this(name, age) {
        println("Name: $name / Age: $age / Address: $address")
    }
}

fun main() {
    val person = Person("정태준", 255, "비공개")
    /* 출력결과:
     * Name: 정태준 / Age: 255
	 * Name: 정태준 / Age: 255 / Address: 비공개
     */
}
```

