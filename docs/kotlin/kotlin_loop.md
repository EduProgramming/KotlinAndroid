# 반복문

## for문

```kotlin
for (변수 in 1..10) { // 1~10까지
    println(변수)
}
```

- 1..10 : 1부터 10까지 1씩 증가
- 1 until 10 : 1부터 9까지 1씩 증가 (10 미포함)
- 1..10 step 2 : 1부터 10까지 2씩 증가
- 10 downTo 5 : 10부터 5까지 1씩 감소



```kotlin
val arrayData = intArrayOf(3, 5, 7)
for (idx in 0..arrayData.size-1) {
    println(arrayData[idx])
}
```

이러한 방식으로 iterable객체에 접근하는 방법도 있지만 더 쉽게 collection 타입의 인덱스값을 가져오는 방법이 있습니다.

`indices`를 쓰면 더 쉽게 접근할 수 있습니다.

```kotlin
val arrayData = intArrayOf(3, 5, 7)
for (idx in arrayData.indices) {
    println(arrayData[idx])
}
```



`withIndex()`함수를 이용하면 index와 실제 데이터를 가져올 수 있습니다.

```kotlin
val arrayData = intArrayOf(3, 5, 7)
for ((idx, value) in arrayData.withIndex()) {
    println("Index: $idx, Value: $value")
}
```



**for~each문**

```kotlin
val arrayData = intArrayOf(3, 5, 7)
for (data in arrayData) {
    println(data)
}
```



## while문

```kotlin
while (조건식) {
    수행문장
}
```

조건식이 참일때만 반복을 수행합니다.

:warning:무한 반복이 될 수 있으니 조건식과 수행문장에서 고려를 잘 해야합니다.