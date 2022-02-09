# Lambda

## 람다 함수

익명 함수(Annonymous function) 정의 기법

```kotlin
// 함수 선언 형식
fun 함수명(매개변수) {
    함수 본문
}

//람다 함수 선언 형식
{ 매개변수 -> 함수 본문 }
```

- 람다 함수는 `{}`로 표현합니다.
- {}안에 화살표 (`->`)가 있으며 화살표 왼쪽은 매개변수, 오른쪽은 함수 본문 입니다.
- <u>함수의 반환값은 함수 본문의 마지막 표현식</u>입니다.



**람다 함수 선언과 호출**

람다 함수에서 반환할 때 `return`키워드를 사용하지 않음

```kotlin
{ param1: Int, param2: Int -> param1 + param2 }(3, 5)
```



**매개변수가 없는 람다 함수**

```kotlin
{ -> print("매개변수 없음")}

// 화살표 생략
{ print("화살표도 생략한 매개변수 없음") }
```



**함수 타입 선언**

```kotlin
// 일반 함수 선언
fun add(num1: Int, num2: Int): Int {
    return num1 + num2
}

// 람다식
val result: (Int, Int) -> Int = { num1: Int, num2: Int -> num1 + num2 }
```



**typealias, 타입 별칭**

```kotlin
typealias typeStr = String

fun main() {
    val name: typeStr = "홍길동"
    println(name)
}
```

```kotlin
typealias paramType = (Int, Int) -> Int

fun main() {
    val sum: paramType = {num1, num2 -> num1 + num2}
    print(sum(3, 7))
}
```



**매개변수 타입 생략**

위와 같이 변수 부분에 함수 타입을 정해줄수도 있지만 함수 본문에 정해줘서 생략할 수도 있습니다.

```kotlin
fun main() {
    val sum = {num1: Int, num2: Int -> num1 + num2}
    print(sum(3, 7))
}
```



## 고차함수

함수를 매개변수로 전달받거나 반환하는 함수

