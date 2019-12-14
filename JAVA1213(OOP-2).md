![image-20191213092057006](C:\Users\sec\AppData\Roaming\Typora\typora-user-images\image-20191213092057006.png)

파일 관리 쉽게 하기 위한 설정,

---

## ★★★다형성 Polymorphism★★★

## 0.  객체의 형변환

>상속 관계에만 가능하다.
>
>즉, child와 parent는 형변환 가능하지만,  child와 child2는 형변환 불가능하다.(상속x)

		 *  변수는 참조변수 타입에 따라서 결정, 메소드는 생성되는 객체가 기준

```java
public class RefCastingTest {
	public static void main(String[] args) {
		System.out.println("1.Super타입의 참조변수로 Super객체를 참조");
		Parent obj1 = new Parent();
		obj1.display();
		System.out.println(obj1.name);
		
		System.out.println("******************************");
		System.out.println("2.sub타입의 참조변수로 sub객체 참조");
		Child obj2 = new Child();
		obj2.display();
		System.out.println(obj2.name);
        
		Parent obj3 = new Child();	//type은 super지만, sub 타입 생성	
		obj3.display();				
		System.out.println(obj3.name);//참조변수 타입에 해당하는 
        							  //클래스의 멤버변수가 실행
		obj3.test();		          //타입이 parent 타입이지만 실제로 생성된 객체가 child 타입이기 때문에 child타입으로 형변환이 가능하다.(명시적)
        ((Child)obj3).test();
    }
}
```

**java.lang.ClassCastException** :  명시적으로 형변환을 해서 컴파일러는 속였으나 실행시점에 캐스팅을 하려고 할때, obj1이 child 정보를 갖고 있지 않으므로 캐스팅 예외 발생
		*[예시 ]*

```java
public class RefCastingTest {
	public static void main(String[] args) {
		System.out.println("5. sub타입의 참조변수 = "
				+"super타입의 참조변수(super객체를 참조)--------x");
        Child obj5 = (Child)obj1;
        //obj1이 실제로 참조하는게 parent라서 절대 캐스팅 불가능

		System.out.println("******************************");
		System.out.println("5. sub타입의 참조변수 = "
				+"super타입의 참조변수(Sub객체를 참조)-----ㅇ");
		Child obj6 = (Child)obj3;
		System.out.println(obj6.name);
		obj6.display();
		obj6.test();			//변수는 type에 의존.
        					//child 타입을 실제로 참조하기 때문에 캐스팅 가능
    }
}
```

```java
public class RefCastingTest {
	public static void main(String[] args) {
        Parent obj8 = null;	//
		Child obj9 = new Child();	//fe
		Child obj10= null;	//fe2
        obj8 = obj9; 	//super타입 = sub타입
		obj10 = (Child)obj8; 
       	obj10.test();	//아무것도 담고있지 않을 때 casting은 되지만, 								nullpoint.
	}

}
```

- obj8이 parent 타입 같아보이지만, 바로 앞 줄에서 obj9를 넣어놨기 때문에 obj8은 child를 참조한다.
- 변수의 형태는 실행 시점에서 알 수 있다.
- 참조는 할 수 잇지만 obj8은 parent타입이기 때문에 명시적으로 casting -> null point.



## 1. 다형성이란,

* `동일한 타입의 변수`(상위 타입의 클래스)를 선언했을 때, 다양한 객체가 매핑되면서 사용자가 무엇을 선택하느냐에 따라 다른 결과가 나타나는 것. (SUPER->A,B,C 기능)+D기능 추가 가능.

* 다형성이 가장 잘 녹여져있는 것이 API.
* 부모의 메서드가 자식의 종류에 따라 다양한 형태로 나타날 수 있는 특징.
* **상속**과 **오버라이딩**을 하면 다형성이 발생한다

### ① 부모타입으로 자식을 생성할 수 있다. 

* 부모에게 있는 메서드만 사용할 수 있다. 

```java
Vehicle v1 = new Airplan();
Vehicle v2 = new Bus();
Vehicle v3 = new Cap();
```

### ② 부모 타입으로 자식을 받을 수 있다.(by Casting)

```java
Airplane a1 = new Airplane();
Vehicle v4 = a1; 			//단, Vehicle에 있는 메서드만 사용할수 있다.
Airplane a2 = (Airplane)v4;	//Airplane, Vehicle 모든 메서드 사용 가능.
```

자식이 여러 개인 경우, 생성된 객체의 인스턴스가 누구 것인지 확인해야 한다. 이때 인스턴스의 타입을 확인하는 키워드가 바로  `instanceof` 이다.

### ③ 부모의 메서드로 자식의 메서드 호출 가능하다.

- 부모의 메서드가 자식의 종류에 따라 다양한 형태로 나타나는 것을 다형성이라고 한다.

## 2. 인터페이스(interface)

모든 메서드가 구현이 되지 않은 추상 클래스를 `interface`라고 한다.

```java
public interface IMagicSquare{
    void make();					//반드시 구현해야 할 메서드
    void print();					//반드시 구현해야 할 메서드
}
```

인터페이스를 구현할 때는 `implements` 키워드를 사용하고, 인터페이스에 선언딘 메서드를 구현해야한다.

구현하지 않으면 추상클래스가 된다.

```java
public abstract class MagicSquare interface IMagicSquare{
    @Override
    public void print(){
        //여기 꼭 구현
    }
    //make를 구현하지 않았다.
}
```

자바에서는 다중 상속이 불가능하지만, 인터페이스로 다중 상속을 흉내낼 수 있다.