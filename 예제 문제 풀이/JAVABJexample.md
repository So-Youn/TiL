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

## 최솟값과 최댓값

첫째 줄에 정수의 개수 N (1 ≤ N ≤ 1,000,000)이 주어진다. 둘째 줄에는 N개의 정수를 공백으로 구분해서 주어진다. 모든 정수는 -1,000,000보다 크거나 같고, 1,000,000보다 작거나 같은 정수이다.

``` java
import java.util.Scanner;
public class BeakJoonTest01 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int N = sc.nextInt();
		int[] arr = new int[N];
		for (int i = 0; i <arr.length; i++) {
			arr[i] = sc.nextInt();
		}
			int min = arr[0];
			for (int i = 0; i <arr.length; i++) {
				min = Math.min(min, arr[i]);
			}
			int max = arr[0];
			for (int i = 0; i <arr.length; i++) {
				max = Math.max(max, arr[i]);
			}
	
		sc.close();
		System.out.print(min+" "+max);

	}
}

```

## 최댓값과  최댓값 위치

``` java
import java.util.Scanner;
public class BeakJoonTest01 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int[] arr = new int[9];
		for (int i = 0; i <arr.length; i++) {
			arr[i] = sc.nextInt();
		}
			int max = arr[0]; // 기준이 될 첫번 째 값을 max에 넣음 
			int count = 0;	  // 최대값 위치 count 할 변수 생성 	
			for (int i = 1; i <arr.length; i++) {  // 비교는 다음 수 부터
				if (arr[i]>max) {
					max = arr[i];
					count=i+1;
				}
			}
		
		sc.close();
		
		System.out.println(max);
		System.out.println(count);
		}
}
```

