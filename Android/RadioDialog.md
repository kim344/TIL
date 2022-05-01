```
var selectIndex = 0
val itemList = arrayOf(
    "월요일",
    "화요일",
    "수요일",
    "목요일",
    "금요일",
    "토요일",
    "일요일"
)

AlertDialog.Builder(this@MainActivity).apply {
    setTitle("타이틀 영역")
    setMessage("메세지 영역")
    setSingleChoiceItems(itemList, 0) { _, index ->
        selectIndex = index
    }
    setPositiveButton("선텍") { _, _ ->
        Toast.makeText(this@MainActivity, itemList[selectIndex], Toast.LENGTH_SHORT).show()
    }
}
```
