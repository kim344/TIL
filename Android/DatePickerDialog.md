

```
// 현재 날짜
var calendar: Calendar = Calendar.getInstance()
var year = calendar.get(Calendar.YEAR)
var month = calendar.get(Calendar.MONTH)
var day = calendar.get(Calendar.DAY_OF_MONTH)

val dateSetListener = DatePickerDialog.OnDateSetListener { view, year, month, dayOfMonth ->
    // 달력에서 선택한 날짜 토스트 메세지로 보여주기
    Toast.makeText(this, "$year / ${month+1} / $dayOfMonth", Toast.LENGTH_SHORT).show()
}

// year, month, day 달력이 호출될때 처음에 보여지는 날짜
// 현재 예제코드 에서는 현재날짜를 보여주도록 설정
DatePickerDialog(this, dateSetListener, year, month, day).apply {  
    setTitle("타이틀 영역")
    setMessage("메세지 영역")
    show()
}
 ```
