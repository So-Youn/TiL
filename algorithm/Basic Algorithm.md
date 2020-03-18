# 알고리즘

* **자료 구조** : 데이터 단위와 데이터 자체 사이의 물리적 또는 논리적인 관계

## 1. 기본 알고리즘

* `while` 문:  어떤 조건이 성립하는 동안 처리를 반복하여 실행.
* `for`문: 하나의 변수를 사용하는 반복문은 `while`보다 `for`문 사용 
* `doWhile` : 일단 루프 본문을 한번 실행한 다음, 계속 반복할 것 인지를 판단하는 사후 판단 반복문.

* 드모르간

> x&&y 와 !(!x||!y)는 같다.

* 논리 부정 연산자 `!` 를 사용한다.

  ```java
  // 두자리 출력
  do{
      
  }while(no>=10||n<=99);
  
  do{
      
  }while(!(no>=10||n<=99));
  ```

### 배열

* 배열 ?   

  ```java
  a = new int[5];  //구성 요소의 개수가 5인 배열
  ```

  * `int` 형의 배열 본체를 생성하고, 그것을 변수 a가 참조하도록 설정
  * a[0] , a[1], ... 는 `int `형 , a 는 `int[5] `형이다.

* 배열 요소 초기화하며 선언하기

  ```java
  int[] a = {1,2,3,4,5}
  //int[] a = new int[]{1,2,3,4,5};
  for (int i = 0; i < a.length; i++)
  	System.out.println("a[" + i + "] = " + a[i]);
  ```

* 배열의 복제(클론)

  * `배열이름.clone();`

  ```java
  int[] b = a.clone();
  //배열 변수 b는 a가 참조하는 배열 본체의 복제를 참조한다.
  ```

  

  



## java String toCharArray()

* 문자열을 **char형 배열**로 바꾼다.
* 배열을 생성 해야하므로 처리속도가 느릴 수 있다

```java
public class tochararray{
    public static void main(String[] args){
        String str = "helloworld";
        //toCharArray() 메서드를 이용한 문자열 나누기
        char[] arr = str.toCharArray();
        
        System.out.print("toCharArray()로 나누어진 값");
        for(int i=0;i<arr.length;i++){
            System.out.print(arr[i]+" ");
        }
        //new String 으로 배열을 문자열로 만들기
       	String newStr = new String(arr);
        System.out.print("new String으로 만들어진 값 :"+newStr)
    }
}
```

* **charAt()**
  * 인자의 위치에있는 char값를 반환하는 String 클래스의 메소드