> **isEmpty, isNotEmpty, isBlank, isNotBlank, isNullOrBlank, isNullOrEmpty 함수의 차이점 정리**

## isEmpty
**CharSequence가 아무 값도 포함하고 있지 않을 때 true를 반환한다.**

```
"".isEmpty()            // true
" ".isEmpty()           // false
"\n".isEmpty()          // false
" A".isEmpty()          // false
null.isEmpty()      	// null
"NORMAL".isEmpty()      // false
```

## isBlank
**CharSequence가 공백만 가지고 있거나 empty일 경우 true를 반환한다.**
```
"".isBlank()            // true
" ".isBlank()           // true
"\n".isBlank()          // true
" A".isBlank()          // false
null.isBlank()      	// null
"NORMAL".isBlank()      // false
```

## isNotEmpty
**CharSequence가 어떠한 값을 포함하고 있을 때(공백 포함) true를 반환한다.**

```
"".isNotEmpty()         // false
" ".isNotEmpty()        // true
"\n".isNotEmpty()       // true
" A".isNotEmpty()       // true
null.isNotEmpty()		// null
"NORMAL".isNotEmpty()   // true
```

## isNotBlank
**CharSequence가 empty가 아니고, 공백만 있지 않을 때 true를 반환한다.**


```
"".isNotBlank()         // false
" ".isNotBlank()        // false
"\n".isNotBlank()       // false
" A".isNotBlank()       // true
null?.isNotBlank()		// null
"NORMAL".isNotBlank()   // true
```

## isNullOrEmpty
**CharSequence가 아무 값도 포함하고 있지 않고 NULL일 때 true를 반환한다.**

```
"".isNullOrEmpty()          // true
" ".isNullOrEmpty()         // false
"\n".isNullOrEmpty()        // false
" A".isNullOrEmpty()        // false
null.isNullOrEmpty()	    // true
"NORMAL".isNullOrEmpty()    // false
```
## isNullOrBlank
**CharSequence가 Blank상태이거나 NULL일 때 true를 반환한다.**

```
"".isNullOrBlank()          // true
" ".isNullOrBlank()         // true
"\n".isNullOrBlank()        // true
" A".isNullOrBlank()        // false
null.isNullOrBlank()	    // true
"NORMAL".isNullOrBlank()    // false
```

<br>

### 정리

* Empty : 어떠한 값도 없을 때
* Blank : 어떠한 값도 없거나 공백, 개행만 가지고 있을 때
