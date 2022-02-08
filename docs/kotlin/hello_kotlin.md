# Kotlin이란

[JetBrains](https://www.jetbrains.com/ko-kr/)에서 개발한 오픈소스 언어입니다.

2011년 처음 공개되었으며 2017년에 구글에서 안드로이드 공식 언어로 지정하였습니다.

Java가 인도네시아 섬 이름을 따와서 사용했듯, Kotlin은 러시아 섬 이름에서 유래되었습니다.



![Kotlin_JVM기반](../_asset/hello_kotlin_jvm.png)

확장자는 `.kt`며 코틀린 컴파일러가 해당 확장자를 컴파일하면 자바 바이트 코드가 만들어집니다.



구글이 Kotlin을 공식적 언어로 지정한 이유는 Oracle사와 법적 소송이 생긴 이후부터 준비했던 부분입니다.

Kotlin을 사용함에도 결국은 Java로 코드가 변경된 후에 JVM에서 돌아가는 체제인데 그렇다면 이점이 무엇일까요?



- **Expressive and Concise (표현력과 간결함)**

> 자바로 작성한 것보다 코틀린 코드가 훨씬 간결하게 나올 수 있습니다.



- **Safer code (안전한 코드)**

> Null safety를 지원하는 언어
>
> 객체지향 프로그래밍에서 객체는 Null 상태일 수 있으며 이 때 NullPointException이 발생할 수 있습니다.
>
> Kotlin에서는 변수를 nullable과 not null로 구분해서 선언합니다.
>
> 개발자가 작성하는 코드가 Null 안정성을 확보할 수 있습니다.



- **Interoperable (상호 운용성)**

> Java 클래스나 라이브러리들을 활용할 수 있습니다.
>
> 반대로, Java에서도 Kotlin 클래스를 이용할 수 있습니다.



- **Structured concurrency (구조화 동시성)**

> Kotlin 언어가 제공하는 Coroutines(코루틴) 기법을 이용하면 비동기 프로그래밍을 간소화할 수 있습니다.
>
> 네트워크 연동이나 데이터베이스 갱신과 같은 작업을 할 때 이용하면 프로그램을 조금 더 간단하게 효율적으로 작성할 수 있습니다.



코틀린은 파일명과 클래스명을 다르게 선언해도 됩니다.

코틀린은 객체 지향만을 목적으로 한 언어가 아니라서 그렇습니다.

> :question:Java와 Kotlin이 연동된다고 하였을 때 Java는 모든 것을 클래스로 묶어야 하기에 문제가 생기지 않는가?
>
> :man:Kotlin 컴파일러가 가능하게 해줍니다.
>
> Kotlin 파일을 컴파일하면 클래스는 각각의 클래스 파일로 만들어 집니다.