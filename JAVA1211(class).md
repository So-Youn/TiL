## 1. 클래스의 구성요소

*어떤 데이터가 필요한지, 어떤 기능이 있는지 중요!*

> `클래스`  객체를 정의해놓은 것.  or 객체의 모든 속성과 기능이 정의되어 있다.
>
> 클래스는 객체를 생성하는데 사용되며, 객체는 클래스에 정의된 대로 생성된다.
>
> `객체`는 실제로 존재하는 것. 사물 또는 개념
>
> 객체가 가지고 있는 기능과 속성에 따라 다르다.

클래스로부터 객체를 만드는 과정을 클래스의 인스턴스화(instantiate), 어떤 클래스로부터 만들어진 객체를 그 클래스의 `인스턴스(instance)`라고 한다.
```java
Tv t;				//Tv 클래스의 참조변수 t 선언. 
					//메모리에 참조변수 t를 위한 공간이 마련된다.
t = new Tv();		//연산자 new에 의해 Tv 클래스의 인스턴스가 메모리의 빈 공간에 생성.
					//생성된 객체의 주소값이 참조변수 t에 저장된다.(instance 접근 가능)
// Tv t = new Tv();
t.channel = 7;		//instance의 멤버변수 channel에 7 저장
t.channelDown();	//channelDown메서드 호출
Tv[] tvArr = new Tv();  	//객체 배열
```

### 1.1 멤버변수(데이터타입 데이터 ;)

>클래스 정의하고 멤버변수 정의(api에 있는 class와 사용방법 동일)
>* 멤버변수 정의할 때는 특별한 경우를 제외하고 초기값을 주지 않는다
>* 초기값을 정의하지 않아도 참조형은 null, 정수형은 0, 실수형은 0.0, boolean은 false
>* 멤버변수를 정의할 때 접근 제어자를 추가해서 접근을 제어할 수 있다.
>* 추가할 수 있는 접근 제어자의 종류 : 
>   * 		public
>   * 		default
>   * 		protected
>   * 		private  : 외부에서 보지 못하게 감춘다. (같은 패키지의 클래스에서도 접근 불가능),
>       * 		선언된 클래스에서만 사용 가능.
>* 	클래스를 정의할 떄 멤버변수는 private으로 선언해서 외부에서 접근할 수 없도록 정보를 은닉하고 `public 메소드`를 통해서 접근할 수 있도록 구현한다.

```java
		//메소드명 : set + 멤버 변수 명(첫 글자를 대문자로 바꾼)
		// 		 setName
		public void setName(String name) { 	//setter메소드
			this.name = name;
		}
		
		//name변수에 저장된 값을 호출하는 곳으로 넘겨줄 메소드
		//메소드명 : get + 멤버 변수명(첫 글자를 대문자로 바꾼)
		// 		 getName
		public String getName() {			//getter메소드
			return this.name;
		}
		Person p1 = new Person();			//new 연산자
		p1.setName("장동건");
```



### 1.1.2 지역변수(local variable)

> 메서드 내에 선언된 변수들은 그 메서드 안에서만 사용 가능.
>
> 서로 다른 메서드라면 같은 이름의 변수 선언 가능

```java
int add(int x, int y){
    int result = x + y;
    return result;
}
int multiple(int x, int y){
    int result = x * y;
    return result;
}

int result = add(3,5); // 메서드 호출
```



### 1.2 메소드(기능)

속성(property) -> 멤버변수(variable)

기능(function) -> 메서드(method) 

>  객체는 속성과 기능, 두 종류의 구성요소로 이루어져 있으며,  일반적으로 객체는 다수의 속성과 다수의 기능을 가진다.
>
> `메서드(method)` 는 특정 작업을 수행하는 일련의 문장들을 하나로 묶은 것.

* 메서드를 사용하는 이유
  * 높은 재사용성
  * 중복된 코드의 제거
  * 프로그램의 구조화

```java
public return타입 메소드이름 (데이터타입 타입변수명,...)			//선언부(header)
{
    //메서드 호출시 수행될 코드
    //구현부(body)
}
public int add(int num1, num2 ){	//숫자 2개를 매개변수로 전달받아 더해서
    								//결과를 리턴하는 메소드
    int result = num1 + num2;
    return result; 		//호출한 메서드로 결과 반환.
}
    

```

* 반환값이 없는 경우 ( =실행 결과가 없는 경우) return type :  void
  * 반환타입이 void 가 아닌 경우, 구현부 {} 안에 반드시 `return 반환값;`  이포함
  * 이 값의 타입은 변환타입과 일치하거나, 적어도 자동 형변환이 가능해야 함.

#### [예제]	

```java
public class Account {
	private String account;
	private int balance;
	private double interestRate;
public String getAccount() {
	return account;
}

public void setAccount(String account) {
	this.account = account;
}

public int getBalance() {
	return balance;
}
public void setBalance(int balance) {
	this.balance = balance;
}
public double getInterestRate() {
	return interestRate;
}

public void setInterestRate(double interestRate) {
	this.interestRate = interestRate;
}
public double calculateInterest() {
	double interest = this.balance *this.interestRate;
	return interest;
}
public void deposit(int money) {
	this.balance = balance + money;
}
```



```java
public class AccountTest {

	public static void main(String[] args) {
		Account s1 = new Account();
		s1.setAccount("441-0290-1203");
		s1.setBalance(500000);
		s1.setInterestRate(0.073);

		s1.print();
		s1.deposit(20000);
		s1.print();
		
	
		double interest = s1.calculateInterest();
		
		System.out.println(+interest);
	}

}
```

![캡처](images/캡처.PNG)

### 1.3생성자(constructor)

생성자는 메소드다. (객체가 생성될 때 호출되는 특별한 메소드.)
주로 자원을 

1. 액세스하거나 자원을 사용하기 위해서 초기화하거나 

2. 자원관련 작업을 하거나, 

3. 객체가 가지고 있는 멤버변수를 초기화하기 위해서  사용한다.

   (자원 - DBMS, 네트워크, 파일 시스템...)

   

[객체생성]

클래스타입 변수 = new 생성자메소드()

   ^					                      ^
   |										  |

​	_사용할  클래스			     _클래스 안에 미리 정의되어 있는 생성자 메소드를 호출
   					                        일반 메소드처럼 생성자 메소드도 매개변수로 외부에서 값을 전달 받아 사용.

>[규칙]
>
>1. 생성자 메소드명은 클래스명 과 대소문자까지 정확하게 동일한 이름으로 정의해야 한다.
>	=> 리턴타입 명시하지 않는다.
>	
>2. 생성자 메소드를 정의하지 않으면 컴파일러가 기본생성자를 정의한다.
>	=> 기본생성자 : 매개변수가 없는 생성자
>	=> 생성자 메소드를 개발자가 정의하면 컴파일러가 기본생성자를 제공하지 않는다.
>	=> 처리되는 일이 없다고 하더라도 무조건 기본생성자는 정의해야한다.
>	
>3. 생성자 메소드도 일반 메소드처럼 매개변수를 정의하고 외부에서 값을 전달받아 사용할 수 있다.
>	=> 주로 객체에 정의된 멤버변수의 값을 초기화하는 작업.
>	
>4. 생성자메소드도 일반 메소드처럼 오버로딩 허용한다. 
>
>5. 생성자 메소드 내부에서 다른 생성자 메소드를 호출할 수 있다.
>	=> this(매개변수..)
>	=> 반드시 첫 번째 문장에서 호출해야 한다.			
>	
>	



## 1.4 제어자(modifier)

`제어자`는 클래스, 변수, 또는 메서드의 선언부에 함께 사용되어 부가적인 의미를 부여한다.

> 접근 제어자 : public, protected, default,private
>
> 그 외: static, final,abstract,native

### 1) static- 클래스의, 공통적인

메모리 static 공간에 올라가 대기상태로 존재.

### 1.1) static 변수

> 인스턴스마다 다른 값이 아닌 같은 값을 공유하는 변수
>
> => **하나의 변수**를 모든 인스턴스가 **공유**

클래스 내 멤버변수로 `static`을 선언한다면, 생성한 클래스가 해당 변수를 고유의 값으로 가진다고 생각하면 된다.

```java
public class StaticDemo {
	String name;
	int num;
	static int staticNum;
	
	public StaticDemo() {
		
	}
	public StaticDemo(String name) {
		this.name = name;
		num++;
		staticNum++;
	}
    //위 클래스로 여러 객체를 생성해도 staticNum의 값은 0에서 증가하는 것이 
    //아니라 "마지막으로 사용했던 값"에서 1이 증가한다.
```

#### 1.2) Static 메소드

static멤버는 인스턴스의 소유가 아니므로 무조건 클래스명으로 접근한다. 

* 클래스 메서드는 객체를 생성하지 않고도, 클래스이름.메서드이름(매개변수) 로 호출 가능.
* 인스턴스 메서드는 반드시 객체를 생성해야만 호출 가능.
* static이 사용될 수 있는 곳 : 멤버변수, 메서드 , 초기화 블럭

```java
//Static메소드의 호출(클래스 메소드)
		System.out.println(Math.PI);
		System.out.println(Math.random());
//static으로 선언한 변수는 인스턴스의 고유한 값을 저장하는 인스턴스 변수
//인스턴스 변수로 접근할 수 없다.
///클래스명으로 접근해야한다.
public class StaticDemoTest {
	public static void main(String[] args) {
		StaticDemo obj1 = new StaticDemo("obj1");
		obj1.display();
		System.out.println(obj1.num+","+StaticDemo.staticNum);
		
		StaticDemo obj2 = new StaticDemo("obj2");
		obj2.display();
		System.out.println(obj2.num+","+StaticDemo.staticNum);
		
		StaticDemo obj3 = new StaticDemo("obj3");
		obj3.display();
		System.out.println(obj3.num+","+StaticDemo.staticNum);
	}

}
```



#### 1.3) non-static메소드(일반메소드-인스턴스메소드)

* 객체 생성을 한 후에 참조변수를 통해서 액세스.

* 인스턴스는 하나의 클래스로부터 생성되었더라도 각기 다른 값을 유지하지만, 클래스변수(static 변수)는 인스턴스에 관계없이 같은 값을 갖는다.

```java
Random rand = new Random();
		System.out.println(rand.nextInt());
```

### 2) 접근 제어자(access modifier)

* private : 같은 클래스 내에서만 사용 가능
* default : 같은 패키지 내에서만 사용 가능
* protected : 같은 패키지 내에서,그리고 다른 패키지의 자손클래스에서 접근 가능.
* public : 접근 제한이 전혀 없다.