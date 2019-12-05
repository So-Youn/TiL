## 1. 클래스

### 1. 변수

`변수` 란 프로그램 실행 시 발생되는 임의의 값을 저장하는 메모리 장소.

데이터타입(Type) 변수명 = 초기값;

* 기본형 : value 저장
* 참조형 (reference type)

## 2. 연산(Operation)

```java
public static void main(String[] args) {
		System.out.println(6);						 //Number
		System.out.println("six"); 					//String (문자열)
		System.out.println("6"); 	//String 6 - 컴퓨터에서 숫자가 아니라 문자로 인식.
		System.out.println(6+6); 					//12
		System.out.println("6"+"6"); 				//66, +는 결합연산자
		System.out.println(6*6);					//36
						//System.out.println("6"*"6");//문자열은 *연산을 할 수 없다.
		System.out.println("1111".length()); //문자열의 길이 ( 숫자의 길이는 확인x)
	}
```

## 3. String

' '는 Character(문자, 한 글자를 표현하는 datatype)를 나타낸다.

" "는 String (character의 모임)

```java
public static void main(String[] args) {
		System.out.println("Hello World");		    //String(문자열)
		
		System.out.println("Hello"
				+ " World"); 						//Hello World 출력
		//new line (\n)
		System.out.println("Hello \n World");
		//escape
		System.out.println("Hello \"World\"");		// Hello "World"
		
	}
```







### 3. Method()

> mothod();
>
> ()에 정의해야 하는 값이 있는 건 메시지를 입력 받아야하는 메소드.
>
> 메소드 처리 후 만들어지는 오직 한개의 값 = `return`값 
>
> void = return 값이 없다는 뜻!





