##  #1.  Throws

#### Class FileInputStream 

- [java.lang.Object](../../java/lang/Object.html)
   - [java.io.InputStream](../../java/io/InputStream.html)
     - java.io.FileInputStream

*메소드를 찾을 때는 상위 것도 다 찾아봐야 한다. (상속관계 파악 필수)*![캡처](C:\Users\sec\Desktop\캡처.PNG)

```java
public class ExceptionTest05 {
	public static void main(String[] args) {
		try {
			FileInputStream fs = new FileInputStream("test.txt");
			System.out.println(fs.read());
			// Unhandled exception type FileNotFoundException
			//이 생성자는 예외 발생가능성이 있으니, 꼭 exception을 처리할 것을 경고해주는 것.
			System.out.println(Integer.parseInt("1234"));
			//System.out.println(Integer.parseInt("문자열"));
			//NumberFormatException : 문자열이지만, 숫자로 인식되어야 한다.
		}catch (FileNotFoundException e) {
			System.out.println("파일을 읽을 때 오류가 발생했습니다.");
		}catch (IOException e) {
			System.out.println("파일을 찾을 수 없습니다.");
			// 파일을 다시 선택할 수 있도록 처리
		}
	}
}
```

####  Class FileNotFoundException

- [java.lang.Object](../../java/lang/Object.html)
   - [java.lang.Throwable](../../java/lang/Throwable.html)
     - [java.lang.Exception](../../java/lang/Exception.html)
        - [java.io.IOException](../../java/io/IOException.html)
           - java.io.FileNotFoundException	

![read](images/read.PNG)



### [Throws 처리 방법]

 1. 예외가 발생된 곳에서 예외를 처리하도록 정의

     예외가 발생한 곳에서 예외를 처리하면 호출하는 곳에서는 어떤 예외가 발생했는지 알 수 없고
     예외가 발생할 때 경우에 따라서 다르게 처리하고 싶어도 할 수 없다.
     
 2. 메소드를 호출하는 곳에서 예외를 처리하도록 설정.

     ```java
     public int test(int num1, int num2) throws ArithmeticException {
         return ~;
     }
     ```



내가 만든 클래스가 exception 클래스가 되게 하려면? exception  클래스 중 아무거나 상속을 받는다.

>`Exception(String message)`        				-사용자 정의 Exception
>
>  Constructs a new exception with the specified detail message.
>
>일반적으로 Exception클래스들의 상위가 Exception

```java
public class MyException extends Exception{
	public MyException(String msg) {
		super(msg);
	}
	//MyException이 발생햇을 때 저장하고 싶은 정보가 있거나 처리해야 할 내용이 있는 경우 구현
}
```

---

```java
//생략
		try { // 더 좋은 방법
			s1.deposit(-10);
		} catch (Exception e) {
			System.out.println(e.getMessage());
		}
		try {
			s1.withdraw(6000000);
		} catch (Exception e) {
			System.out.println("금액이 0보다 적거나 현재 잔액보다 많습니다.");
		}

```



```java
public void deposit(double money) throws Exception {//호출할 수 있게 처리하도록 예외를 던져버림

		if (money < 0) {
			throw new Exception("입금 금액이 0보다 적습니다.");
		}
		this.balance = balance + money;
	}	
public void withdraw(int money) throws Exception {
		if (money < 0 | balance < money) {
			throw new Exception();
		}
		this.balance = balance - money;
	}
```






