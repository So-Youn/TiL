# firebase

## 데이터 저장 방법

| 메서드      | 비고                                                         |
| ----------- | ------------------------------------------------------------ |
| update      | 정의된 경로에서 모든 데이터를 대체하지 않고 일부 키를 업데이트합니다. |
| push        | 데이터베이스의 **데이터 목록에 추가**합니다. 목록에 새 노드를 푸시할 때마다 데이터베이스에서 고유 키(예: `messages/users//`)를 생성합니다. |
| transaction | 동시 업데이트에 의해 손상될 수 있는 복잡한 데이터를 다루는 경우 트랜잭션을 사용합니다. |
| set         | More Actions**정의된 경로**(예: `messages/users/`)에 데이터를 쓰거나 대체합니다. |

* 기본적인  쓰기 작업은  `setValue()` 코드를 사용하여 지정된 참조에 데이터를 저장하고 해당 경로의 기존 데이터를 모두 바꾸는 방식으로 !

  * ex ) 사용자 추가

  ```java
  private void writeNewUser(String userId, String name, String email) {
      User user = new User(name, email);
   mDatabase.child("users").child(userId).setValue(user);
  }
  ```

  * `setValue()`를 사용하면 지정된 위치에서 하위 노드를 포함하여 모든 데이터를 덮어쓴다. 

    * 전체 객체를 다시 쓰지 않고도 하위 항목을 업데이트하는 방법 

    ```java
    mDatabase.child("users").child(userId).child("username").setValue(name);
    //이렇게 사용자 이름을 업데이트 하면 하위만 update 가능
    ```

### 이벤트 수신 대기

* `ValueEventListener` : 경로의 전체 내용을 읽고 변경사항을 수신 대기
  *   return : `onDataChange()`
    * `onDataChange()` 메서드를 사용하여 **이벤트 발생 시점에 특정 경로에 있던 콘텐츠의 정적 스냅샷을 읽기**
    *  `onDataChange()` 메서드는 하위 항목의 변경사항을 포함하여 지정된 데이터베이스 참조에서 데이터가 변경될 때마다 호출
  * snapshot에 대해 `getValue()`를 호출하면 데이터의 자바 객체 표현이 반환
*  `addListenerForSingleValueEvent()`  : 데이터 한번 읽기
  * 더 이상 변경되지 않는 UI 요소 초기화와 같이 경우에 따라 한 번만 호출되고 즉시 삭제되는 콜백
  *  한 번 로드된 후 자주 변경되지 않거나 능동적으로 수신 대기할 필요가 없는 데이터에 유용

## 데이터 삭제

>  데이터 위치의 참조에 `removeValue()`를 호출

* `removeEventListener()` 메서드를 호출하면 콜백이 삭제

## 트랜잭션 데이터 저장

* 증분 카운터와 같이 **동시 수정으로 인해 손상될 수 있는 복잡한 데이터**를 다루는 경우를 위해 SDK에서 [트랜잭션 작업](https://firebase.google.com/docs/reference/node/firebase.database.Reference?hl=ko#transaction)이 제공

* 여러 번 호출되는 트랜잭션 함수
  * 트랜잭션 핸들러가 수 차례 호출되어 `null` 데이터를 처리할 수 있어야한다.  데이터베이스에 기존 데이터가 있더라도 트랜잭션 함수가 실행될 때 로컬에 캐시된 데이터가 없을 수도 있습니다.

```java
DatabaseReference upvotesRef = ref.child("server/saving-data/fireblog/posts/-JRHTHaIs-jNPLXOQivY/upvotes");
upvotesRef.runTransaction(new Transaction.Handler() {
  @Override
  public Transaction.Result doTransaction(MutableData mutableData) {
    Integer currentValue = mutableData.getValue(Integer.class);
    if (currentValue == null) {
      mutableData.setValue(1);
    } else {
      mutableData.setValue(currentValue + 1);
    }

    return Transaction.success(mutableData);
  }

  @Override
  public void onComplete(
      DatabaseError databaseError, boolean committed, DataSnapshot dataSnapshot) {
    System.out.println("Transaction completed");
  }
});
```



## Iterator

* `Iterator` : 자바의 컬렉션에 저장되어 있는 요소들을 읽어오는 방법을 표준화

  * `boolean hasNext()` : 읽어 올 요소가 있는지 확인
  * `Object next()`
  * `void remove()` : 읽어온 요소를 삭제 
    * next() 를 호출한 다음에 remove() 를 호출해야 한다. 
    * 선택적 기능
  * 사용법
    * Iterator를 사용해서 list의 모든 값을 가져올 수 있다.

  ```java
  ArrayList<Integer> list = new ArrayList<Integer>();
  
  Iterator<Integer> itr = list.iterator();
  
  while( itr.hasNext() {
  	list.get( itr.next() );
   }
  ```

* startActivityForResult : 

  ```java
  public void startActivityForResult(@SuppressLint("UnknownNullness") Intent intent,
          int requestCode) {
      startActivityForResult(intent, requestCode, null);
  }
  ```

  