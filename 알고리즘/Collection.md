#  Collection

## 1. List

> 중복을 허용하면서 저장순서가 유지되는 컬렉션

* `get(index)` : 저장된 위치에 있는 객체 반환
* `set(index, element)` : 지정된 **위치(index)**에 **객체(element)**를 저장

## 2. Set

> 중복을 허용하지 않고 저장순서가 유지되지 않는 컬렉션 클래스 구현
>
> ex ) HashSet, TreeSet

## 3. Map

> 키(key)와 값(value)을 하나의 쌍으로 묶어서 저장하는 컬렉션 클래스
>
> * 키는 중복될 수 없지만 값은 중복이 가능

* `get(key) `: 지정한 key객체에 대응하는 value객체 찾아 반환
* `isEmpty()` : Map이 비어있는지 확인
* `put(key, value)` : value를 key객체에 연결(mapping)하여 저장 

## 4. ArrayList

> List 인터페이스를 구현하기 때문에 데이터의 저장순서가 유지되고 중복을 허용한다.
>
> *가장 많이 사용되는 컬렉션 클래스*



