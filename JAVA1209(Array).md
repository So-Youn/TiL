## 1. 배열의 복사

```java
int [] arr = new int[5];
int[] tmp = new int[arr.length*2];		//기존 배열보다 길이가 2배인 배열 생성.
for(int i = 0; i<arr.length;i++){
    tmp[i] = arr[i];	
}
arr = tmp;		//참조변수 arr에 참조변수 tmp값 저장한다.
```

* System.arraycopy()를 이용한 배열의 복사

  * for문 대신 System 클래스의 arraycopy()를 사용하면 보다 간단하고 빠르게 배열 복사할 수 있다.

  * for문은 배열의 요소 하나하나에 접근해서 복사하지만, arraycopy()는 지정된 범위의 값들을 한번에 통째로 복사한다.

  * 어느 배열의 몇 번째 요소에서 어느 배열로 몇 번째 요소로 몇개의 값을 복사할 것인지 지정.

    ```java
    system.arraycopy(num, 0, newNum, 0, num.length);
    		//num[0]에서 newNum[0]으로 num.length개의 데이터 복사.
    ```

```java
public static void main(String[] args) {
		char[] abc = { 'A', 'B', 'C', 'D'};
		char[] num = {'0', '1', '2', '3', '4','5','6','7','8','9'};
		System.out.println(abc);
		System.out.println(num);
		
		//배열 abc와 num을 붙여서 하나의 배열(result)를 만든다.
		char[] result = new char[abc.length+num.length];
		System.arraycopy(abc, 0, result, 0, abc.length);
		System.arraycopy(num, 0, result, abc.length, num.length);
		System.out.println(result);
		//배열 abc을 배열 num의 첫 번째 위치부터 배열 abc 길이만큼 복사.
		System.arraycopy(abc, 0, num, 0, abc.length);
		System.out.println(num);
		//number의 인덱스 6위치에 3개를 복사
		System.arraycopy(abc, 0, num, 6,3);
		System.out.println(num);
		}
```

## 2. String 배열

```java
String[] name = new String[3]; 	//3개의 문자열을 담을 수 있는 배열을 생성한다.

```

* 참조형 변수의 기본 값은 null

* String 배열의 초기화

  ```java
  String[] name = new String[3];
  name [0] = "Kim";
  name [1] = "Park";
  name [2] = "Yi";
  // String[] name = {"Kim", "Park", "Yi"}; 		//new String 생략 가능
  ```

  * String 클래스만 " "만으로 간략히 표현하는게 허용되지만, 원래는 String `클래스`  이므로 new 연산자를 통해 객체를 생성해야한다.

## 3. 커맨드 라인을 통해 입력받기

- 메인 메서드의 매개변수(args)

> 커맨드 라인에서 `java class`명령을 사용해 실행할 때 뒤에 `client1` `client2`와 같은 매개 변수를 주면, 각각 다른 명령을 실행할 수 있게 해주는 역할을 함.

## 3.1. 명령 prompt

![명령 prompt](C:\Users\sec\Desktop\명령 prompt.PNG)		

c:\java>java ArgsTest 100.0 200.0
명령은 매개변수 ->100.0
명령은 매개변수 ->200.0

### 3.2. argument

* Run configurations - program argument - spring prompt 
  * Scanner 클래스 대신 사용하던 방법

```java
	public static void main(String[] args) {
		/*
		 *		args = new String[2];
		 *						명령형 매개변수의 갯수만큼 설정
		 *		args[0] = "100"
		 *		args[1] = "200"
		 */		
		System.out.println("명령은 매개변수 ->"+args[0]);
		System.out.println("명령은 매개변수 ->"+args[1]); 
		
		for (int i=0; i<args.length;i++) {
			System.out.println(args[i]);
		}
		System.out.println("합=>"+(args[0]+args[1]));  		
        //String이기 때문에 계산이 되지 않고, 100, 200으로 출력
		
	//	int num1 = args[0]; 		//int =  String x
		int num1 = Integer.parseInt(args[0]);	//String을 매개변수로 전달
		int num2 = Integer.parseInt(args[1]);
		
		System.out.println("합=>"+ (num1+num2)); 
	}
```

## 3.3 다차원 배열

### 3.3.1 배열을 참조하는 배열.

```java
int[][] score; 				//타입[][] 변수이름;
int[][] score = new int[4][3];	//4행 3열의 2차원 배열 생성

		//2차원 배열의 선언과 생성
		int[][] myarr = new int[2][3]; 
									// int 데이터 3개의 요소를 저장하는 2개짜리 배열
		//2차원배열의 초기화
		myarr[0][0] = 100;
		myarr[1][1] = 200;
```


### 3.3.2 2차원 배열 선언과 생성 초기화하기.

```java
		int[][] myarr2 = {
				{1,2,3},
				{6,7,8,9},
				{11,12,13,14,15},
				};	//int[][] myarr = new int[3][]
		//myarr와 myarr2의 배열의 배열에 저장된 값을 출력하기
		for(int j=0;j<myarr2.length;j++) {
			for(int i=0;i<myarr2[j].length;i++) {
				System.out.print(myarr2[j][i]+"\t");
				}
			System.out.println( );
			}
```

### 3.3.3 가변 배열

* 2차원 이상의 다차원 배열을 생성할 때 전체 배열 차수 중 마지막 차수의 길이를 지정하지 않고, 추후에 각기 다른 길이의 배열 생성함으로써 유동적인 가변 배열 구성.

  ```java
  int[][] score = new int[5][]; //두번째 차원의 길이는 지정하지 않는다.
  ```

  ```java
//2차원 배열부터 배열이 참조하는 배열의 요소를 각각 다르게 정의할 수 있다.
		int[][] myarr = new int[3][];
		myarr[0] = new int[3];
		myarr[1] = new int[2];
		myarr[2] = new int[1];
		
		
		for(int outer=0; outer<myarr.length;outer++) {
			for(int i=0;i<myarr[outer].length;i++)
			{
				System.out.print(myarr[outer][i]+"\t");
			}
			System.out.println( );
		}	
		
	```

