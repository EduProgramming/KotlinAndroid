# Inheritance, 상속

```kotlin
open class Super {
}

class Sub: Super() { // Super 클래스 상속
}
```

다른 클래스에서 상속을 할수 있게 선언하려면 `open`키워드를 사용해합니다.

하위 클래스는 클래스 이름 뒤에 `:`을 입력하고 상속받을 상위 클래스 이름을 입력하면 됩니다.

입력할 때는 생성자를 호출하듯 입력하시면 됩니다. (인스턴스화)



```kotlin
open class Super(name: String) {
}

class Sub(name: String): Super(name) { // Super 클래스 상속
}
```



**하위 클래스에서 보조 생성자만 있는 경우**

```kotlin
open class Super(name: String) {
}

class Sub: Super {
    constructor(name: String): super(name) {
        
    }
}
```

 

## Override

상위 클래스에서 정의된 변수나 함수를 재정의 해서 사용할 수 있습니다.

보편적으로 함수를 재정의하여 많이 사용합니다.

```kotlin
open class Super {
    open fun test() {
        println("Super")
    }
}

class Sub: Super() {
    override fun test() {
        println("Sub")
    }
}
```

오버라이딩을 하기 위해서는 상위 클래스의 함수에서도 `open`키워드가 작성되어 있어야 합니다.

그리고 하위 클래스에서 해당 함수 앞에 `override`라고 작성해주셔야 합니다.



## Visibility modifier, 접근 제한자

클래스의 멤버를 외부의 어느 범위까지 허용하게 할 것인지 결정하는 키워드입니다.

| 접근 제한자 | 최상위에서 이용       | 클래스 멤버에서 이용               |
| ----------- | --------------------- | ---------------------------------- |
| public      | 모든 파일에서 가능    | 모든 클래스에서 가능               |
| internal    | 같은 모듈 내에서 가능 | 같은 모듈 내에서 가능              |
| protected   | 사용 불가             | 상속 관계의 하위 클래스에서만 가능 |
| private     | 파일 내부에서만 이용  | 클래스 내부에서만 이용             |

kotlin에서 접근 제한자를 생략하면 public이 기본입니다.

internal의 모듈이라는 개념은 Gradle이나 Maven같은 빌드 도구에서 프로젝트 단위 또는 같은 세트 단위를 말합니다.

protected는 클래스 멤버에서만 선언할 수 있고 최상위에 선언되는 변수나 함수는 선언할 수 없습니다.