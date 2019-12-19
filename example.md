## 알람시계 45분 일찍 맞추기

```JAVA
import java.util.Scanner;
public class Main {
	// ctrl+shif+f : 줄 정리
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		
		int H = input.nextInt();
		int M = input.nextInt();
		System.out.println("현재시간 "+H+"시"+M+"분");
		input.close();
		if (M >= 45) {
			M = M - 45;
			System.out.println("알람시간 "+H+"시"+M+"분");
		} else {
			if (H == 0) {
				H = 24;
			}

			H = H - 1;
			M = M - 45 + 60;
			System.out.println("알람시간 "+H+"시"+M+"분");
		}

	}
}
```

## 숫자 더하기 (while)

0보다 크거나 같고, 99보다 작거나 같은 정수가 주어질 때 다음과 같은 연산을 할 수 있다. 먼저 주어진 수가 10보다 작다면 앞에 0을 붙여 두 자리 수로 만들고, 각 자리의 숫자를 더한다. 그 다음, 주어진 수의 가장 오른쪽 자리 수와 앞에서 구한 합의 가장 오른쪽 자리 수를 이어 붙이면 새로운 수를 만들 수 있다. 다음 예를 보자.

26부터 시작한다. 2+6 = 8이다. 새로운 수는 68이다. 6+8 = 14이다. 새로운 수는 84이다. 8+4 = 12이다. 새로운 수는 42이다. 4+2 = 6이다. 새로운 수는 26이다.

위의 예는 4번만에 원래 수로 돌아올 수 있다. 따라서 26의 사이클의 길이는 4이다.

N이 주어졌을 때, N의 사이클의 길이를 구하는 프로그램을 작성하시오.

```java
package Test;

import java.util.Scanner;

public class BeakJoon {
	public static void main(String[] args) {
	Scanner sc = new Scanner(System.in);
	int num = sc.nextInt();
	int a =0;		//첫번째 자리 수
	int b =0;		//두번째 자리 수
	int temp=0;		//두번째 자리 수 임시 저장
	int cycle = 0;	//사이클 길이
	
	a = num/10;	
	b = num%10;
	
	while(true) {
		cycle++;
		temp = b;
		b = (a + b)%10;	//두번째 숫자는 합의 가장 오른쪽 자리 숫자.
		a = temp;		// 첫번째 숫자는 두번째 숫자.
		if (num == a*10+b) {  //이어붙이기
			break;
		}
	}
	System.out.println(cycle);
	sc.close();
	}
}
```

