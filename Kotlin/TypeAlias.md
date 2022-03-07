> # TypeAlias

**typealis** 라는 키워드를 사용하면 **이미 존재하는 타입(Int, Long, String 등)에** 별명을 붙일 수 있다.
<br/><br/>

## 사용법
**typealias 별명 = 타입**
<br/><br/>


## 예시
서울시 강남구 서초동의 미세먼지 데이터를 가지고 있는 클래스를(SeoulCityGangNamGuSeoChoDongFineDustData) 사용하기에는 타입의 이름이 너무 길어
간편하게 AirkCondition 이라는 별명으로 바꿔서 사용할 수 있다.
```
typealias AirCondition = SeoulCityGangNamGuSeoChoDongFineDustData

data class SeoulCityGangNamGuSeoChoDongFineDustData(
    val pm10: Int,
    val pm25: Int
)

val airCondition = AirCondition(pm10 = 10, pm25 = 25)
```
<br/>


## 정리
**typealias는 타입의 이름이 너무 길 때, 타입 이름을 줄이는 용도로 사용하면 좋다.**
