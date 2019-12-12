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

