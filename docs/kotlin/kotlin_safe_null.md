# Null 안전성

Null: 객체가 선언되었지만 초기화되지 않은 상태로 객체가 주소를 가지지 못한 상태를 나타냅니다.

Null 상태의 객체를 이용하면 `NullPointException`이 발생합니다.

이때 Null 안전성이란 NullPointException이 발생하지 않도록 코드를 작성하는 것을 말합니다.



## ?연산자, Null 허용

`?`연산자를 쓰면 변수에 null의 값을 넣어줄 수 있습니다.



## ?.연산자, Null 안전성 호출

null허용으로 선언한 변수의 멤버에 접근할 때는 반드시 `?.`연산자를 이용해야 합니다.



## ?:연산자, 엘비스

엘비스 연산자란 변수가 null이면 설정한 다른 값을 반환해줍니다.

```kotlin
fun main() {
    var data: String? = null
    println("Length: ${data?.length ?: 0}")
}
```



## !!연산자, 예외 발생

객체가 null일 때 예외(exception)를 일으키는 연산자입니다.

어떠한 경우에는 NullPointException을 발생시켜야할 때도 있습니다.

이러할 때 `!!`연산자를 사용합니다.

```kotlin
fun geeting(name: String?): String {
    return "${name!!} 입니다. 안녕하세요."
}

fun main() {
    println(geeting("홍길동")) // 홍길동 입니다. 안녕하세요.
    println(geeting(null)) // Exception in thread "main" java.lang.NullPointerException
}
```

