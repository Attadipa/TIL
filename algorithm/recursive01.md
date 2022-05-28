# 이진수 출력 / 팩토리얼 (재귀함수 활용)

### 인프런 자바(Java) 알고리즘 문제풀이 : 코딩테스트 대비

풀이

```java
//10진수의 2진수로의 변환
import java.util.Scanner;

public class Main {
	
	public static void recursive(int n) {
		if(n==0) return;
		else {
			recursive(n/2);
			System.out.print(n%2);
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		recursive(n);
	}
}

//팩토리얼
import java.util.Scanner;

public class Main {
	
	public static int recursive(int n) {
		if(n==1) return 1;
		else return n * recursive(n-1);
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		System.out.println(recursive(n));
	}
}
```