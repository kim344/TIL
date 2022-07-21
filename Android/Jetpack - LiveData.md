## LiveData는 관찰 가능한(Observable) 데이터 클래스다.
<br>
DataBinding, RxJava의 Observable 다르게 LiveData는 Lifecycle을 통해 생명주기를 인식한다. 즉 액티비티, 프래그먼트, 서비스와 컴포넌트들의 생명주기를 따른다.
<br><br>
LiveData는 데이터의 변경을 활성화된 관찰자(Observable)를 통해 알린다. 
**LifecycleOwner**의 생명주기가 **STARTED, RESUME** 상태인 경우만 활성 상태로 간주한다. **DESTROYED** 상태가 되면 자동으로 옵서버는 내부에서 제거된다.
그러므로 액티비티 또는 프래그먼트의 생명 주기에 따른 메모리 누수 등을 걱정할 필요가 없어진다.
<br><br>
## LiveData 장점
  * UI와 데이터상태의 동기화 
  * 메모리 누수를 방지한다
  * 액티비티가 갑작스럽게 종료될 때도 안전하다
  * 생명주기에 대한 고민은 이제 그만한다
  * 최신의 데이터를 유지한다
  * 구성 변경에 대응한다
  * 자원 공유하기
