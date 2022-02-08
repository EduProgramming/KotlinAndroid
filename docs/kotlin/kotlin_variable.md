# Variable

Kotlin에서 변수는 `val`, `var` 키워드로 선언합니다.

- `var`: variable, 값 변경 가능
- `val`: value, 값 변경 불가능

```kotlin
val IMMUTABLE_VALUE: Int = 5
var mutableVariable: Int = 3
```



**타입 지정과 타입 추론**

```kotlin
var num1: Int = 5 // 타입 지정
var num2 = 3 // 타입 추론: Compiler가 알아서 해줌
```



## 초기화 미루기

### lateinit

이후에 초깃값을 할당할 것임을 명시적으로 선언

- var 키워드로 선언한 변수에만 사용할 수 있습니다.
- Byte, Short, Int, Long, Float, Double, Boolean 타입에는 사용할 수 없습니다.



### lazy

변수 선언문 뒤에 `by lazy{ }`형식으로 선언

소스에서 변수가 최초로 이용되는 순간 중괄호로 묶은 부분이 자동으로 실행

```kotlin
val data: Int by lazy {
    5 // 5의 값으로 할당
}
```



## 데이터 타입

**Kotlin의 모든 변수는 객체**

Int는 Primitive type이 아니라 클래스 -> 객체

```kotlin
var data: Int = 5

data = data + 3
data = data.plus(2) // 객체의 method 이용
```



다른 언어에서 사용하는 Primitive Type(기초 데이터 타입)을 가지고 있다.

- Byte
- Short
- Int
- Long
- Float
- Double
- Boolean

- Char
- String

> 정확히는 String은 primitive type이라기 보다는 reference type

문자열 String은 double quote(")로 감싸거나 double quote를 3번 써서 삼중 따옴표를 만들어 사용할 수 있습니다.

삼중 따옴표의 경우에는 문장 자체적으로 띄어쓰기 개행 요소들을 처리해서 나타낼 수 있습니다.

```kotlin
val strData = """
	Hello,
	Kotlin!
"""

println("Check: ${strData.trimIndent()}")
// .trimIndent() 문자열 앞에 공백을 없애줌 
```

위와 같이 문자열 도중에 변수값을 넣어서 처리하고자 `$`를 써서 처리하였는데, 이러한 방식을 **문자열 템플릿** 이라고 합니다.

문자열 템플릿은 단일 변수만 사용할 때는 `$변수명`, 위와 같이 함수를 쓴다거나 다른게 붙는다면 `${변수명}`방식으로 처리합니다.



### Any - 모든 타입 가능

**Kotlin에서 최상위 클래스**

즉, 모든 Kotlin 클래스는 Any의 하위 클래스입니다.

Any타입으로 선언한 변수는 모든 타입의 데이터를 할당할 수 있습니다.



### Unit - 반환문이 없는 함수

데이터 형식이 아닌 특수한 상황을 표현하는 목적으로 사용

Unit 타입으로 선언한 변수에는 Unit 객체만 대입할 수 있습니다.

함수에서 반환문이 없음을 명시적으로 나타낼 때 Unit 타입을 사용합니다.

<u>함수를 선언할 때 반환 타입을 생략하면 자동으로 Unit이 적용</u>됩니다.



### Nothing - null이나 예외를 반환하는 함수

Nothing으로 선언한 변수에는 <u>null만 대입</u>할 수 있습니다.

Nothing으로 선언한 변수는 데이터로서는 의미가 없습니다.

Nothing은 주로 함수의 반환 타입에 사용합니다.



### nullable과 not null

변수를 선언할 때 타입 뒤에 `?`표시를 한다면 null 허용이지만,

추가하지 않았다면 null 불허용입니다.