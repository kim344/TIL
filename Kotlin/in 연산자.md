> # in 연산자

어떤 값이 객체에 포함되어 있는지 여부를 조사하는 역할을 한다.
<br/><br/>


## 예시
```
val array = mutableListOf(1,2,3,4)

println('o' in "Kotlin")    // true
println("in" !in "Kotlin")  // false
println(3 in array)         // true

val number9 = 9

when (number9){
    in 0..10 -> {
        println("number9 0이상 10이하 입니다.")
    }
    in 10..20 -> {
        println("number9 10이상 20이하 입니다.")
    }
}

결과 => number9 0이상 10이하 입니다.
```
<br/>


## 정리

