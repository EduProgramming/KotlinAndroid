# 가정문

## if문

**if문**

```kotlin
if (조건식) {
    // 조건식 참일때 수행문장
    수행문장
}
```



**if~else문**

```kotlin
if (조건식) {
    수행문장
} else {
    // 조건식 거짓일 때 수행문장
    Else 수행문장
}
```



**if ~ else if ~ else문**

```kotlin
if (조건식A) {
    수행문장A
} else if (조건식B) {
    수행문장B
} else if (조건식C) {
    수행문장C
} else {
    Else 수행문장
}
```



Kotlin도 모든 변수가 객체로 이루어져 있기에 아래와 같이 사용도 가능합니다.

```kotlin
var data = 5
var result = if (data > 5) {
    println("data가 5보다 크다")
    true // 참을 때 리턴값
} else {
    println("data가 5보다 작거나 같다")
    false
}

println(result)
```

Kotlin은 삼항연산자 기능이 없기에 위와 같은 방도로 사용하면 됩니다.



## when문

switch~case문이라고 보시면 됩니다.

```kotlin
when (데이터) {
    경우1 -> {
        수행문장1
    }
    경우2 -> {
        수행문장2
    }
    else -> {
        Else 수행문장
    }
}
```



```kotlin
var data: Any = 3
when (data) {
    is String -> println("Data is String")
    3, 5 -> println("Data is 3 or 5")
    in 1..10 -> println("Data is 1..10")
    else -> println("Data is not valid")
}
```

위의 예시 같은 경우는 '3, 5'의 경우에도 맞고 'in 1..10'의 경우에도 맞지만 가장 먼저 조건이 맞는 부분 내용만 수행합니다.



**when문 표현식사용**

```kotlin
var data: Any = 3
when {
    data is String -> println("Data is String")
    data == 3 || data == 5 -> println("Data is 3 or 5")
    data in 1..10 -> println("Data is 1..10")
    else -> println("Data is not valid")
}
```



```kotlin
var data: Any = 3
val result = when {
    data is String -> "Data is String"
    data == 3 || data == 5 -> "Data is 3 or 5"
    data in 1..10 -> "Data is 1..10"
    else -> "Data is not valid"
}

println(result)
```

